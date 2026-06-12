---
title: "Unable to create &quot;Persistent&quot; Ubuntu 20.04"
date: 2020-07-10
forum: Installation &amp; Upgrades
---

### Post by alok8 on 2020-07-10
I am using Yumi to create persistent (1 GB) Ubuntu 20.04 on a 16 GB USB but unable to make the installation as persistent. casper -rw is created but don't know why it doesn't save the session and once I restart the system, everything resets. Any help?

---

### Post by C.S.Cameron on 2020-07-10
What version are you using, BIOS or BIOS/UEFI? (2.0.7.1 or 0.0.2.3)

---

### Post by alok8 on 2020-07-10
BIOS/UEFI
Does that makes any difference??

---

### Post by C.S.Cameron on 2020-07-11
If USB is made using YUMI BIOS, (YUMI-2.0.7.1), it will not boot in UEFI mode. Suggest using YUMI BIOS/UEFI, (YUMI-UEFI-0.0.2.3), it boots in either mode. Only problem is that persistence is limited to 4GB, but I see you are booting okay.

I now recall that with Ubuntu 20.04 persistence files named "casper-rw" no loner work. You must change the name to "writable".

Persistence partitions named "casper-rw" still work though.

---

### Post by alok8 on 2020-07-12
You mean to say I've to rename the "casper-rw" folder to "writeable"?

---

### Post by ActionParsnip on 2020-07-12
You could sidestep all of this and just install to the USB like it was an internal drive

---

### Post by C.S.Cameron on 2020-07-12
> **alok8 said:**
> You mean to say I've to rename the "casper-rw" folder to "writeable"?

Yes, just rename the casper-rw file. Not the folder. You may need to be root.

---

### Post by C.S.Cameron on 2020-07-12
> **ActionParsnip said:**
> You could sidestep all of this and just install to the USB like it was an internal drive

Perhaps alok8 is using YUMI because he wants to multiboot a lot of OSs. Multiboot can be done with Full installs but not as quickly as with YUMI or Ventoy.

Come to think of it Ventoy might be an option to YUMI, It can use persistence files greater than 4GB both BIOS and UEFI

---

### Post by C.S.Cameron on 2020-07-12
Just to confirm: 
Created a persistent USB using YUMI-2.0.7.1, formatting was FAT32, MSDOS partition table, (GPT would not work), made casper-rw 1GB.
Booted the drive and made some changes to test persistence, confirmed that it was not persistent.              
Plugged the drive back into a Windows machine, selected the drive in Files and opened the ubuntu-20.04-desktop-amd64 folder.
Changed the name of casper-rw to writable.
Drive is now persistent.

---

### Post by alok8 on 2020-07-12
> **C.S.Cameron said:**
> Perhaps alok8 is using YUMI because he wants to multiboot a lot of OSs. Multiboot can be done with Full installs but not as quickly as with YUMI or Ventoy.

Come to think of it Ventoy might be an option to YUMI, It can use persistence files greater than 4GB both BIOS and UEFI

Actaully, I'm having some issues with my Window 10, so looking an alternative OS to get my things going on. Ubuntu will be my only OS on the USB stick.

---

### Post by alok8 on 2020-07-12
> **C.S.Cameron said:**
> Just to confirm: 
Created a persistent USB using YUMI-2.0.7.1, formatting was FAT32, MSDOS partition table, (GPT would not work), made casper-rw 1GB.
Booted the drive and made some changes to test persistence, confirmed that it was not persistent.              
Plugged the drive back into a Windows machine, selected the drive in Files and opened the ubuntu-20.04-desktop-amd64 folder.
Changed the name of casper-rw to writable.
Drive is now persistent.

Thanks,will try and let you know the result on my end.

---

### Post by alok8 on 2020-07-12
It worked for me &#128512;.
Thanks a lot. 
Also, mailed YUMI about the same issue and their response is similar one. Hope they can fix the issue in next update of YUMI.

---

### Post by C.S.Cameron on 2020-07-12
> **alok8 said:**
> Actaully, I'm having some issues with my Window 10, so looking an alternative OS to get my things going on. Ubuntu will be my only OS on the USB stick.

If you are usin the stick to replace your hard drive then ActionParsnip's suggestion to make a Full install to USB is probably better than using a Persistent install, however a Full install can not install Ubuntu to your PC except by cloning itself.

---

