---
title: "HDIO_GET_IDENTITY failed for '/dev/sdb' after upgrade"
date: 2013-05-20
forum: Installation &amp; Upgrades
---

### Post by htubi on 2013-05-20
Three weeks ago I upgraded my dual boot (Windows/Ubuntu) Asus computer to ubuntu 13.04.  The configuration was different - in that it designated the Windows partition as OS - but it worked.  Until today.  

I booted and got this error message:
ata_id (296:) HDIO_GET_IDENTITY failed for /dev/sdb: Invalid argument

Then a message BusyBox v1.20.2 etc

and a prompt:
(initramfs)

I've searched to find how others have dealt with this error but mainly find people using external drives ...

All help appreciated.
Thanks.

Howard (htubi)

---

### Post by 2F4U on 2013-05-20
Is the Windows system booting without issues? Maybe there are bad sectors on the Ubuntu partition?

---

### Post by htubi on 2013-05-20
> **2F4U said:**
> Is the Windows system booting without issues? Maybe there are bad sectors on the Ubuntu partition?

Yes, Windows is rebooting.  
I have just booted with a live CD of 12.04 and went into terminal.  
With 'ls', I couldn't find /dev/sdb, but was also told /dev/sda is not a directory ...  

On opening GPartEd, I see that my partition for linux is SDA3, with sda5 being / and sda6 /home

Could I just rename sda3 sdb?

Howard

---

### Post by htubi on 2013-05-20
> **2F4U said:**
> Is the Windows system booting without issues? Maybe there are bad sectors on the Ubuntu partition?

Yes, Windows is rebooting.  
I have just booted with a live CD of 12.04 and went into terminal.  
With 'ls', I couldn't find /dev/sdb, but was also told /dev/sda is not a directory ...  


Now I've booted with a Live CD.

I cannot dev/sdb (using 'ls' in terminal), and am told that /dev/sda is not a directory.

I've looked at it with GParted, and see that the linux partition is /dev/sda3
dev/sda5 is /
dev/sda6 is /home

Should I just rename /dev/sda3 /dev/sdb?



Howard

---

### Post by gonehiking on 2013-05-20
You definitely do not want to rename device files.

It would seem you have added a new disk to your system - SATA/SCSI/USB, which is showing up as /dev/sdb. This new disk, I bet, does not have a partition table which causes hdparm to fail to read the UUID and ubuntu startup scripts are not tolerant of that. Easiest way to boot up your system in Ubuntu would be to stop the system in grub, edit the kernel command line, replace the part of kernel command line that says something like "root=UUID=....." with "root=/dev/sda5" and then boot with CTRL-x or F10. This will boot your system in Ubuntu and then you can repair it by editing /etc/default/grub to give explicit root fs partition as /dev/sda5 (not the recommended saolution), or put a partition table on the new disk (preferred solution).

---

### Post by htubi on 2013-05-21
Thanks.  The system has no new hard disk, although from time to time I obviously do plug other drives into the USB port.   
Anyway, therefore I I tried the less recommended solution.
Unfortunately, on editing the kernel command line, I didn't succeed in booting - just got the error message"/dev/sda5 not recognised" 

Perhaps there's another name for the location /dev/sda5

---

### Post by htubi on 2013-05-21
Solved ...   I booted with a live CD and followed the advice here: 
[https://sites.google.com/site/easylinuxtipsproject/grub](https://sites.google.com/site/easylinuxtipsproject/grub)

and when I tried 
[COLOR=#0000FF]sudo mount /dev/sda5 /mnt  [/COLOR]
I got an error message which I searched and then found the advice to do something like
sudo efsck -f 
which took me completely out of my depth, resizing inodes (what are they?) and fixing numbers, but ended up somehow solving the problem.
It was a bit hair-raising, but at least I'm now booting OK.

Thanks to the people who tried to help.  [COLOR=#0000FF]



[/COLOR]

---

