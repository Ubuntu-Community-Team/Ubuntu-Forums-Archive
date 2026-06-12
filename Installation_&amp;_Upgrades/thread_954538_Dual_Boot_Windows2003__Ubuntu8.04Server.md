---
title: "Dual Boot Windows2003 / Ubuntu8.04Server"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by GerryH001 on 2008-10-21
Hi all,
it's a simple question: is there a way to dual boot windows 2003 / Ubuntu 8.04 server? I would like to test some things like performance, before switching to ubuntu server. 

So the situation is this:
- a windows 2003 server, three harddisks. Harddisk 1 is for OS, 2 en 3 are for data. All formatted in NTFS.
- Harddisk 1 has 100 Gbyte left (should do it).
- I want to install Ubuntu server next to it. Sadly enough, it will not automatically modify grub. 

Ubuntu is on sda5 and sda6, windows i noticed is on sda1. Probably something to add in fstab, then modify menu.lst, but what? 

Any help is greatly appreciated.
Grt GerryH

---

### Post by logos34 on 2008-10-21
If you want to continue using the Grub for the existing ubuntu installation, during install of the server edition make sure to specify that grub is written to the server / partition, not the default location (MBR).  [Edit:  the server edition uses the text-based install layout--the bootloader settings screen is one of the last steps.]  Change the grub location from 'hd0' to whatever the server root is (use '/dev/sda?' format to avoid confusion).  Then as you guessed add an entry to menu.lst and a line in /etc/fstab if you want to be able to mount/access it from the other ubuntu.

---

### Post by GerryH001 on 2008-10-21
Tx for the information! I will dig into this evening, probably with vms to test this out. I will create a windows 2003 vm, leaving some space for ubuntu which will follow. 
I have done some installing of ubuntu now, but am not sure where the advanced setting is. I will come back with the info.

And I found this rather old, but nevertheless
[promising manual]("http://www.psychocats.net/ubuntu/mountwindowsfstab").

---

### Post by GerryH001 on 2008-10-22
> **GerryH001 said:**
>  
I have done some installing of ubuntu now, but am not sure where the advanced setting is. I will come back with the info.
[/URL].

Hello Logos34, I discovered the setting. Strange thing happened the first time, the bootloader did not find the windows setup. Next few vms i created all worked with the automated grub "looking for other OS" feature in the install setup.

Yep! I will install this on my home server. My goal is to replace my current windows2003 setup (AD, domain, dns, ftp, iis, exchange2007, fileserver) for an ubuntu setup (openLDAP, samba, bind, vsftpd, zarafa ([www.zarafa.com](www.zarafa.com)), samba). To be used with several windows workstations.
Next stop: trying to get outlook and wine to work :-)

---

