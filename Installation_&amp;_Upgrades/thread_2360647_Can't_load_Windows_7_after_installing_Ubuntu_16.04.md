---
title: "Can't load Windows 7 after installing Ubuntu 16.04 LTS"
date: 2017-05-06
forum: Installation &amp; Upgrades
---

### Post by james8314 on 2017-05-06
I installed Ubuntu 16.04 LTS on my Windows 7 PC.  I installed Ubuntu on two separate partitions of my HDD.  This is the only HDD I am using and Windows 7 is on another partition.  Prior to doing any Ubuntu installation I had my 1 TB HDD separated into two partitions.  One partition was where I installed Windows 7.  I also used and still use this partition for storing most of my files (e.g. music, movies, general use).  I had a second partition that I simply used for extra storage space.  When installing Ubuntu, I created two new partitions within this second partition to make space for Ubuntu.  One of these partitions is used for the Ubuntu OS and the other newly created partition is for storing  my general use files (i.e. the /home partition).  I installed Ubuntu using a bootable USB drive that I created with Rufus.  Ubuntu installed successfully and I am currently using it but when I start my PC, the Grub loader never appears and my PC just boots straight into Ubuntu.

I have done a few things already to try and resolve this.  I first ran Boot-repair from terminal within Ubuntu and did the "recommended repair".  That didn't do anything.  Next I created a bootable USB with Boot-repair on it and I created this bootable USB using YUMI 2.0.4.9 on my Windows 10 laptop.  Then I restarted my PC and booted from my USB and launched Boot-repair.  Once again, I did the "recommended repair" and that didn't solve the problem.  Here is the url that was generated from that session, [http://paste.ubuntu.com/24525709](http://paste.ubuntu.com/24525709).

I have run the "os-prober" command from terminal and it shows that Windows 7 is installed.  I have also run "sudo update-grub" from terminal and that didn't solve my problem.

What do you guys think?

---

### Post by efflandt on 2017-05-06
Somehow you have grub both in the MBR and in the boot sector of /dev/sda6. So maybe "sudo update-grub" is updating the one on sda6 instead of in the MBR.```
=================== Recommended repair
The default repair of the Boot-Repair utility will purge (in order to) and reinstall the grub2 of sda6 into the MBR of sda.
Additional repair will be performed: unhide-bootmenu-10s
```That should have purged grub from sda6, set it up in the MBR, and unhide the grub menu. You might try booting into Ubuntu on that hard drive and doing:```
sudo grub-install /dev/sda
sudo update-grub
```That should make sure that update-grub is updating the one in the MBR.

NOTE: I have a problem only on one PC (Dell XPS 8100 in my sig from 2010) in that 16.04.1 seemed to leave something in a state such that no text displayed during boot (reboot or cold boot). It was blank through BIOS splash and grub menu until something did graphics (gui Ubuntu login, or Win7 if previously set as default). The 16.04 desktop worked fine, no text during boot was the only issue. Lack of text during boot persisted one more time after disconnecting that drive. That is not a problem with 14.04 (still on my WDC drive w/Win7) or 16.10 (running now from mSATA SSD in SATA adapter). 16.04.1 was no problem on any other PC or laptop including much older Dells. I have not tried 16.04.2 yet.

Just thought I would mention that, so if you do not see your BIOS splash screen, that might explain why you do not see the grub menu. Although, I have Nvidia graphics and you have AMD graphics.

---

### Post by james8314 on 2017-05-07
> **efflandt said:**
> You might try booting into Ubuntu on that hard drive and doing:```
sudo grub-install /dev/sda
sudo update-grub
```That should make sure that update-grub is updating the one in the MBR.


I ran those commands (no errors) and my PC is still not showing Grub at boot and is booting straight into Ubuntu.  At this point I no longer want Ubuntu and want to have Windows 7 as my only OS.  Would restoring the master boot record from my Windows 7 install disk and deleting the Ubuntu partition resolve my problem?

---

### Post by oldfred on 2017-05-07
Do not delete Linux partitions before fixing MBR to boot Windows.
It looks like Boot-Repair's reinstall of grub ran os-prober and added Windows to grub menu.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

