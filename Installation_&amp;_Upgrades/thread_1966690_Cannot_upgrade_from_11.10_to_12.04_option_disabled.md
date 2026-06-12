---
title: "Cannot upgrade from 11.10 to 12.04 option disabled"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by kabeza on 2012-04-27
Hi
I've installed some weeks ago Ubuntu 11.10 from amd64 DVD version
Now I've got the 12.04 amd64 CDROM version.

I booted with this 12.04 version and after some time, I got the upgrading option disabled (cannot select it). Also, when I boot 11.10 and insert the 12.04 CDROM I don't get the upgrading message as usual.

Should I download the 12.04 DVD-amd64 version to do the upgrading?

Thanks a lot in advance,

---

### Post by xp15 on 2012-05-18
having same problem, solution?

---

### Post by Vereinfachen on 2012-05-18
Why don't you upgrade using the Software Update in your 11.10 machine? Go to the Update Tool, refresh the package list and it should give you the option to upgrade to the new version over the internet. :)

---

### Post by kabeza on 2012-05-18
> **xp15 said:**
> having same problem, solution?


to download and burn one of these (depending your PC config)

- ubuntu-12.04-alternate-amd64.iso.torrent
- ubuntu-12.04-alternate-i386.iso.torrent

from
[http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)

Once you insert an alternative CD into your PC, Ubuntu will launch the distro upgrade. Be advised I had trouble. I upgraded from 11.10 to 12.04 successfuly (the process went OK), but the 12.04 never worked well so I decided to backup and do a clean 12.04 install :(

---

### Post by jadtech on 2012-05-18
ok go to  the software updater

in settings the updates tabthe bottom pull down menu ( notify me of new ubuntu versions) if never is chose  change that to any new version  close the windows all out  then go to a terminal

type this 

```
 sudo apt-get update

sudo apt-get do-release-upgrade 


```

do any updates and the upgrade button should become available

---

