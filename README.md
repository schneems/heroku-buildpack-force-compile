

# Heroku Buildpack Force Compile


## What

Force compile buildpacks

## Why

Mostly for debugging problems with buildpacks. When they fail the slug still releases so you can `heroku run bash` and see what is wrong interactively.


## How


Put buildpacks you want to force compile into a `.buildpacks` file:


```
$ cat .buildpacks
https://github.com/heroku/heroku-buildpack-nodejs.git#0198c71daa8
https://github.com/heroku/heroku-buildpack-ruby.git#v86
```

Commit to git

```
$ git add .buildpacks
git commit -m multi-buildpacks
```

Now specify this buildpack in your `BUILDPACK_URL`:

```
$ heroku config:add BUILDPACK_URL=https://github.com/schneems/heroku-buildpack-force-compile.git
```

## License

MIT
