---
title: "upgrading to edgy - glchess"
date: 2006-10-15
forum: Installation &amp; Upgrades
---

### Post by distroman on 2006-10-15
I am trying to upgrade from dapper to edgy. 

The upgrade quit again, this time because of glchess. 
```
E: The package glchess needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```

[https://launchpad.net/distros/ubuntu/+bug/56413](https://launchpad.net/distros/ubuntu/+bug/56413)

uninstall
```
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 223491 files and directories currently installed.)
Removing glchess ...
dpkg: error processing glchess (--remove):
 unable to stat installed post-removal script `/var/lib/dpkg/info/glchess.postrm': Permission denied
Errors were encountered while processing:
 glchess
```

reinstall
```
Selecting previously deselected package glchess.
(Reading database ... 223498 files and directories currently installed.)
Preparing to replace glchess 0.9.8-1 (using glchess_0.9.8-1_all.deb) ...
Unpacking replacement glchess ...
dpkg: warning - unable to stat old post-removal script `/var/lib/dpkg/info/glchess.postrm': Permission denied
dpkg - trying script from the new package instead ...
dpkg: ... it looks like that went OK.
dpkg: error processing glchess_0.9.8-1_all.deb (--install):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/postinst': Permission denied
Errors were encountered while processing:
 glchess_0.9.8-1_all.deb
```

Anyone know away to solve it?

...
/var/lib/dpkg/info

glchess.list
glchess.md5sums
glchess.postinst
glchess.postrm
glchess.prerm

The permissions of "glchess.postrm" could not be determinated.

Guess I am screwed? hah

Also it might have a little something to do with this.
[https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/58424](https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/58424)

ohh well, didn't really think I would get lucky.

---

### Post by distroman on 2006-10-16
uff,,,think I got it!

reverted back to dapper source.list
sudo aptitude update && sudo aptitude dist-upgrade

got permissions back in /var/lib/dpkg/info/ “glchess files” with
reiserfsck --check 
reiserfsck --rebuild-tree

then reinstalled glchess
sudo dpkg -i glchess_0.9.8-1_all.deb

sudo apt-get remove glchess

then finally 
apt-get -f install
which let me install “Setting up libgl1-mesa (6.4.1-0ubuntu8)”

Then removed glchess -
So glchess is GONE BYE BYE and I can fix the broken packages. 

Off to upgrade again. Not to optimistic though. :D

---

### Post by fakie_flip on 2007-03-13
I just upgraded to feisty.

chris@ubuntu:~$ cat /etc/issue.net 
Ubuntu feisty (development branch)

Here is how to do it.

gksu 'update-manager -d'

---

### Post by distroman on 2007-08-07
Hey thanks that worked a treat. Slow down on the cookies though.

---

