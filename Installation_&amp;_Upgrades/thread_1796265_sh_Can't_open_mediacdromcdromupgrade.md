---
title: "sh: Can't open /media/cdrom/cdromupgrade"
date: 2011-07-03
forum: Installation &amp; Upgrades
---

### Post by techbrainless on 2011-07-03
Hi All , 

I am trying to upgrade from ubuntu 10.04 to 10.10 via the alternate CD/DVD , following the instruction mentioned at the link [https://help.ubuntu.com/community/MaverickUpgrades](https://help.ubuntu.com/community/MaverickUpgrades)

after executing the last step which is :
```
gksu "sh /media/cdrom/cdromupgrade"
```

I am getting error 
```
sh: Can't open /media/cdrom/cdromupgrade
```

---

### Post by Ranko Kohime on 2011-07-03
> **techbrainless said:**
> Hi All , 

I am trying to upgrade from ubuntu 10.04 to 10.10 via the alternate CD/DVD , following the instruction mentioned at the link [https://help.ubuntu.com/community/MaverickUpgrades](https://help.ubuntu.com/community/MaverickUpgrades)

after executing the last step which is :
```
gksu "sh /media/cdrom/cdromupgrade"
```

I am getting error 
```
sh: Can't open /media/cdrom/cdromupgrade
```
Are you running that command literally?

You'll probably have to change the directory to whatever it is on your system.  Type ```
ls -l /media
``` to see what the CD might be mounted as on your system.

---

### Post by techbrainless on 2011-07-04
Thanks Ranko Kohime for your reply, 

Actually /media/cdrom exists but the file "cdromupgrade" does not exist .

---

### Post by Ranko Kohime on 2011-07-04
> **techbrainless said:**
> Thanks Ranko Kohime for your reply, 

Actually /media/cdrom exists but the file "cdromupgrade" does not exist .
Hmm...  Perhaps this then?  gksu is generally for graphical applications, and I don't know how it reacts with command-line programs like sh...  So use sudo instead.

And also, shorten the path to just the cdrom, which does exist, like so.
```
sudo sh /media/cdrom
```

EDIT: Wait, that won't do anything but give you a root shell.  I just read the update page, are you mounting the ISO image from your hard drive?  If so, make sure it mounted and you can see the contents.  It should show up like a regular CD-ROM, and be browsable, etc.  Then the original command should work.

---

### Post by techbrainless on 2011-07-04
Thanks Ranko Kohime for your reply, 

> sudo sh /media/cdrom
I have executed the command but nothing happened , 

by the way it mounted and I can see the contents.  It shows up like a regular CD-ROM, and it is browsable, etc.

---

### Post by Ranko Kohime on 2011-07-04
I realized it wouldn't do much after I posted that.

'cdromupgrade' is a program the instructions are expecting will be on the ISO image/CDROM, and it's not there, so...

You either have the wrong ISO/CDROM, or a bad image.

---

