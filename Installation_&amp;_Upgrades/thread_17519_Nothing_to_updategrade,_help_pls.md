---
title: "Nothing to update/grade, help pls"
date: 2005-03-01
forum: Installation &amp; Upgrades
---

### Post by HJB on 2005-03-01
Hi all. I’m very new at this, so pls be patient.
During installation of Warty I lost internet connection and when the screen for header upgrades (something like that) appeared I had to ctrl Q (I think) because it was just hanging and timing out.
Eventually everything else installed fine

The problem now is when I do a sudo apt-get update or upgrade it tells me **0 upgraded** etc with 0 everywhere.
Same goes for upgrade and for dist-upgrade
What should I do, pls help
Bye
H
 #-o

---

### Post by ixus_123 on 2005-03-01
A similar thing happened to me.  I lost the connection & ended up with a buggy system.  As it's a fresh install the easiest thing to do would be be to take an hour & reinstall.

Before you do this however, you might as back up the packages you've already downloaded.  Do this: (lifted from the unofficial Ububtu guide)

[http://ubuntuguide.org/#backuprestoredownloadedrepositoriescache](http://ubuntuguide.org/#backuprestoredownloadedrepositoriescache) 

```
 $ mkdir -p $HOME/backup/var/lib/
$ sudo cp -R /var/lib/apt/ $HOME/backup/var/lib/
$ mkdir -p $HOME/backup/var/cache/
$ sudo cp -R /var/cache/apt/ $HOME/backup/var/cache/
$ mkdir -p $HOME/backup/etc/apt
$ sudo cp -R /etc/apt/ $HOME/backup/etc/
$ sudo chown -R $USER $HOME/backup/
``` 

You'll then need to put this on a CD-R:
```
 $ nautilus burn:///
``` 

Drag the folder backup folder into the window & File menu --> Write to disc --> write

once that's done reinstall but DON'T downloadsoftware from the internet.  It's better to have a workable system first before you update.

Put your backup CD in a drive & copy it back to your homefolder, then:

```
 $ sudo cp -fR $HOME/backup/var/* /var/
$ sudo cp -fR $HOME/backup/etc/apt/* /etc/apt/
``` 

then

```
sudo apt-get update
sudo apt-get upgrade
``` 

you might want to add more repositories before you do that.  There is a howto @ the above link :)

go out / watch a film etc while all that stuff downloads :)

---

