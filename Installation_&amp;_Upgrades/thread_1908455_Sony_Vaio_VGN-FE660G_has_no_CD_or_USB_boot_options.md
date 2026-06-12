---
title: "Sony Vaio VGN-FE660G has no CD or USB boot options"
date: 2012-01-13
forum: Installation &amp; Upgrades
---

### Post by Em-Digity on 2012-01-13
Hey Guys. Been trying to install 11.10 on an older XP machine. First via CD (burned ISO) to no avail, then via USB via  USB installer from pendrivelinux.com also with no luck.

Problem is the only boot options listed in the BIOS are:

-Floppy Disk Drive (external) 
-Internal Optical Drive
-Internal Hard Disk Drive
-Network

Also tried the Plop Boot Manager v5.0. Tried both .com installs; says they cannot run from a windows dos window. Tried from safe mode with command line; nope. Tried burning the ISO to CD->the machine doesn't recognize the files on the disc (this machine does). 

What next? Any other options?

Thanks.

---

### Post by BC59 on 2012-01-13
Go [here]("https://help.ubuntu.com/community/Installation/FromUSBStick#PLoP_Boot_Manager") and check the capital of PLoP Boot Manager.

---

### Post by Em-Digity on 2012-01-13
> **BC59 said:**
> Go [here]("https://help.ubuntu.com/community/Installation/FromUSBStick#PLoP_Boot_Manager") and check the capital of PLoP Boot Manager.

Thanks for the response. InstallToBootMenu.bat completes successfully, but I do not see "Plop Boot Manager" in the boot options menu upon reboot (invoked by F8 ). 

What am I missing?

---

### Post by coldraven on 2012-01-13
Did you select "Burn Image" when making your boot CD?

---

### Post by Em-Digity on 2012-01-13
> **coldraven said:**
> Did you select "Burn Image" when making your boot CD?

Yes, I used the windows disc image burner (Windows 7). But there is no option to boot from CD in the BIOS of the sony.

---

### Post by coldraven on 2012-01-13
> Problem is the only boot options listed in the BIOS are:

-Floppy Disk Drive (external) 
-Internal Optical Drive
-Internal Hard Disk Drive
-Network

Internal optical drive? You said there was no option, I'm confused.
If it is listed make sure it is at the top of the list.

---

### Post by Em-Digity on 2012-01-13
> **coldraven said:**
> Internal optical drive? You said there was no option, I'm confused.
If it is listed make sure it is at the top of the list.

Didn't realize that was the CD-ROM. Thanks. But still, it's above the hard-drive and doesn't boot it. 

I went ahead and put it at the top; still no luck. 

When I explore the CD in windows it shows nothing on the Sony (but DVD's will play).

Same CD on another machine shows the burned contents. Could there be an issue with the cd-rom drivers?

---

### Post by Em-Digity on 2012-01-14
Ok, made some progress. Looks like the CD/DVD drive was just dirty ](*,)
It's booting it. Trying to install now... Thanks for the help. I'm sure I'll need more :D

---

