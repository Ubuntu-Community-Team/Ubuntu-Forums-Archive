---
title: "What to clear in usr?"
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by Hiroshima on 2007-11-24
I am trying to upgrade to 7.04 (just updated to 6.10 yesterday)

but I am getting "usr full, please clear an additional 17M of disk space"

usr is on it's own partition.  System Monitor says:
Total 3.9G
 Free 580M
Used 3.4G

I have run
apt-get clean
emptied the trash 
and deleted the contents of .Trash-root

in usr:

bin is 205mb
etc 183kb
games 1.9mb
include 38mb
java 112mb
lib 1.2G
lib 64 kb
local 108 kb
man 4kb
sbin 23mb
share 1.4G
src ... (doesn't give a number, but there is stuff in there)
x11r6  ... (doesn't give a number, but there is stuff in there)
.Trash-root is empty

 Any ideas on what I can safely get rid of?  Or uninstall for now, and reinstall when the updates are done?

Thanks in advance, Hiroshima

---

### Post by elctb on 2007-11-24
If you have room on a different partition I would copy the share directory to the new partition and then create a symbolic link from /usr to the new location. For example:

. cd /usr
. sudo cp -r share /home/hiroshima (assuming the hiroshima directory exists).
. sudo rm -rf share
. sudo ln -s /home/hiroshima/share share

This might work.

---

### Post by Hiroshima on 2007-11-24
ok, will give it a try!

---

### Post by Hiroshima on 2007-11-24
2.1G now free! and my home partition still has breathing room too! (if it gets too full there are big files I can get rid of)

I will start updating... wish me luck.

Thanks for the help,

Hiroshima

---

