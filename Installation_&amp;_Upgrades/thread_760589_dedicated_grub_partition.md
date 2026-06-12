---
title: "dedicated grub partition"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by TheDro on 2008-04-20
I've been reading about dual booting and grub for about a week now and I am still slightly confused about one thing.

I am planning on creating a dedicated grub partition, which will of course be what I use to choose which operating system to boot, but based on the installation walkthrough I've been reading, you have to install grub on the MBR (master boot record). Does this mean that even if I have a dedicated grub partition, I still need to install grub to the MBR and I have to install it for every distribution or can I choose not to install grub when I install ubuntu?

---

### Post by mikewhatever on 2008-04-20
You don't need to put GRUB to MBR, but something else must be there, because whatever that is, it starts the boot process. You also do not have to install GRUB for every distro, but then you'll need to know how to boot them. Alternate install CD allows to install Ubuntu without GRUB.

---

### Post by sandysandy on 2008-04-20
GRUB is a bootloader. normally it is in MBR because thats where the computer will look for the IPL (initial program loader). as told by mikewhatever, something must be there in MBR to start the boot process.

here are some links

[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

[http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)

regards

---

### Post by LeoSolaris on 2008-04-20
> **TheDro said:**
> I've been reading about dual booting and grub for about a week now and I am still slightly confused about one thing.

I am planning on creating a dedicated grub partition, which will of course be what I use to choose which operating system to boot, but based on the installation walkthrough I've been reading, you have to install grub on the MBR (master boot record). Does this mean that even if I have a dedicated grub partition, I still need to install grub to the MBR and I have to install it for every distribution or can I choose not to install grub when I install ubuntu?


You don't need a dedicated partition for Grub. It will pick up on the other distros and XP when placed on the MBR. Without it on the MBR you will likely have XP's bootloader starting everything, which will not recognize anything other than XP. It will multiboot pretty much automaticly, if ya install Ubuntu last. (that's the easier way anyways.)

Leo

---

### Post by confused57 on 2008-04-20
This may help you decide if you really want a dedicated grub partition:
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_)

---

### Post by TheDro on 2008-04-21
Thanks for the help. That is the documentation I was already using and it's pretty good. The only thing that seems to be missing is where to get some of the files you need for grub. Luckily I had installed super grub on my usb thumbdrive to test things out before  so I could copy those files. In his walkthrough he supposes you already have grub installed as well as linux whereas I was doing everything from the liveCD. 

Grub is working fine even though I only have one operating system on my computer for now :P. Btw, is there a way to modify menu.lst through grub or windows? (just because booting the CD is kinda a long)

---

