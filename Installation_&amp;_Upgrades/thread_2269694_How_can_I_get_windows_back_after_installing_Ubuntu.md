---
title: "How can I get windows back after installing Ubuntu with dual boot?"
date: 2015-03-17
forum: Installation &amp; Upgrades
---

### Post by Clopper Almon on 2015-03-17
How can I get Windows back after installing Ubuntu?

On a new Lenovo laptop (G50-80E30) I installed Ubuntu 14.04 with dual boot, a quarter of the 1 TB hard disk left for Windows and three quarters given to Ubuntu. After the installation, Ubuntu booted nicely, but when I tried to start Windows from grub, it failed. From the Ubuntu forums, I have learned that this is a common problem officially known as Bug 1024383. It has been reported by 86 people, is given a &#8220;Critical&#8221; priority, has been known for several years, but has no one assigned to work on it.
 
The workaround note on the bug's page reads &#8220;Boot Windows from (EFI) BIOS menu or add valid Windows entries via Boot-Repair.&#8221; 

I learned that &#8220;Boot-Repair&#8221; is a free program by Yannubuntu (who first reported the bug). I installed Boot-Repair and ran it in a terminal window. It ran for a while producing voluminous output, then threw up a window offering me the possibility to make the recommended repairs. I accepted the offer, but was informed that Boot-Repair could not make those changes because the UEFI was in Legacy mode and that I should reboot Ubuntu in EFI mode and then run Boot-Repair again. 

And there I am stuck. Yes, I remember having selected Legacy mode when editing the UEFI to change the EFI boot order to put the DVD at the top of the list prior to installing Ubuntu. Evidently that was a huge mistake. Somehow, however, that boot order was changed. I have burned a Windows recovery disk &#8211; a two hour job &#8211; and of course have the Ubuntu Live disk. I turn off the computer, put one of the them in the DVD, start up, and the system goes straight to grub paying no attention to the bootable disk in the DVD. 

So how can I &#8220;Boot Windows from (EFI) BIOS menu&#8221;  or &#8220;reboot Ubuntu in EFI mode&#8221;?

---

### Post by oldfred on 2015-03-18
You cannot if Ubuntu is installed in BIOS mode and Windows is in UEFI mode. You have to totally reboot to switch from BIOS to UEFI or vice-versa.

Did Boot-Repair convert Ubuntu install to UEFI by installing grub-efi-amd64?  Then it may be you left Windows hibernated or fast boot on. 
Grub really only boots a working Windows. That means no hibernation and no chkdsk flag set. Best just to have Windows repair flash drive as you cannot always boot Windows directly even on a Windows only system.

Post link to summary report from Boot-Repair.

What brand/model system? 
Some also have a fast UEFI boot setting separate from the Windows hibernation fast boot. That needs to be off or set to allow you to get into UEFI from key board.
Only if repair flash drive is bootable will you have that option in UEFI boot menu. Best to verify that is it correctly created.
You should also have a one time boot key, like f10 or f12 but varies by vendor.

---

### Post by Clopper Almon on 2015-03-18
Thanks, Oldfred, for taking a look at my cry for help.

The make and model, as mentioned, is Lenovo G50-80E30. The URL for the Boot-Repair summary report is: [http://paste.ubuntu.com/10624217](http://paste.ubuntu.com/10624217)

Windows was definitely shut down with fast boot on. That was a pitfall I learned about only later, and I have definitely fallen into the pit.

I have read the instructions for making a bootable USB drive for Windows, but they require that Windows be up and running, so I cannot use that approach. I also looked into Restore and Reset, but the Microsoft instructions require that Windows be running.

The Ubuntu Linux that is running on the computer is quite lame. For example, after each reboot, one and only one access to the Internet is allowed. One and only one "Files" window will open, so no drag-and-drop copying is possible. 

I have no files on the computer which need to be preserved, so a total reboot is not a bad option. I can even buy a Windows 8.1 disk inexpensively, but since neither the Ubuntu Live disk nor the Windows DVD that I made (as described) will boot, I suspect that that disk would not either. In other words, I think the attempt to install Ubuntu somehow changed the boot sequence that I had set in the UEFI in Windows. Is there any way to reset the boot sequence from Linux?

Thanks for your attention.

---

### Post by oldfred on 2015-03-19
Are you able to get into UEFI boot menu or does one time boot key work.
Since system is UEFI, you should still be able to directly boot Windows from UEFI boot menu. You may have to turn back on UEFI, or other settings.
Some will not boot anything other than Windows if you have secure boot on in UEFI. Others require you to authorize anything else to boot and/or secure boot off.  I do not think users with Lenovo's have required a password, but some systems require to to set a UEFI password (never lose that) to allow any settings in UEFI.

An older Lenovo user posted this a year or two ago:
 > Lenovo's  buggy EFI Bios is will not boot from a DVD at all unless you enable 'legacy' (which you can't do because it screws with Windows 8!)
 The work around was to turn ON 'Legacy' boot mode in the BIOS and turn OFF "secure-boot" mode from locking out Ubuntu), and also make sure to turn OFF 'Legacy' SATA AHCI to ATA.
Then I installed Ubuntu from a USB stick (because these settings would only boot the Ubuntu installer from USB, but not DVD). 

      
 T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)

I do not use Unity, but you can open multiple Windows. I just do not like having to click two times as you have to then choose which you want when you have two open. I use fallback which is very similar to the old gnome2 gui with top & bottom panels and bottom panel shows open windows so I can directly click to something else.

 If you do not like Unity, use K/L/X ubuntu or the DE/ WM of your choice. 
Difference between Windows manager & desktop enviroments
[http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893](http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893)

If you have multiple gui's you have to choose as you log in.

 Classic, fallback, flash back explanation -  by kanasnoob 
[http://ubuntuforums.org/showthread.php?t=2185161](http://ubuntuforums.org/showthread.php?t=2185161)
How to choose Display manager sessions -  by kanasnoob 
[http://ubuntuforums.org/showthread.php?t=2184682&p=12929682#post12929682](http://ubuntuforums.org/showthread.php?t=2184682&p=12929682#post12929682)

I think the new name is gnome-panel.
[https://wiki.gnome.org/Projects/GnomeFlashback](https://wiki.gnome.org/Projects/GnomeFlashback)

---

### Post by Clopper Almon on 2015-03-20
Thanks again,Oldfred. No, I cannot get into the UEFI menu, and the one-time boot keys did not work. I also tried efibootmgr, but it could not find the UEFI files it needed to work on. I presume that it had that problem because I had turned on Legacy mode before I booted Ubuntu. 

In any event, before my return period expired, I got the seller, Best Buy, to take it back. I give them high marks for that and will give them all the business I can in the future. I figure Lenovo will know what to do with it. Unfortunately, Lenovo has discontinued the model, and Best Buy had no more. I was able to order another from Amazon.
   
I am working on some edits to the Ubuntu installation wiki which I hope will help others avoid these problems.

---

