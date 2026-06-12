---
title: "Boot problem on new install"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by Allan Reed on 2010-01-12
After installing 9.10 I have not been able to boot. The grub loader screen comes up but any of the options selected gives the reply 'system not found'.
I have installed the system on a second hard drive with winxp on the other drive. he two ide drives are on a raid pci card but are now being run as two ide hdds.
I have put the grub loader on the linux drive (sdb) with the intention of selecting the boot drive by pressing F11 on switch on of the computer in order to load xp or ubuntu.
Should I have put grub on ths sda hdd? I am somewhat apprehensive of doing this as I may not be able to boot into any system!

---

### Post by darkod on 2010-01-12
Grub2 is OK on the linux drive, in fact it's better to be there.
But the fact that the drives are on a raid card can be the problem. Somehow, 9.10 can "see" raid settings or their remains on hdds even if the drives are not in an array actually. I can't know for sure, but I suspect this is your problem.
Boot with the 9.10 cd, Try Ubuntu option, and open Gparted. If it lists the drives only as /dev/sda and /dev/sdb, it's normal. If you see a device like /dev/mapper/blabla, then that's raid settings.
One way to get rid of them would be:

sudo dmraid -E -r /dev/sdb (do the same for /dev/sda if needed)

After that get rid of dmraid completely:

sudo apt-get remove dmraid

But the fact the drives are connected on raid card might put settings back on them right away. Do you have an option to use them without the card? If you're not using any raid the card is just complicating it for you.

---

### Post by Allan Reed on 2010-01-12
Thanks Darko, will try.

---

### Post by Allan Reed on 2010-01-12
Darko,
I have checked with g-parted and the drives are shown as sda and sdb, no odd descriptions. In the bios boot order however they show as raid 1 and raid 2.
I will look at putting them back on the motherboard.

---

### Post by Allan Reed on 2010-01-19
Darko,
   Before revamping the computer internals I tried the 9.10 alternate iso as this is said to be able to cope with raid systems.
   The text based installer seemed slower but the detailed information on the screen was very helpfull. The option to direct grub was offered at the point of its installation and recommended installing into the windows mbr on sda. I redirected this to the 9.10 disk sdb. The installation failed an offered a retry or to go back a step. I allowed the recommended installation on to sda and the install completed ok and 9.10 is running as a dual boot with winxp with the normal grub screen.
  Either the alternate downloaded iso could cope with any raid remanents on the system - or perhaps the origional install would have completed if I had allowed grub to load on the sda hdd. This is somewhat surprising as the advice to put grub on the same disk as ubuntu appears frequently on the forum.
 
                                                               Allan.

---

### Post by darkod on 2010-01-19
Since you decided to leave the drives on the raid card, it's no surprise that the alternate cd can cope better. That's why the ubuntu team is recommending it for LVM and RAID setups.
I can't really say why it didn't want to install grub to sdb, I'm not much experienced with raid.
Anyway, as long as it's working for you the way you want it, it's good. :)

---

### Post by presence1960 on 2010-01-19
Edit: didn't see you got it working!

---

### Post by justNiz on 2010-01-21
I was having similar problems with mythbuntu. Grub was not able to boot my drives in fake raid, and the installer refused to see my drives as anything other than a raid array even if I set my bios settings to IDE emulation. (the 9.04 installer saw sda and sdb just fine with any bios settings). After spending several evenings messing around trying different combinations of tweaking and reinstalling with no luck, then trying everyones suggestions above, still with no luck, subesequent install attempts showed the partioner page no longer finding/listing any drives at all (not even a raid array) for some reason.

I finally found a fix by simply booting into the CD live envronment, using aptitude to remove the dmraid and dmraid-lib packages from the live environment, then running the installer from the live desktop. Without dmraid installed, sda and sdb showed up just fine on the partitioner page so I just installed on sda as single-drive install. The installled system booted fine via grub even though I hadn't removed the dmraid and dmraid-lib packages from the installed system before rebooting. Once the new system had booted I just added sdb to fstab.

Its annoying having a mythtv system working as 2 separate drives rather than a raid 0 array which I felt is required for a myth box, as it seems concurrently recording multiple HD TV streams while watching another is highly drive-intensive. However I couldn't find another way to get 9.10 installed. I had considered setting up software raid but I also read somewhere that software raid in 9.10 has performance bugs/issues. I hope they fix nvidia chipset fake raid compatability for the partitioner and grub in 10.4.

---

