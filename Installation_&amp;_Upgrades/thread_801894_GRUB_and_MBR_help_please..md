---
title: "GRUB and MBR help please."
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by FattMatt on 2008-05-21
Hi,

I have been using Ubuntu 7.10 for the last few months and I really like. However, I want to remove it from the computer I am using it on now and install it on another. But I am having some serious troubles with this one, here's where they start...

I have Ubuntu 7.10 installed on a USB External hard disk, and Windows XP on my internal hard disk. I believe that when I installed Ubuntu originally, I chose to install the GRUB on my internal hard disk, but Ubuntu on the external. So now, if I do not have the external powered on when booting, I get GRUB Error 21 message and cannot boot Windows at all. If I do have the external powered on, my GRUB boots properly and I am given options on which operating system I would like to boot. I need to somehow figure out how to remove GRUB from my internal disk and place it on the external (where Ubuntu is).

This is my device map if it helps.
(hd0)	/dev/sda
(hd1)	/dev/sdb

I would really appreciate all the help on this one,

Thanks a lot,
Fatt Matt

---

### Post by rraj.be on 2008-05-21
GRUB Error 15 indicates there is no hard drive..

The best solution would be boot from a live ubuntu cd and reinstall grub to some other location.

The next way is to boot into ubutu and edit the grub.

this too will help you.

---

### Post by confused57 on 2008-05-21
> **FattMatt said:**
> Hi,

I have been using Ubuntu 7.10 for the last few months and I really like. However, I want to remove it from the computer I am using it on now and install it on another. But I am having some serious troubles with this one, here's where they start...

I have Ubuntu 7.10 installed on a USB External hard disk, and Windows XP on my internal hard disk. I believe that when I installed Ubuntu originally, I chose to install the GRUB on my internal hard disk, but Ubuntu on the external. So now, if I do not have the external powered on when booting, I get GRUB Error 21 message and cannot boot Windows at all. If I do have the external powered on, my GRUB boots properly and I am given options on which operating system I would like to boot. I need to somehow figure out how to remove GRUB from my internal disk and place it on the external (where Ubuntu is).

This is my device map if it helps.
(hd0)	/dev/sda
(hd1)	/dev/sdb

I would really appreciate all the help on this one,

Thanks a lot,
Fatt Matt

First you need to reinstall Window's IPL(Initial Program Loader) to the internal hard drive's mbr...you can do this with a Windows XP install cd(not a recovery disk), press "r", then FIXMBR.  You can also use Super Grub Disk, if you don't have a Windows install cd...

Then you can use the Ubuntu live cd to install grub's IPL to the external drive's mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
something like:
```
root (hd1,0)
setup (hd1)
```

You should get a grub boot menu when you boot first to your external drive...if you do, highlight the first Ubuntu entry, press "e", highlight the line with root, press "e" again, change root from (hd1,?) to (hd0,?), press "enter" then "b" to boot.  This change is temporary, but can be made permanent:
```
gksudo gedit /boot/grub/menu.lst
```
you'll also need to change the line with #groot to (hd0,?)

---

### Post by meierfra. on 2008-05-21
Deleted. Didn't  see the previous post.

---

### Post by Microsux on 2008-05-21
i had a similar problem,
butt it shoud work if you
remove linux and then boot the XP cd and go to the 
restore....option nr.2 (don't now the name in english i think it's something like "systemrestore")
press "fixmbr"
and press "fixboot" just to be safe...
that should do it, that will erase the GRUB boot loader...
you can uninstall linux before or after..
should work...

---

### Post by FattMatt on 2008-06-02
Thanks a lot Microsux. That worked marvelously. For some damn reason I was way too worried to try anything for the fear of my computer being down for more than a minute. Haha anyway, thats all for the replies!

Now I can install Ubuntu natively on a different system. Thumbs down to dual-boots!

<- Fatt Matt ->

---

### Post by meierfra. on 2008-06-02
```
 Thumbs down to dual-boots!
```

 Did you  try confused57  suggestion?

---

### Post by FattMatt on 2008-06-03
> **meierfra. said:**
> ```
 Thumbs down to dual-boots!
```

 Did you  try confused57  suggestion?

No I didn't. I think his suggestion would've properly fixed the issue, no doubt. However I was looking for the quickest fix, and since I re-installed Ubuntu on another PC, I didn't need to fix the GRUB issue here.

<-Fatt Matt->

---

### Post by meierfra. on 2008-06-03
> I think his suggestion would've properly fixed the issue, no doubt.  


Yes,  confused57 method will work for you.  Your situation is pretty  common (I see a case like this about once a week) In fact I  wrote a HowTo for this problem, which is  essentially the same as confused57 approach (click on "Dual" in my signature). I know about 10 people who  successfully used this method, and I have never seen it fail.


I still don't understand your "Thumbs down to dual-boots!". You could have solved your grub problem in less time than it takes to reinstall.

---

### Post by FattMatt on 2008-06-04
> **meierfra. said:**
> Yes,  confused57 method will work for you.  Your situation is pretty  common (I see a case like this about once a week) In fact I  wrote a HowTo for this problem, which is  essentially the same as confused57 approach (click on "Dual" in my signature). I know about 10 people who  successfully used this method, and I have never seen it fail.


I still don't understand your "Thumbs down to dual-boots!". You could have solved your grub problem in less time than it takes to reinstall.

I just read your 'Dual' post and it was exactly what I was looking for. If I found that earlier I would've been set, but to be honest I just got fed up with the boot problems and wanted to get rid of my dual-boot issues.

Thanks for all the help though folks!

<-Fatt Matt->

---

### Post by meierfra. on 2008-06-04
> Thanks for all the help though folks!

You are welcome. Just remember, Ubuntu sometimes takes a little bit of patience , but once you have it set up right, it will work perfectly.

---

