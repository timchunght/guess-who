## Learn some names!

This is a simple game that allows you to guess the names of people.

This is a fork of https://github.com/cyrusstoller/guess-the-stack

### For development

```bash
$ shotgun config.ru
```

### Without reloading between requests

```bash
$ rackup config.ru
```

### Deployment

```bash
cap production deploy:setup
cap production deploy
```

## Database schema

The sqlite file should live in

> data/people.sqlite3.db

A sample file can be found in

> data/sample.sqlite3.db

For a quick start you can run:

```bash
$ ln -s data/sample.sqlite3.db data/people.sqlite3.db
```

```sql
CREATE TABLE "groups" (
	`id`	INTEGER NOT NULL PRIMARY KEY AUTOINCREMENT UNIQUE,
	`name`	TEXT
);
CREATE TABLE "people" (
	`id`			INTEGER NOT NULL PRIMARY KEY AUTOINCREMENT UNIQUE,
	`name`			TEXT,
	`web_url`		TEXT,
	`description`	TEXT,
	`thumbnail`		TEXT,
	`group_id`		INTEGER
);
```

For now, to load data from a csv:

- First remove the `id` column

```
sqlite3 data/people.sqlite3.db
.mode csv
.import 'raw.csv' people
```

- Add the `id` column back
- I plan on adding a rake task for this in the future

## Contributing

### Bugs / Issues

If you find a bug or something that could improve the user experience, please file an issue on this github project, so contributors/maintainers can get started fixing them. :-)

Even if you plan on filing a patch for the issue yourself it'd be great if you could still file an issue so that we don't have people duplicating work unnecessarily.

### Submitting Pull Requests

1. Fork this project
2. Make a feature branch git checkout -b feature
3. Make your changes and commit them to your feature branch
4. Submit a pull request