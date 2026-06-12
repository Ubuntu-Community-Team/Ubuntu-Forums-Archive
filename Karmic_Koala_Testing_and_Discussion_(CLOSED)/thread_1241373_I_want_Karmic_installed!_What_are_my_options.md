---
title: "I want Karmic installed! What are my options?"
date: 2009-08-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kestal on 2009-08-15
Here's the thing, I am on the Dell 14z Laptop. No DVD drive. Karmic, at least for me, cannot be booted off of a USB. 

I've done it with other distributions and even versions of Ubuntu (9.04 was the latest) and it was fine, however all 9.10 does is send me to a black screen with just a blinking _, or sticks me into a tty1 screen.

I do not want to place Ubuntu "within" my Windows partition. Is there an option on Wubi where I could somehow just create a normal/dedicated partition?

Is there another option? like using partition software to pre-create the partition and then somehow install Ubuntu from a windows environment with a target of that partition? etc etc?

Thanks.

---

### Post by overdrank on 2009-08-15
Moved to Karmic Koala Testing and Discussion

---

### Post by wayne_cat on 2009-08-15
Maybe via LVPM

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

---

### Post by kestal on 2009-08-15
> **wayne_cat said:**
> Maybe via LVPM

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

Looking at it, from what I can tell. I have to create the Wubi installation first through Windows, and then use Lubi? The documentation seems to stretch it only as far as 8.04, but I assume there shouldn't be any conflicts with this for 9.10?

---

### Post by nmaster on 2009-08-15
you could try testing karmic through VirtualBox.  that seems the simplest solution.

---

### Post by ronacc on 2009-08-15
if you already have 9.04 installed you could edit your /etc/apt/sources.list to change all instances of jaunty to karmic and then run 
```
 sudo apt-get update 
```
 
and then 
```
 sudo apt-get dist-upgrade
```

warning though if you can boot 9.04 from a usb stick but not karmic, an install may send you to a black screen also.

---

### Post by keypox on 2009-08-15
> **kestal said:**
> Here's the thing, I am on the Dell 14z Laptop. No DVD drive. Karmic, at least for me, cannot be booted off of a USB. 

I've done it with other distributions and even versions of Ubuntu (9.04 was the latest) and it was fine, however all 9.10 does is send me to a black screen with just a blinking _, or sticks me into a tty1 screen.

I do not want to place Ubuntu "within" my Windows partition. Is there an option on Wubi where I could somehow just create a normal/dedicated partition?

Is there another option? like using partition software to pre-create the partition and then somehow install Ubuntu from a windows environment with a target of that partition? etc etc?

Thanks.

I had an issue creating a usb startup. Formatted and retried and it worked. 

Also that is a great idea for wubi.  I would love to see that feature. Might not be possible in on same drive runnning windows though.

---

### Post by kestal on 2009-08-15
I have tried Virtual box, but thats not what I am asking. I want it on a dedicated partition. I can do Jaunty in a usb but not Karmic (Tried nightly build, and official, among a few other attempts, all failed with a tty1 screen). I am currently using Windows 7.

Thanks for the info, even if upgrading.. thats somewhat frustrating.

---

### Post by Starks on 2009-08-16
A netboot solution might work if you are interested in getting your hands dirty.

---

### Post by kestal on 2009-08-16
I tested it on virtualbox and it did NOT force tty1. I wonder if anyone else can verify the usb part? I cant even get to the installation screen or even to boot into the live desktop, as thats when it gives errors and does that.

I will try wubi/lubi and see what I can do.

---

### Post by bennachie on 2009-08-16
How did you make the USB stick from the ISO? Unetbootin or USB Disk Creator?

---

### Post by Eclipse. on 2009-08-16
Unetbootin is highly recommended.I use it all the time for booting USB off my netbook.

---

### Post by taavikko on 2009-08-16
> **ronacc said:**
> if you already have 9.04 installed you could edit your /etc/apt/sources.list to change all instances of jaunty to karmic and then run 
```
 sudo apt-get update 
```
 
and then 
```
 sudo apt-get dist-upgrade
```

warning though if you can boot 9.04 from a usb stick but not karmic, an install may send you to a black screen also.

why do it the hardway when you can just use
```
update-manager -d
```
If software-sources is set to use "normal" distribution releases

---

### Post by ronacc on 2009-08-16
> **taavikko said:**
> why do it the hardway when you can just use
```
update-manager -d
```
If software-sources is set to use "normal" distribution releases

both ways should work ,I prefer the apt-get way because it finds things to upgrade that update-manager misses .

---

### Post by NCLI on 2009-08-16
> **kestal said:**
> I tested it on virtualbox and it did NOT force tty1.

I will try wubi/lubi and see what I can do.
Of course it didn't. Virtualbox only shows the OS' you install virtual hardware, so you can't use it to determine whether Karmic has problems with some of your hardware(at this very early stage), which it sounds like it does to me.

I wouldn't recommend an install.

---

### Post by kestal on 2009-08-16
> **bennachie said:**
> How did you make the USB stick from the ISO? Unetbootin or USB Disk Creator?

unetbootin. I tested again with Jaunty and it worked fine, then did Karmic (downloaded a new iso) and I got a tty1 login screen after I see the graphical load up bar (but both of which load up fine in Virtualbox)

> **NCLI said:**
> Of course it didn't. Virtualbox only shows the OS' you install virtual hardware, so you can't use it to determine whether Karmic has problems with some of your hardware(at this very early stage), which it sounds like it does to me.

I wouldn't recommend an install.

Your prediction seems correct. I tried to install from my USB onto my desktop and it worked without problem. I guess I will wait for the beta's to try again.

---

