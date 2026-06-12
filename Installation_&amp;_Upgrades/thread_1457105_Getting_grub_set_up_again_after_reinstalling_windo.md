---
title: "Getting grub set up again after reinstalling windows XP"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by muntasir_120 on 2010-04-18
I recently had to reinstall Windows XP and as usual it destroyed my grub setup. I have done this before, so I simply booted from a live CD and typed this in the terminal:

```
sudo grub

> root (hd0,2)
> setup(hd0)
> quit
```

Now, the problem with it this time is that in the past in these situations I had only Ubuntu Feisty and Windows XP installed on my machine. But I have installed Ubuntu 9.04 on a separate partition (retaining the old 7.04 installation separately) since I last had to reinstall XP. Doing the above procedure restores my grub sttings to my pre-9.04 installation (i.e. I only get Ubuntu 7.04 and Windows XP in the grub menu).

I have tried searching this forum and elsewhere on the web, but can't find how to restore the latest grub settings.

Can anyone help?

---

### Post by tom4everitt on 2010-04-18
Isn't it simply that (hd0,2) is the partition that you have feisty on? (hd0,2) is the third partition on the first hard drive. 

Most likely your jaunty installation is on partition (hd0,3) or (hd0,4) or something like that. If it for instance is on (hd0,4), you should instead do:

```

sudo grub

> root (hd0,4)
> setup(hd0)
> quit

```

---

### Post by muntasir_120 on 2010-04-18
Thanks for the answer. Yes, (hd0,2) is indeed the partition where I installed Feisty, and that is why grub reverts to that setting. I guess what I should have been asking is how to figure out which partition ((hd0,3), (hd0,4), hd0,5), etc.) contains Jaunty. Any ideas how I might do that?

---

### Post by roynoblin on 2010-04-18
I wish I could help but I am new to this. I have searched to find a answer to my problem and you seem to know about GRUB and having more than 1 OS on the same drive so I am hopeful you can help me.
 

 I have three partitions on this 1T HDD. I Installed XP Pro on it and then I installed UBUNTU. I set it 250 G partition for XP. 250G for UBUNTU and the remaining 500G for data. As best I can tell I have 3 partitions on this HDD.
 

 Everything has been working great until I started XP and did a update. It installed several security updates and requested I restart this PC.
 

 Since the restart I can still use UBUNTU and I can access the data in the data partition but XP gets to the XP window with the little blue dots running in the bar. The screen then goes black as usual but instead of XP starting it does a restart.
 

 My thoughts are the bootlog is messed up and by doing 'E' I see what looks like you have posted and I assume is the boot log.
 

 The xp line I arrow down to has (on /dev/SDA1)
 does this mean it should looking in partition 2?
 

 If you can help or point me in the right direction to get help I would really appreciate it.
 I sure you will need additional information as to my set up but I have no idea what or where to get it.
 Thank you

---

### Post by tom4everitt on 2010-04-18
> **muntasir_120 said:**
> Thanks for the answer. Yes, (hd0,2) is indeed the partition where I installed Feisty, and that is why grub reverts to that setting. I guess what I should have been asking is how to figure out which partition ((hd0,3), (hd0,4), hd0,5), etc.) contains Jaunty. Any ideas how I might do that?

Yes. Run

sudo fdisk -l

to get a list of your partitions. Given that you can figure out which partition is jaunty in that list, you can convert from sdaX format (hdX,Y) the following way.

sda1 = (hd0,0)
sda2 = (hd0,1)
sda3 = (hd0,2)
sda4 = (hd0,3)

etc. etc. Also

sdb1 = (hd1,0), etc. 

(Beware though, when you upgrade to grub2, which comes with karmic, sda1 will be (hd0,1). Pretty illogical, but i'm sure there's a reason.)

---

### Post by tom4everitt on 2010-04-18
> **roynoblin said:**
> I wish I could help but I am new to this. I have searched to find a answer to my problem and you seem to know about GRUB and having more than 1 OS on the same drive so I am hopeful you can help me.
 

 I have three partitions on this 1T HDD. I Installed XP Pro on it and then I installed UBUNTU. I set it 250 G partition for XP. 250G for UBUNTU and the remaining 500G for data. As best I can tell I have 3 partitions on this HDD.
 

 Everything has been working great until I started XP and did a update. It installed several security updates and requested I restart this PC.
 

 Since the restart I can still use UBUNTU and I can access the data in the data partition but XP gets to the XP window with the little blue dots running in the bar. The screen then goes black as usual but instead of XP starting it does a restart.
 

 My thoughts are the bootlog is messed up and by doing 'E' I see what looks like you have posted and I assume is the boot log.
 

 The xp line I arrow down to has (on /dev/SDA1)
 does this mean it should looking in partition 2?
 

 If you can help or point me in the right direction to get help I would really appreciate it.
 I sure you will need additional information as to my set up but I have no idea what or where to get it.
 Thank you

This is actually a rather different problem. You should start a new thread for it (put a link in this thread so I can find it). 

I don't think there is a problem with a grub entry. Rather, it seems like your xp upgrade broke your xp in some way. I'm not sure how to fix this.

---

### Post by oldfred on 2010-04-18
Anytime it gets beyond simple we need to document the system:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by muntasir_120 on 2010-04-18
Thanks for the help. I got my old setup back again.

---

### Post by roynoblin on 2010-04-18
tom i did start a new thread
[http://ubuntuforums.org/showthread.php?t=1457206](http://ubuntuforums.org/showthread.php?t=1457206)
thanks

---

### Post by jemmah on 2010-04-18
get the jaunty alternate install cd and go 'rescue damaged system' from the menu :confused:from there you're on your own but THIS MAY GET RID OF YOUR OTHER INSTALLATION how should i know I'm a newbe:wink:

---

