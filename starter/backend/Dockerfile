FROM python:3.10-slim

RUN adduser --uid 1000 app

RUN apt-get update && \
    apt-get install -y \
    build-essential \
    libpcre3 \
    libpcre3-dev \
    libffi-dev \
    && rm -rf /var/lib/apt/lists/* && \
    pip install pipenv

RUN mkdir -p /var/www/app && mkdir /app

COPY Pipfile* /app

RUN cd /app && pipenv install --system --deploy

COPY . /app

USER app

EXPOSE 5000

CMD ["pipenv", "run", "serve"]
