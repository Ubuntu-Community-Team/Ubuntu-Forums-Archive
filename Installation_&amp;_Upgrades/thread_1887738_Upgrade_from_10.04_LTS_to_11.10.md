---
title: "Upgrade from 10.04 LTS to 11.10"
date: 2011-11-27
forum: Installation &amp; Upgrades
---

### Post by chudder on 2011-11-27
Hi Ubuntu Forums Users,

I've been a long Ubuntu fan but I haven't whipped my machine out in a year.  It has 10.04 LTS on it.  Ever since I put Ubuntu on this laptop I've had a set of partitions that made it relatively easy to ensure I keep my files, music, etc.

I have a screen shot of my partitions, they may seem odd or unorthodox but they've worked well for me.  

/dev/sda1 is the Ubuntu OS
/dev/sda5 is simply swap space
/dev/sda6 is my files

As I recall, what I would do when upgrading is format the sda1 partition and leave the other two as is.  The mount points are what I've done in the past, I wrote that down.

The question I have is at the bottom of the photo, "Device for boot loader installation".  Should I choose sda1, since that is where the OS is? I can't remember what I did there.

I attached another photo showing the choices I have for that.

Thanks in advance,

chudder

---

### Post by fantab on 2011-11-27
> **chudder said:**
> Hi Ubuntu Forums Users,

I've been a long Ubuntu fan but I haven't whipped my machine out in a year.  It has 10.04 LTS on it.  Ever since I put Ubuntu on this laptop I've had a set of partitions that made it relatively easy to ensure I keep my files, music, etc.

I have a screen shot of my partitions, they may seem odd or unorthodox but they've worked well for me.  

/dev/sda1 is the Ubuntu OS
/dev/sda5 is simply swap space
/dev/sda6 is my files

As I recall, what I would do when upgrading is format the sda1 partition and leave the other two as is.  The mount points are what I've done in the past, I wrote that down.

The question I have is at the bottom of the photo, "Device for boot loader installation".  Should I choose sda1, since that is where the OS is? I can't remember what I did there.

I attached another photo showing the choices I have for that.

Thanks in advance,

chudder

Why fix it, if it ain't broken? (Next LTS release will be 12.04 it is due in April 2012).

Your /dev/sda1 =' / '
Is /dev/sda6 = ' /Home ' or just Linux data without any mount-point?

If it is '/home' then I suggest you BACKUP Your Important Data. **It is advisable to NOT use /home from 10.04 (gtk2 engine) with 11.10 (gtk3 engine) there may be issues later**.  Its better to be safe than sorry. So my suggestion will be (if its /home) to back up your data and format it clean when using with 11.10. 

As for GRUB you will have to install it to **/dev/sda** ONLY and not to /dev/sda1.

---

