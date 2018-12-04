# spring-boot-app-config

Files for setting up spring-boot application configuration

If you currently have your application secrets either:

* hardcoded in the Java
* hardcoded in an `application.properties`
* in `application.properties` which is in `.gitignore`

then the four files in the subdirectory `config` in this repo are just what you need.

```
env.sh
setHerokuEnv.py
localhost.json.SAMPLE
heroku.json.SAMPLE
```

# To use these files:

1. Clone this repo as a sibling of your repo
2. `cd` into your repo, and then do:
   ```
   cp ../spring-boot-app-config/config/* .
   ```
3. Then, add these files to your .gitignore
   ```
   localhost.json
   heroku.json
   ```
4. Commit these four new files to your repo (and the changes .gitignore)

# Using the files on localhost

1. `cp localhost.json.SAMPLE localhost.json`

2. Edit `localhost.json` with the values that you need.

3. Execute `source env.sh` OR `. env.sh`

   Those both do the same thing.  NOT the same as `./env.sh`

   The space between `.` and `env.sh` is on purpose.

   This defines an environment variable `SPRING_APPLICATION_JSON` which
   has property values that override the ones in your `src/main/resources/applicaiton.properties` or `src/main/resources/application.yml` with new values.

   Those are the values you use when running on localhost.

   The file `localhost.json.SAMPLE` should contain "fake data" for all the
   values you need, and the README.md should explain how to set up
   real values (e.g. how to set up github oauth, or firebase credentials,
   or google oauth, or an mlab database, etc. etc.)

# Using the files to run on heroku

1. Copy from `heroku.json.SAMPLE` to `heroku.json`

2. Edit the file to set the values for heroku

3. Run `./setHerokuEnv.py --app name-of-your-herokuapp`

   If you get a permission error, do this first:

   ```
   chmod u+x setHerokuEnv.py`
   ```

   This sets the config variables on Heroku to the values in your
   `heroku.json`.   You can see those value in the Heroku dashboard config
   vars.

   