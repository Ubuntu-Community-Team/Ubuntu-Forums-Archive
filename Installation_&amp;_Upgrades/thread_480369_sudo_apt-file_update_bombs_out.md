---
title: "sudo apt-file update bombs out"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by monteros on 2007-06-21
I am having a problem trying to update apt-file, and was hoping someone out there might be able to help.  Installed apt-file without issue.

when I run ```
sudo apt-file update
```it looks like it is going to start, and it tries to find > Contents-i386.gz on the cdrom, and it bombs out.

I checked it isn't there, I am running 704 server within VMware on an ESX server.  I think it is something as simple as it is trying to stat the CDROM for that file, and since it doesn't exist it hangs.

I would expect it to keep going just like apt-get and stat the update sites and grab what it needs, but it doesn't.

Here is the info on exactly what I see:```
twiki:/$ sudo apt-file update
Put CDROM labeled [Ubuntu-Server_7.04__Feisty_Fawn__-_Release_i386_(20070415)] in the cdrom device
read: 1: arg count
mount: block device /dev/hda is write-protected, mounting read-only
cp: cannot stat `/cdrom/dists/feisty/Contents-i386.gz': No such file or directory

``` Then it hangs and does nothing.

Anyone have any ideas? Thanks! :D

-Monteros

---

### Post by monteros on 2007-06-21
nevermind, it did hang, but it was updating with nothing verbose for some reason, it worked fine after I just let it sit there.  I had expecged to see updating information like apt-get update shows...

---

