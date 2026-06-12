---
title: "uninstall ubuntu"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by bubka20 on 2007-05-19
what is the proper way to uninstall ubuntu on a dual boot system?  I tried both resizing and deleting the ubuntu partition, but grub came up with error 22 when I was trying to boot back to my old Windows 98....?

---

### Post by jrib on 2007-05-19
On Windows xp you can load the "recovery prompt" from the install cd and run "fixmbr" to restore the windows bootloader.  I have no idea how to do it on window 98, but this page came up on google: [http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_98_Floppy_Disk_Method](http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_98_Floppy_Disk_Method)

The issue though, is that you want to restore the windows mbr.

---

### Post by bubka20 on 2007-05-19
Problem is that I don't have windows 98 boot disk.  I downloaded an iso boot disk and I'm brought to an A:\  .... I tried typing fixmbr and bootfix but neither did anything.... 
Any suggestions?

---

### Post by bubka20 on 2007-05-19
clarification.... I downloaded a boot cd from the following site: [http://www.answersthatwork.com/Downright_pages/Boot_Disks_and_Boot_CDs.htm](http://www.answersthatwork.com/Downright_pages/Boot_Disks_and_Boot_CDs.htm)
I set bios to boot from cd and I received an A:\    .... At this prompt I tried the fixmbr command... nothing happened.

---

### Post by seshomaru samma on 2007-05-19
google for 'freedos'
download it , burn it
boot up FreeDOS, search FDISK.EXE in the windows directory
change directory to where it resides and type ```
fdisk /mbr
```

---

### Post by jrib on 2007-05-19
> **bubka20 said:**
> clarification.... I downloaded a boot cd from the following site: [http://www.answersthatwork.com/Downright_pages/Boot_Disks_and_Boot_CDs.htm](http://www.answersthatwork.com/Downright_pages/Boot_Disks_and_Boot_CDs.htm)
I set bios to boot from cd and I received an A:\    .... At this prompt I tried the fixmbr command... nothing happened.

the page I linked to suggests a different command

---

### Post by bubka20 on 2007-05-19
got it to work with the fdisk/mbr command and then reset... 
Thanks for the help

---

