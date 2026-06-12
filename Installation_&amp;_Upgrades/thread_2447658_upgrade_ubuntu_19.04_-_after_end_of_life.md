---
title: "upgrade ubuntu 19.04 - after end of life"
date: 2020-07-23
forum: Installation &amp; Upgrades
---

### Post by francescodc87 on 2020-07-23
Hi,
I have a machine with 19.04 installed. I need to upgrade the distro as 19.04 is not supported any more.
```
sudo do-release-upgrade
``` gives me the following error
```

Checking for a new Ubuntu releaseYour Ubuntu release is not supported anymore.
For upgrade information, please visit:
http://www.ubuntu.com/releaseendoflife


Please install all available updates for your release before upgrading.

```

Searching online I found several possible solutions, but nothing seems to work.
I would install directly a new version of ubuntu via usb stick, but the machine is at my office and I won't have access to it until September (maybe later give to COVID related issues).
Could anybody help?

---

### Post by ActionParsnip on 2020-07-23
You'll need to grab the 19.10 ISO and upgrade using that. You can then upgrade to 20.04
Be sure you run a final full backup before starting if your data is valuable to you

Personally I suggest you run a final full backup and wipe the install off. You can then do a clean install of 20.04 and restore your user data. You will have fewer issues and less stuff and fluff from the old install.

---

### Post by francescodc87 on 2020-07-23
Thanks for the quick reply!
Is there a way to "grab the 19.10 ISO and upgrade using that" remotely? Maybe via ssh?
Unfortunately, I don't have physical access to the machine till late September...

---

### Post by ActionParsnip on 2020-07-23
[http://releases.ubuntu.com/19.10/ubuntu-19.10-desktop-amd64.iso](http://releases.ubuntu.com/19.10/ubuntu-19.10-desktop-amd64.iso)
MD5: [COLOR=#000000]ee829212bbd90d6c0237701b10ad90fd[/COLOR]

---

### Post by francescodc87 on 2020-07-23
hi,
so I downloaded the image, mounted it in media/cdrom. 
```

ls /media/cdrom/
boot  casper  dists  EFI  install  isolinux  md5sum.txt  pics  pool  preseed  README.diskdefines  ubuntu

```

What should I do next?

---

### Post by ActionParsnip on 2020-07-23
As far as I know you'll need to make a bootable media using the ISO and the upgrade will be offered there. Others may know a different method

---

### Post by rsteinmetz70112 on 2020-07-23
If you're feeling brave and lucky it is possible to upgrade using the online [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/). I did it once upon a time and it required changing the sources to point to the old releases repositories. 

More information here. [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

