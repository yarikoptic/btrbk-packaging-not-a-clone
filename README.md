btrbk packaging
===============

This is the btrbk packaging repository, **used for creating debian
packages**.

The official btrbk git repository is available here:

- git://dev.tty0.ch/btrbk.git
- https://github.com/digint/btrbk.git


Creating a Debian Release
-------------------------

### Step 0: add upstream remote

```
git remote add upstream git://dev.tty0.ch/btrbk.git
```

### Step 1: merge upstream release

```
git fetch upstream v0.19.3
git merge --no-ff v0.19.3
git tag upstream/0.19.3 -m 'btrbk upstream release 0.19.3'
```


### Step 2: update debian build files

```
edit debian/changelog
edit debian/[...]
```


### Step 3: create Debian package

```
dpkg-buildpackage -d -rfakeroot -g
```

if everythin went fine, create a tag:

```
git tag debian/0.19.3-1 -m 'btrbk Debian release 0.19.3-1'
```


### Step 4: cleanup

```
git clean -d -f
git checkout -- .
```
