---
title: "SAMBA network printer will not print"
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2006-09-04
I have 2 Ubuntu computers one of which has a parallel port HP laserjet 2100 printer hooked directly to it (NO printer server card, etc.).

I have SAMBA setup on both computers.  Can see each of the computer from the other.

Have setup the HP printer as a local printer using printer under system administration on the computer it is physically attached to.

Have setup the HP printer on the other Ubuntu computer as a SAMBA network printer.

Have turned on detect lan printers under global settings on both computers.

Have uncommented the printing = cups & the printcap name = cups lines the smb.conf file.

When I try to print a test page from the other computer the job is placed in the que but nothing ever prints.  NO ERROR MESSAGE OCCURS.

What am I missing ???

Thanks.

---

### Post by dorhelp on 2006-10-21
I was looking for a solution to why I couldn't print to a windows computer from unbuntu when I found your post.
  If you are really trying to print from ubuntu to another ubuntu box you do not use samba for this at all. First you set up your printer on the machine with the printer installed. (if you want to use the CUPS interface you have to add cupsys to the shadow group otherwise it refusees to let you successfully enter password  
        sudo adduser cupsys shadow
        sudo /etc/init.d/cupsys restart
)
you have to edit some files by hand to get cups to listen for requests
in /etc/cups/cupsd,conf under location section add
Allow From IPaddress
Change /etc/cups/cups.d/pors.conf change liste line to
listen 631
Make sure all the coputer is listed in etc/hosts.allow 
restart cups dameon
on client machine add server to client.conf
restart cups on that machine
The printer should just show up on the client
                Good Luck

---

### Post by jsteve54302 on 2006-11-14
I'm having the problem as wpshooter, and was unable to connect to the network printer.  When i try to connect to the box I want to act as server, it refuses to authenticate under any (possibly) valid name from either box.  When trying to guess from the local name, i get nothing, though this worked when it was running XP, before the head crash.  Any hints here?

---

