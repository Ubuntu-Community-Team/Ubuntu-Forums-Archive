---
title: "Installtion problems"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by Skycloud on 2007-06-26
I'm currently trying to install ubuntu, this is my 3rd try, the past 2 when I rebooted they both said 'Operating System Not Found'. Before trying to install ubuntu I tried to install gentoo maybe 2 times, before that I formated my hard drive. What should I do, I'm about to babysit my computer while installing to see what happens.

---

### Post by Scunizi on 2007-06-26
Ok.. if this is going to be a fresh install again  AND you're using the entire harddrive and not trying to create a multiboot system then I would do the following.

Delete all partitions on the drive and format using the live cd or a bootable gparted cd.

Create the partitions you want or let the live cd automatically handle it.

Install.

If you have multiple HD's in your computer and no other operating systems (maybe one being data), make sure the hd that holds the operating system is listed as the boot drive in the bios and is in the 1st drive (or 0 zero drive) connection on the ide cable.  This last item is only to eliminate any quirky motherboard issues.

Hopefully that will work for you.

---

### Post by Skycloud on 2007-06-26
I'm having a little bit of trouble deleting my partitions, how should I go about doing that?

---

### Post by Scunizi on 2007-06-26
Are you using Ubuntu Live CD or Kubuntu Live or one of the Alternate cd's?

---

### Post by Skycloud on 2007-06-26
I'm using Ubuntu Live CD.

---

### Post by Scunizi on 2007-06-26
When you get to the partition portion of the install choose 'use entire hd'.  That should automatically wipe everything out, partitions included.  If that doesn't work, choose 'manual partition' and there should be options there to delete and create..

---

### Post by Skycloud on 2007-06-26
Alright, I'm installing now, the last time I tried I don't know if it finished or not, but It opened up my CD-ROM drive, and tried to reboot I guess, but the screen just stayed black, and nothing happened.

---

### Post by Scunizi on 2007-06-26
yea.. when it's done it will tell you to remove the disk to boot into the new system.

---

### Post by Skycloud on 2007-06-26
:(Alright, it finished up, and I still get 'Operating System Not Found', I had the same problem when I tried to install gentoo. What could I be doing wrong? :(

---

### Post by dabl on 2007-06-26
Is the partition that you want to boot from marked "bootable"?

---

### Post by Skycloud on 2007-06-26
I'm not sure I'm installing in graphical mode, and just running the installer, I don't mess with anything, and I have it setup my partitions.

---

### Post by Scunizi on 2007-06-26
If you know how to get on irc using Gaim or Xchat go to irc.freenode.net and then join #ubuntu.  Ask there and you might get a different response.  I'm lost at this point..  It's a strange problem I haven't come across.  Probably simple enough though.

---

