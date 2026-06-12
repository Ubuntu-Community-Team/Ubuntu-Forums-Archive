---
title: "Installation Unsuccessful Ubuntu on HP Compaq"
date: 2013-10-13
forum: Installation &amp; Upgrades
---

### Post by dariomgsilva on 2013-10-13
Hello guy´s i´m a new guy on this forum and i need your help please. 

I have a HP Compaq amd e1-1200 apu with radeon(tm) hd graphics 1.40 ghz. 

I installed Ubuntu on laptop together with Windows and when i  restart the system gives the following error. 

\ubuntu\winboot\wubildr.mbrstatus 0xc000007b



Then i try to install by the USB way and that install normaly but when the system restart to not appearing the windows tho choose Linux or WIndows ....

---

### Post by dariomgsilva on 2013-10-14
No help?

---

### Post by varunendra on 2013-10-14
Welcome to the forums dariomgsilva!

> **dariomgsilva said:**
> ..the system gives the following error. 

\ubuntu\winboot\**[COLOR="#FF0000"]wubildr[/COLOR]**.mbrstatus 0xc000007b
...
Then i try to install by the USB way and that install normaly but when the system restart to not appearing the windows tho choose Linux or WIndows ....

WUBI is quite buggy now and doesn't always work as expected.

Regarding your second attempt-

Have you done a full installation on the hard disk now?

Did you test the USB in live mode (Test without installing option)?

Did your laptop/netbook come with Windows 8 pre-installed? If it is Win7, not win8, can you confirm if it is a UEFI based installation or not?

And last, Can you still boot into Windows normally?

---

### Post by dariomgsilva on 2013-10-14
> **varunendra said:**
> 
Have you done a full installation on the hard disk now?
I made the installation in hard disk using USB PEN

> **varunendra said:**
> Did you test the USB in live mode (Test without installing option)?
Yes.

> **varunendra said:**
> Did your laptop/netbook come with Windows 8 pre-installed? If it is Win7, not win8, can you confirm if it is a UEFI based installation or not?
Yes my netbook  come with Windows 8 pre-installed. The BIOS say something about UEFI. 
[IMG]http://i.imgur.com/qZ6E9Nv.png[/IMG]
This is in Portuguese sorry but you can see the netbook that i have. 

> **varunendra said:**
> And last, Can you still boot into Windows normally?

I install the Ubuntu and whe i restart the PC that goes directly to windows.

---

### Post by ubfan1 on 2013-10-14
At boot, if you type a function key (varies by machine) do you get to the efi boot menu to select devices or OSes?  Do you see "windows boot manager" and "ubuntu" in this list or maybe after you select the hard disk?  If you select ubuntu, do you get to the grub screen?  If you are at the grub screen, can you select ubuntu and have it boot?

---

