---
title: "Almost upgraded to Edgy, but Courier is broken"
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by atiaxi on 2006-11-12
I did the official method of upgrading, and it only got so far before breaking.  It did, however, modify sources.list, because Adept (I mostly use KUbuntu) showed thousands of packages that needed updating.  I let it go, and it got mostly finished.  However, courier seems to have broken things.  When I try to complete the upgrade (command line shown here for clarity) I get:

```

You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  courier-authlib-userdb: Depends: courier-authlib but it is not installed
                          Depends: courier-authlib (>= 0.58) but it is not installed
  courier-base: Depends: courier-authlib but it is not installed
E: Unmet dependencies. Try using -f.

```

So I run an apt-get -f install and get:

```
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  courier-authdaemon courier-authlib
The following NEW packages will be installed:
  courier-authlib
The following packages will be upgraded:
  courier-authdaemon
1 upgraded, 1 newly installed, 0 to remove and 36 not upgraded.
3 not fully installed or removed.
Need to get 0B/83.9kB of archives.
After unpacking 164kB of additional disk space will be used.
Do you want to continue [Y/n]?
dpkg: error processing courier-authdaemon (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
```

Okay, so I need to reinstall courier-authdaemon.  I do apt-get --reinstall install courier-authdaemon:

```
The following packages have unmet dependencies:
  courier-authdaemon: Depends: courier-authlib (>= 0.58) but it is not going to be installed
  courier-authlib-userdb: Depends: courier-authlib but it is not going to be installed
                          Depends: courier-authlib (>= 0.58) but it is not going to be installed
  courier-base: Depends: courier-authlib but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

I've been going around in this circle on and off for a few days now.  Any help?

---

### Post by atiaxi on 2006-11-12
As usual, I discover the answer to the problem only after I've posted in order to make a fool of myself.

[http://ubuntuforums.org/showthread.php?t=285466&highlight=courier](http://ubuntuforums.org/showthread.php?t=285466&highlight=courier)
had the answer I needed, thanks! :)

---

