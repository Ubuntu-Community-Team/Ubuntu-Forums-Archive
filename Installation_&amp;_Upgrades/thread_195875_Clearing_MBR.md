---
title: "Clearing MBR"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by dstein on 2006-06-13
Before I installed Ubuntu on my second Hard Drive, I had Suse installed. When installing Suse, i believe I originally put Grub on my second hard drive, but then reinstalled it onto my first hard drive, because the BIOS looked at the first hard drive first. Anyhow, when installing Ubuntu, I installed Grub on the 1st hard drive. When I boot my computer normally, there is no problem. But I would like to clear the MBR of my second hard drive, cause I know there is leftover junk in it. For example, when I change my BIOS settings to boot from the second hard drive, I get "Can not load Operating System", but I would prefer for it to just load Ubuntu without any boot loader options. How should I go about doing this? Thanks.

---

### Post by jaa1180 on 2006-06-13
[QUOTE=dstein]When I boot my computer normally, there is no problem. [/QUOTE]
does this mean off the first HDD, into Ubuntu?
What is the output of your menu.lst? 

> when I change my BIOS settings to boot from the second hard drive, I get "Can not load Operating System", 

Is this booting Suse? or another install of Ubuntu?

---

### Post by DoctorDread on 2006-06-13
You need to FDISK the mbr. Get to a command prompt and type fdisk /mbr once or twice to clear the MBR. This is the DOS way of clearing the MBR so I am not too sure if it will work for Linux. I have never had to do it for Linux. I hope this helps.

Someone correct me if I am wrong..

---

### Post by dstein on 2006-06-13
I believe that fdisk /mbr clears the mbr of the first HD. I also believe that it clears it for use with Windows. I would like to clear it to the way it came when I bought it.

---

### Post by jaa1180 on 2006-06-13
[QUOTE=dstein]I believe that fdisk /mbr clears the mbr of the first HD. I also believe that it clears it for use with Windows. I would like to clear it to the way it came when I bought it.[/QUOTE]

that is right. I wanted to see if there was anything else I could offer...
Sorry, should have stated that first.

---

