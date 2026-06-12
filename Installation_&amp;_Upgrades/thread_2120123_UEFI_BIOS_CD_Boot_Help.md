---
title: "UEFI BIOS CD Boot Help"
date: 2013-02-25
forum: Installation &amp; Upgrades
---

### Post by andreuec on 2013-02-25
So I finally got myself a LiveCD and I want to try and boot my laptop from CD before installing the OS, so I can check everything works without actually modifying the Hard Disk, among other things.

The problem is I don't know how to make my laptop boot from CD.
The CD (DVD actually) should be fine.
It is a HP Pavilion g6-2254ss ([http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c03559258](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c03559258)) and it seems it has this "UEFI BIOS", which I can barely understand.
I have Windows 8 which boots in UEFI, not Legacy, and I intend it to stay the way it is (I plan to have dual boot in the future, with both OS installed).

I've tried pressing F10 while booting to edit the boot settings by moving the default options (Screenshot: [http://i.imgur.com/1tR5XGJ.jpg](http://i.imgur.com/1tR5XGJ.jpg)) to this order:

```
USB CD/DVD ROM Drive
USB Diskette on Key/USB Hard Disk
Internal CD/DVD ROM Drive
OS Boot Manager
! Network Adapter
```

and it didn't work.

I've reseted them to default and tried again in vain.
I've tried pressing F9 to get to the "Change Boot Device" screen (while in both settings) but I can't find the CD, even though it should have automatically loaded the CD while in the modified setting.
First, there is this screen ([http://i.imgur.com/DxRbYto.jpg](http://i.imgur.com/DxRbYto.jpg)) and then, there are two options: "OS Boot Manager" and "Boot From EFI File" (Screenshot: [http://i.imgur.com/FdxWlLA.jpg](http://i.imgur.com/FdxWlLA.jpg))
If I press OS Boot Manager, Windows 8 boots.
If I press Boot From EFI File, another screen appears with some options like...

```
<.>
<..>
<Microsoft>
<Boot>
<HP>
```

There are some more options once you select one of these, but whatever I press next I always end up booting Windows 8.

Does any of you know if there is something I do wrong or if something should look different... anything, any tip?

Thanks :D

---

### Post by oldfred on 2013-02-25
Someone in another thread with a different brand computer said his UEFI would never boot from a DVD in UEFI mode. He could only get UEFI boot from a flash drive.

Be sure to backup efi partition and your Windows install before installing Ubuntu. 

Use Windows to shrink the Windows install, but not to create any new partitions. Reboot into Windows several times to get it to run chkdsk and update itself to its new size.

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

           



Other HPs that have worked.
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)

    
       HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

            UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)

---

### Post by andreuec on 2013-02-26
Thanks a lot, **oldfred**! :)
I tried booting from the USB and it worked, I never thought it wouldn't work from a DVD...

---

