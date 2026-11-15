# todo-app

ToDo アプリのモノレポです。

## 構成

```
todo-app/
└── apps/
    ├── api/   # Java API（Spring Boot）
    ├── bff/   # BFF（Hono）… 後続
    └── web/   # フロントエンド（Angular）… 後続
```

システム構成は次のとおりです。

```
Angular → Hono（BFF）→ Java API → PostgreSQL
```

現時点で実装済みなのは `apps/api` のみです。`apps/bff` と `apps/web` は後続のチケットで追加します。

## apps/api

前提条件:

- Java 25
- Docker（`bootRun` で PostgreSQL を起動するために必要。`build` のテストは Docker がなくても通ります）

ビルドとテスト:

```sh
cd apps/api
./gradlew build
```

起動:

```sh
cd apps/api
./gradlew bootRun
```

`bootRun` は `compose.yaml` の PostgreSQL を Docker で起動します。起動後、<http://localhost:8080/swagger-ui.html> で API の仕様を確認できます。
