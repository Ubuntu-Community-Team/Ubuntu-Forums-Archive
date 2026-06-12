---
title: "Installing ubuntu onto a USB stick"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by epud on 2010-10-28
Hello

I wish to install a fully working Ubuntu system on my 16GB USB disk so that when I boot from my USB stick I get directly into Ubuntu. I do not want to be prompted with the option of "Try Ubuntu" or "Install Ubuntu". How do I do this?

Thanks

---

### Post by ndefontenay on 2010-10-28
Hi.

I don't think this is easily possible. 

I suppose you can try installing ubuntu on your usb key. That means that when you put your CD in your computer, you will have a choice of where to install ubuntu. At that point you can choose your USB key for installation.

BUT! When you remove it what will happen? Where will grub be installed? Can you plug it on another computer?

I have a few serious doubts.

---

### Post by wojox on 2010-10-28
Are you doing this from Windows or [Linux]("http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar") ?

---

### Post by epud on 2010-10-28
Yes, I do not want to screw up GRUB. I need some sort of Casper partition and a partition for my files (/home directory). Ubuntu has such a nice way of making a USB startup disk.

Is there no program which will let me install ubuntu on a USB so that I can boot it from any computer and have Ubuntu running?

---

### Post by epud on 2010-10-28
> **wojox said:**
> Are you doing this from Windows or [Linux]("http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar") ?

Either works for me. I have dual boot.

---

### Post by amedac on 2010-10-28
Try to follow this tutorial, it is for BT4, but it should work for ubuntu: [URL="http://www.infosecramblings.com/backtrack/backtrack-4-usbpersistent-changesnessus/"]

---

### Post by arubislander on 2010-10-28
What I usually do is to create a Live USB with persistence in the normal way. Then I do the following:
1. remove the ubiquity package.
2. create a new user
3. disable auto login.

I am left with a system that boots to the login screen and allows me to login with my newly created user.

HTH

---

### Post by epud on 2010-10-28
> **arubislander said:**
> 
I am left with a system that boots to the login screen and allows me to login with my newly created user.

HTH

Sounds good! I now have a persistence disk of 4GB. How would I utilize, the rest of the USB stick. It is 16 GB in size.

---

### Post by ghostborg on 2010-10-28
Another thread with info
[http://ubuntuforums.org/showthread.php?p=9807003#post9807003]("http://ubuntuforums.org/showthread.php?p=9807003#post9807003")

---

### Post by snowpine on 2010-10-28
> **ndefontenay said:**
> I suppose you can try installing ubuntu on your usb key. That means that when you put your CD in your computer, you will have a choice of where to install ubuntu. At that point you can choose your USB key for installation.

BUT! When you remove it what will happen? Where will grub be installed? Can you plug it on another computer?

GRUB is installed to /dev/sda by default. However, if you click the Advanced button on the final installer screen, you can install GRUB to your USB device (for example maybe /dev/sdb) instead. You could also just unplug your internal HDD during the install (so the USB is the only disk connected).

An Ubuntu USB install should boot fine on other computers (why wouldn't it?) unless of course you do something silly like try the 64-bit version on a 32-bit machine.

I have not tested this yet with 10.10 but it worked OK with past releases.

---

### Post by epud on 2010-10-28
I managed to install Ubuntu onto my USB stick by disconnecting the harddrive and then using the install CD.

---

### Post by Thirusan on 2012-09-01
Check out my video it's easy to understand and much better it helps you refer back to this site if you want for more help:

I made two different videos one is easy and can only be done on certain OS such as Ubuntu 
Linux mint and some other ones.

But the second video explains how to install any Linux operating system on a usb.

First video:
[http://www.youtube.com/watch?v=oOsC5_-ph_M&list=UUKPnZFyxZ0uKhaJ6774YjiA&index=2&feature=plcp](http://www.youtube.com/watch?v=oOsC5_-ph_M&list=UUKPnZFyxZ0uKhaJ6774YjiA&index=2&feature=plcp)

Second video:
[http://www.youtube.com/watch?v=dWrmi4c6lFU&feature=player_profilepage](http://www.youtube.com/watch?v=dWrmi4c6lFU&feature=player_profilepage)

---

