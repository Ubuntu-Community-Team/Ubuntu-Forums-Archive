---
title: "[SOLVED] multi-boot"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by two4two on 2008-03-07
I have 3 physical hard drives.  On primary master (C) was Win98SE.  I reserved primary slave (D) for WinXP, which I didn't install yet.  On secondary master (E) I installed UBUNTU.  It booted up both OSs OK.  Then I installed an UltraATA133 controller card.  Didn't move the cable; just installed the card.  Win98SE only boots in safe mode; UBUNTU boots OK.  I can take care of Win98 issue (I hope!).  Then I moved the cable for the primary to the UltraATA133 card.  Grub can't find an OS.  OK, I think I can recover Win98SE by re-installing it while the cable is attached to the Ultra but stopping before it re-loads all of Windows.  This gets the Win98 mbr back, and so I'll lose Grub loader.  Then I'll install WinXP on primary slave while cable is mounted on the motherboard, and after success. move the cable back to the Ultra.  Finally, I'll reinstall UBUNTU onto the secondary master while the cable is mounted on the Ultra card.  This will give me the grub loader instead of the WinXP loader.  Anyone see a problem with this so far?  But I want to recover the WinXP loader and use a boot.ini file.  How do I do that (assuming all of what I outlined above works).  Thanks for reading.

---

### Post by -random on 2008-03-07
Is it possible for you to have all 3 physical hdd's in at the same time?

Have you tried:

installing win_xp while the 98se_hdd isn't in,

then plug in all hdd's
 and then install ubuntu (on the ubuntu hdd/parition).

(very important to install ubuntu last, since you want to install the grub so that it can see both of the windows partitions).

?

---

### Post by two4two on 2008-03-07
Thanks random.  Yes.  All three HDDs are installed at the same time.  They are now on the Ultra card: primary master/slave and secondary master.  I have fixed the problem with the Ultra card.  Somehow, just the act of putting it in messed up the video driver.  I set the BIOS to clear and then reinstalled the video driver.  Win98SE boots OK now in normal mode.  Also, I did a FDISK /mbr to get the Win 98 loader back.  So next I will install Win XP on Ultra's Primary slave.  Finally I will install ubuntu on Ultra's secondary master.  I think this will set grub as the boot loader; not Win XP (ntldr) and boot.ini.  I like boot.ini because I can edit it from all 3 OS's. -- two4two

---

### Post by -random on 2008-03-08
Cool man..

let me know if you get stuck with the installation or something. Good luck!

---

### Post by two4two on 2008-03-10
OK, prior to installing the UltraATA133 PCI add-in HD controller I had already installed ubuntu on the secondary master plugged into mobo.  But now that I've re-installed Win98SE and WinXP there is no BRUB anymore.  When I use the ubunto CD as a Live Linux and boot from it I can see the files on the HDD on which I had originally installed ubuntu.  How would I modify my Windows boot.ini file to simply include the prior ubunto OS on that HDD?  How do I find the ubunto hdd designation for that drive?  The drive has two partitions:  an OS partition for ubunto and a swap partition as ubunto requires it.  It is the secondary master on the UltraATA133 IDE controller card PCI add-in card.  What lines do I add to the ntldr's boot.ini file so that the ubunto install could be found and booted to?

---

### Post by -random on 2008-03-10
Is there a specific reason that you want the loader to be ntldr?

If ubuntu is your last operating system installation it'll configure the grub for you automatically for all the other operating systems.

I don't have windows anymore, so soz i can't help you with the boot.ini file. Here's the link to microsoft's site about that bit [http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022) . 'sudo fdisk -l' in ubuntu console gives information about the partitions you might need?

> **-random said:**
> (very important to install ubuntu last, since you want to install the grub so that it can see both of the windows partitions).

The easiest will be to just install ubuntu over again and let it worry about boot configurations. From there we can help you to change the options / boot order, time out etc...

---

