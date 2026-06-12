---
title: "Ubuntu 10.4 upgrading then Ubuntu 10.10 installation problems"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by Shareb on 2011-01-04
Greetings,

I was using an unsupported version of Ubuntu (9.04) and was asked to upgrade to 9.10 so I hit the upgrade button and after the upgrade it's stuck at the Ubuntu logo and doesn't boot.

So, I thought I'd just burn a new Ubuntu 10.10 image, and use it to backup my data then do a clean installation. but I ended up getting this error after I choose "Try Ubuntu without installing" option:

```

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed:Input/output error

Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs 

```

I'm a Linux n00b and I need help.

---

### Post by nomko on 2011-01-04
Do you have a install cd of Ubuntu?? 
 
Then do a fresh/clean installation!
Start the installation and when the setup enters the partition manager, remove the whole partition which contains the old Ubuntu version. 
 
The select the cleaned disk for installing the new version and continue
 
Never do an upgrade within a running version. The risk of getting in trouble (like yours) is to high. Always perform a fresh/clean install.

---

