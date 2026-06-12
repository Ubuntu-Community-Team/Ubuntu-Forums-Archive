---
title: "Alternative dual boot, booting from boot.ini"
date: 2005-03-08
forum: Installation &amp; Upgrades
---

### Post by oti on 2005-03-08
A number of other linux distributions i have used were easy to setup as booting through boot.ini . I do NOT want to boot to MBR because of troubles i am sure will arise due to having linux on hdb1 and windows xp on hdc3 or similar.

So i have installed grub on the partition /dev/hdb1 and gone about making a boot file from the boot sector with partboot.

Following the regular procedures i can get a linboot.bin file output using *partboot* in windows, which is 1kb in size, but when i try and boot from this i get an error message along the lines of "cannot find <windows root>/system32/hal" (regardless of what it says, it's definately trying to boot windows somehow.)

I have ubuntu set up with a single 10gb partition mounted on / (ie. no separate /boot partition).

Are there any options for me other than doing a clean install of windows to HDA1 and ubuntu to HDA2? I am confident with installations on those drives that grub on MBR will not give me problems.

Edit: I should also add that i used the  dd if=/dev/hdc2 of=/bootsect.lnx bs=512 count=1 command in the ubuntu install shell (alt/ctrl+F2 when it asks about partitions) after mounting my ubuntu installation from /dev/discs/disc2/part1/disc to /ubuntu and chrooting to /ubuntu/ as stated in the guide. Then used explore2fs to copy the output file to a the windows drive to boot from.

---

### Post by kamstrup on 2005-03-08
I am not and expert here but the "map" command in Grub might be helpful here... See [this thread](http://ubuntuforums.org/showthread.php?t=18501).

Swapping the HDs in your box so that the Ubuntu partition with grub is hda and then use the map-command to cheat Windows into thinking that it is reciding on hda even though it might sit on hdb... Wow, that sounded complicated :)

Cheers

---

### Post by Asycas on 2005-03-08
Does this method apply for Ubuntu too?

[http://www.aboutdebian.com/dualboot.htm](http://www.aboutdebian.com/dualboot.htm)

I'm thinking of installing Ubuntu on my comp and dual booting with Windows, but I've heard of certain problems you have if you let GRUB overwrite the MBR, so is it possible and safer to use boot.ini instead? Besides, I want it to be easier to remove Ubuntu if I need to, for some remote reason.

---

### Post by kamstrup on 2005-03-08
It depends very much on your hd-layout Asycas... If you just have one harddisk with several paritions, and windows on the _first_ partition, there's no trouble at all... At least I've had none. Just install grub to MBR away :)  ... Removing it again is another matter... But why would you ever do that?

There's an awful lot of documentation at the end of that link... I don't think it is that complicated :) It seems to cover just about any possible setup with any possible bootloader...

---

### Post by Asycas on 2005-03-09
So it is possible to use boot.ini?

Ubuntu sounds really good, and I don't think I might ever want to remove it, but I'm quite new to linux and want to keep that possibility easily open... just in case (I'm an extremely paranoid person) And I have read of some problems people meet with when they use GRUB... just want to be sure...  ;)

---

### Post by kamstrup on 2005-03-09
If you want to be able to remove ubuntu/grub/linux easily you shouldn't install grub to MBR.

I don't know much about boot.ini, but everything is possible - this is Linux :) It is just a question of how hard it is to do ;P

Grub should suffice for almost any setup as far as I know. It is a really advanced bootloader...

Keeping Windows on you first partition and installing grub+Ubuntu on some other partition and making that one the active one should not pose any problems as far as I know... You could then remove everything just be formatting that partition and setting you Windows partition to be the active again...

---

