FROM jupyterhub/jupyterhub:1.5.0

RUN apt-get update && \
    apt-get install --yes ssh && \
    rm -rf /var/lib/apt/lists/*

RUN python3 -m pip install \
    escapism \
    python-digitalocean \
    oauthenticator

ADD templates /usr/local/share/jupyterhub/templates/
ADD static/images /usr/local/share/jupyterhub/static/images/
ADD static/js /usr/local/share/jupyterhub/static/js/
ADD web.py /usr/local/lib/python3.8/dist-packages/tornado/web.py
ADD _xsrf_utils.py /usr/local/lib/python3.8/dist-packages/jupyterhub/_xsrf_utils.py

# Re-create users on startup, based on directories existing in /home
ADD start.sh /usr/local/bin/
CMD [ "start.sh" ]
