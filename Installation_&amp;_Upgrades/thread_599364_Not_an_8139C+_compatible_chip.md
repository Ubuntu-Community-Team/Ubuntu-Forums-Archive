---
title: "Not an 8139C+ compatible chip"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by lenB on 2007-11-01
Hi..

I just installed Gutsy without problems.. However, when I boot, the screen turns black, with a flashing cursor and after a while the following message is displayed:

This is not a 8139C+ compatible chip. Use the 8139too driver instead.

Where do I find this driver and how do I enable it?

---

### Post by Pumalite on 2007-11-01
Looks like Realtek is the place you should be looking at:
[http://en.opensuse.org/SDB:Realtek_8139_Driver_Problem](http://en.opensuse.org/SDB:Realtek_8139_Driver_Problem)

---

### Post by lenB on 2007-11-04
Hi there.. I follow the steps in the guide..first run
 ```
hwinfo --netcard
```

That gives: 
```
Driver Info #0:
    Driver Status: 8139too is active
    Driver Activation Cmd: "modprobe 8139too"
  Driver Info #1:
    Driver Status: 8139cp is active
    Driver Activation Cmd: "modprobe 8139cp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

Now, I run
```
rmmod 8139cp
```

Now it looks like this: 

```
Driver Info #0:
    Driver Status: 8139too is active
    Driver Activation Cmd: "modprobe 8139too"
  Driver Info #1:
    Driver Status: 8139cp is not active
    Driver Activation Cmd: "modprobe 8139cp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #17 (PCI bridge)

```

Now, I run
```
modprobe 8139too
```

But this changes nothing!!:(

I think it has something to do with the fact that in the guide they change #0 to 8139too and I am trying to change #1. Maybe the modprobe command should look little different.

Thanx very much for the help!!

---

### Post by Pumalite on 2007-11-04
Have you rebooted?
Why don't you run:

modprobe 8139cp

And then reboot. Let's see what happens.

---

### Post by lenB on 2007-11-04
Yes I rebooted and got the same message.

Don't have my laptop with me at the moment, will give
```
modprobe 8139cp
``` a try, however it doesn't really make sense to me since the error message instructs to use the 8139too driver instead

---

### Post by Pumalite on 2007-11-04
You might be right. Here is a collection of links that could help you anyway:

[http://ubuntuforums.org/showthread.php?t=569280](http://ubuntuforums.org/showthread.php?t=569280)
[http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound)
[http://ubuntuforums.org/showthread.p...ght=sound+will](http://ubuntuforums.org/showthread.p...ght=sound+will)
[http://ubuntuforums.org/showpost.php?p=3588321&postcount=5](http://ubuntuforums.org/showpost.php?p=3588321&postcount=5)
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide)

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[http://www.alsa-project.org/main/index.php/MainPage](http://www.alsa-project.org/main/index.php/MainPage)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469)

---

### Post by lenB on 2007-11-06
Thanx.. Will have a look at it.

```
modprobe 8139cp
```
takes me right back where I started, also when I reboot, the 8139cp is automatically activated again.

Thank you very much with your help on this.

---

