---
title: "Screwed up Linux Boot File"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by kingspan on 2008-01-02
Hi all,

I screwed up my Ubuntu Boot by writing a Windows Boot record on my hard drive.  I was trying to fix a windows installation and wrote the MBR to the wrong hard drive thereby erasing my Ubutnu boot files and replacing it with Windows MBR.

Is there anyway to write over this windows MBR and recover my data on the drive?  Right now when I try and boot I get a Windows NTLDR.exe error.  

Thanks.

Garry

---

### Post by logos34 on 2008-01-02
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by kingspan on 2008-01-02
Thank you for the reply.  I tried that except I can not boot using the live cd.  I get a "Can't access tty:  Job control turned off error".  I searched the logs and founds some suggestions but nothing has worked.  

I am not sure how to proceed.

Garry

---

### Post by logos34 on 2008-01-02
> **kingspan said:**
> Thank you for the reply.  I tried that except I can not boot using the live cd.  I get a "Can't access tty:  Job control turned off error".  I searched the logs and founds some suggestions but nothing has worked.  

I am not sure how to proceed.

Garry

remove floppy if present

turn off floppy boot-up seek in Bios

reinstall grub using Super Grub disk

---

### Post by kingspan on 2008-01-03
Thank you again.  I have no floppy but I was able to get to a shell and was able to finally get to boot from a cd however it tells me I have no /bin ... .I guess it's totally trashed.  I am going to try and reload the files from the alternative CD.  

Thank you.

Garry

---

