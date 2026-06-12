---
title: "Multiboot / Partition Move / Boot Problem"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by Joerg Moeller on 2010-11-24
Hello,

I'm sort of Linux Newbie so please be kind.... ;-)

I ran a Ubuntu 10.04 installation on a 160GB drive. After some time I decided to create a multi boot system on a new 500GB drive together with Ubuntu 10.04, SLES 10 and RHEL 5.5. So I partitioned my new drive with at boot partition (sda1), a swap partition (sda2) a partition for SLES (sda5), RHEL (sda6) Ubuntu (sda7) and shared data (sda8).

I transfered my current Ubuntu 10.04 installation with partimage from the 160GB drive to the 500GB drive (sda7). I reconfigured the boot menus, changed UUIDs, ... I can boot RHEL and Ubuntu but .... when startin Ubuntu the GUI pops up, drive is working and after some time I'm getting the Login screen - but without any accounts provided so I basically can't login.

Any hints how to proceed are very much appreciated! Thanks in advance!

Kind Regards
Joerg

---

### Post by oldfred on 2010-11-24
Welcome to the forums.

I hope you are not attempting to share the /boot.  I do not recommend /boot for desktops, but some other installs create one as the file system cannot be directly booted from grub. 

It sounds like your copy of the users or copy of /home did not work correctly.

But lets look at how you are booting.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] here [ /code] tags.

---

