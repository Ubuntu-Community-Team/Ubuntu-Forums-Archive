---
title: "mount second drive to /home ???"
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by adds2one on 2006-08-24
I have just added a second hard drive to my system. I currently have it mounted and fully operational under /media/hdb1

What I was hoping to do is to mount this drive to /home to make my /home partition larger but when I do this I am unable to get into Gnome.

here is my current fstab:

```
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /media/hdb1     ext3    defaults        0       0

```

I thought that if I instead mounted /dev/hdb1 to /home that all should be good and my /home made bigger. This doesn't seem to work. 

Is this possible?

---

### Post by meng on 2006-08-24
Did you remove (comment out) the line with /dev/hda3 when you did this? You might have trouble mounting 2 partitions to /home simultaneously!

---

### Post by adds2one on 2006-08-24
No I didn't. I had the impression that it was possible to mount a second drive to the same mount point. I thought for sure that I had read this somewhere.

Can anyone definitely confirm or dismiss this?

---

### Post by meng on 2006-08-24
It doesn't make sense that you should be able to mount two devices to the same mountpoint, and even if you did, how would you then copy the contents of one to the other?

Try this instead:
(assuming your hdb1 is empty and everything is mounted as in your posted fstab)
cp -r /home /media/hdb1

then change your fstab, comment out /dev/hda3, change mountpoint of /dev/hdb1 to /home

---

### Post by adds2one on 2006-08-24
I guess that is what I will do. Thanks.

---

### Post by aysiu on 2006-08-24
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html) will walk you through the process.

---

### Post by adds2one on 2006-08-24
aysiu, I do already have a /home partition that I created when I originally installed Ubuntu so your link doesn't apply.

I copied the contents of my original /home to my new /dev/hdb1 drive and then commented out the original /home partition and changed fstab to mount my new hard drive to /home.

but when I reboot I get an error. I'll have to write it all down and post it. 

back in a bit.

---

### Post by meng on 2006-08-25
Sorry to hear things went pear-shaped. I hope you had some sort of livecd/rescue disk to restore your fstab or otherwise tinker with things.

---

### Post by adds2one on 2006-08-25
No, things aren't that bad. I can still change my fstab and get everything working as they were originaly, /dev/hda3 mounted as /home and /dev/hdb1 mounted as /media/hdb1

I guess I will have to stick with this.

---

