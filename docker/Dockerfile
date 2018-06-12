FROM node:8 as dev

ENV TINI_VERSION v0.18.0
ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini /tini
RUN chmod +x /tini
ENTRYPOINT ["/tini", "--"]

ENV APP_ROOT /app

ADD frontend/package.json $APP_ROOT/package.json
WORKDIR $APP_ROOT

RUN yarn

EXPOSE 3000

# TODO: 意味ない?
CMD ["bash"]

# ------------------------------

FROM dev as builder

COPY frontend $APP_ROOT
RUN yarn build

CMD ["yarn", "start"]