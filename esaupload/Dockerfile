FROM btbn/ffmpeg_base

RUN \
	ESAUPLOAD_COMMIT="5d611cb9ef8fa0669d2e12bf5122309823259b96" && \
	BDEPS="python-pip python-dev git virtualenv" && \
	RDEPS="python-minimal less nano vim" && \
	apt-get -y update && \
	apt-get -y install $BDEPS $RDEPS && \
	virtualenv -p /usr/bin/python2 /venv && \
	/venv/bin/pip install --upgrade setuptools pip && \
	/venv/bin/pip install git+https://github.com/BtbN/esaupload.git@$ESAUPLOAD_COMMIT && \
	apt-get -y remove --purge --auto-remove $BDEPS && \
	apt-get clean && \
	rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp* && \
	mkdir -p /record /config

ENV PATH /venv/bin:$PATH
VOLUME /record /config

