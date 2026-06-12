---
title: "Multibooting With 4 Linux Distros"
date: 2007-08-11
forum: Installation &amp; Upgrades
---

### Post by ohitsmee on 2007-08-11
Thinking of install Debian, Suse, Ubuntu, Blag 5000 on laptop. Currently have Ubuntu and SUSe install and it. Thinking of wiping it out completely. Any recommends on order in which distos should install first and so fort.

Also on my desktop my wireless card is seeing my 2 router but cannot get ip from either of them even if i reset both to default. I attacted screen shots when i do ifconfig and iwconfig.

---

### Post by tgalati4 on 2007-08-11
I went through a similar exercise on a desktop.  Each install resulted in scrambling GRUB.  The solution for me was to use a Super Grub floppy and it detected all of the grub menu.lst entries.  Once I could see all of the distros, I printed out the Super Grub config file and picked one of the Grubs and manually edited menu.lst so that it would work properly.  It's time consuming but it works.

As you go through each install, be sure to install Grub on that distro's partition and no other, otherwise you will get hopelessly confused and end up breaking more than installing.

Expect to spend a couple of hours and 20 or so reboots until you get everything configured.  

Never heard of Blag 5000.

---

### Post by rpw on 2007-08-11
Hello,

I'm doing it in a completly different way, I'm using GAG-Bootmanager ([http://gag.sourceforge.net/](http://gag.sourceforge.net/)) and install the GRUB only on the partition where the distro is installed (not into MBR). And then I don't really care for entries of other systems in the GRUB-files.

Regards,

rpw

---

### Post by louieb on 2007-08-11
And heres another way. I went ahead and used the the  [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") and carved up my drive for half a dozen or so distros. 1st distro I Install GRUB to the **MBR**. For the 2nd,3rd,... installed GRUB to the **boot sector** of its / (root) partition. Then modified the 1st Distribution's menu.lst to chainload the 2nd, 3rd  ... distribution.   
More on chainloading and using the configfile option can be found here [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/"). Both chainloading and configfile are pretty easy and they keep thing straight when one of the distributions does a kernel update.

BTW: the dual boot site has some good stuff on GAG too.

---

### Post by adrian15 on 2007-08-26
> **tgalati4 said:**
>  The solution for me was to use a Super Grub floppy and it detected all of the grub menu.lst entries.  Once I could see all of the distros, I printed out the Super Grub config file and picked one of the Grubs and manually edited menu.lst so that it would work properly.  It's time consuming but it works.
.

So you did not use neither the configfile nor the chainloading method. 

**Do you mean that you edited all your menues, wrote them to a paper and then write them back into your current menu.lst???**

Didn't you think to mount the other distro's partition as root and copy-paste the menu.lst important parts neither?

adrian15

---

