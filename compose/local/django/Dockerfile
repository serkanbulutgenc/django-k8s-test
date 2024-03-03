FROM python:3.11-slim-bullseye as builder

LABEL APPNAME="Django Web app" APPVERSION="1.0.0" MAINTAINER="serkanbulutgenc@gmail.com"

ENV VIRTUAL_ENV=/opt/venv
ENV PATH="$VIRTUAL_ENV/bin:$PATH"

COPY requirements.txt /app/

WORKDIR app

COPY . .

SHELL ["/bin/bash", "-c"]

RUN apt-get update && apt-get upgrade -y &&\
    apt-get install -y python-dev libxml2-dev libxslt1-dev zlib1g-dev

RUN python -m venv $VIRTUAL_ENV && \
    $VIRTUAL_ENV/bin/pip install --upgrade pip && \
    $VIRTUAL_ENV/bin/pip install -r requirements.txt &&\
    source $VIRTUAL_ENV/bin/activate

EXPOSE 8888

CMD [ "python", "manage.py", "runserver", "0.0.0.0:8888" ]
