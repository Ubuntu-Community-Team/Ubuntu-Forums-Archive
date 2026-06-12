---
title: "how do i..."
date: 2007-01-23
forum: Installation &amp; Upgrades
---

### Post by aledelic42 on 2007-01-23
how do i change my hard drive to the ntfs format so i can dual boot with windows..
sorry im new:(

---

### Post by mandrakethepenguin on 2007-01-23
You do not need to change your HD to NTFS to dual-boot Windows. [This]("https://help.ubuntu.com/community/WindowsDualBoot") is a nice tutorial for dual-booting Windows and Ubuntu.

---

### Post by aledelic42 on 2007-01-23
actually im using fedora core 6 but the fedorda forums arent answering me..
im trying to dual boot with either xp or vista
i had xp pro on then i tried setting up a dual boot with fc6 but i guess i didnt do it right cause i can only boot linux and my xp disc wont do anything after it says setup is configuring computers hardware
my vista disc works but i cant install it cause my hard drive isnt in the right format
i have a 320 gb sata hard drive with 30gb partitioned for linux

if itd be easier to start everything over on my hard drive thats fine cause i just built my computer and i dont have any personal files on it yet

thanks

---

### Post by kerry_s on 2007-01-23
Yes, it would be easier to install windows first, make sure you install on the first partion, after that hour long install, install ubuntu on the second partion and it will take care of the dual boot setup.

Grab a copy of gparted to setup your partions-> [http://umn.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.3-0.iso](http://umn.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.3-0.iso)

make 1 ntfs and 1 ext3, you might also want to create a fat32 partion to transfer files or whatever between windows and linux. linux ntfs support is still rocky, so it's not really safe to write to ntfs with linux.

---

### Post by aledelic42 on 2007-01-23
how would i do that with fedora core 6 though
is it the same?

---

### Post by kerry_s on 2007-01-24
What about fedora, are you keeping it? The gparted cd will let you partion your disk  any which way you want, you can check it out here.-> [http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)

Here's a how to for saving data-> [http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by aledelic42 on 2007-01-25
everything got so messed up and that gparted cd didnt work
nothing would boot up without errors (fedora core, any linux discs, windows xp disc, vista disc, gparted disc) so i downloaded this killdisc thing that erased everything on my hard drive
and i decided im gonna try dual booting vista ultimate with feisty fawn which supposebly should work with my 775 chipset motherboard
hopefully thats a lot easier than fedora core
thanks for the help though

---

