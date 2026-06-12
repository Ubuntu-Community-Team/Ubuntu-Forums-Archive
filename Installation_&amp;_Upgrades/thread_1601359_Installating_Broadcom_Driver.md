---
title: "Installating Broadcom Driver"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by The True Mop on 2010-10-20
Hi,

I'm new to this forum, and as you'll probably guess, new to Ubuntu. I've never used the OS until a few days ago, and I've never been a particularly code-minded individual. As such, I have found myself at a complete and utter loss trying to install a driver so I can use my Broadcom wireless card on here.

I've tried following the readme that came with the code, but it's all in jargon and I simply haven't had enough experience to work my way around it. Every time I type any code into terminal, nothing happens, it simply drops a line. This isn't the case when I use sudo, but I have no idea what command I'd use to compile code in any language, let alone something as alien to me as sudo.

If anyone could give me a really basic step-by-step guide on how to install this sod, I'd be very grateful, as will my laptop when I can happily remove my college's ethernet cable.

Many thanks,
Alex

---

### Post by halj32 on 2010-10-20
if you cant get onto the internet you can use the cd, the drivers you need are in /pool/
you need to install, dkms, fakeroot, patch and then the bcmwl-kernel-source package

if you are online do an update
sudo apt-get update
sudo apt-get upgrade
 then install the above

---

### Post by The True Mop on 2010-10-20
> **halj32 said:**
> if you cant get onto the internet you can use the cd, the drivers you need are in /pool/
you need to install, dkms, fakeroot, patch and then the bcmwl-kernel-source package

if you are online do an update
sudo apt-get update
sudo apt-get upgrade
 then install the above
I don't actually know how to install anything, the whole operating system is a little bit technical...

---

### Post by lkraemer on 2010-10-20
WELCOME to Linux & Ubuntu.  You will love it after you have a bit of time
under your belt.  You have to "get over" the hold Windows has on you.......

There are several ways you can get the Broadcom Drivers installed easily.

Here is one method, that has two options.  I'd suggest the standard B43
Drivers that are included with Ubuntu.  You could use ndiswrapper if
nothing else works.

[http://ubuntuforums.org/showthread.php?t=1470146&highlight=Howto%3A+Broadcom](http://ubuntuforums.org/showthread.php?t=1470146&highlight=Howto%3A+Broadcom)


Your next question will be:
"What software will replace my Windows XXXXXXProgram?"

[http://ubuntuforums.org/showthread.php?t=1597400](http://ubuntuforums.org/showthread.php?t=1597400)
Posting #5 (along with the others......)

Just figure out the MUST HAVE Windows software, and then search for a 
replacement, or how to get that software running in Linux........
ZIT, ZOT!  You don't really need Windows.........and if you do
there is VirtualBox......

lk

---

### Post by TBABill on 2010-10-20
Which version of Ubuntu are you using and what Broadcom device do you have? You can type ```
lspci
``` into a terminal and in the list is a line that will give you the specific model number of yours. You can just copy/paste that info here. (that's LSPCI but in lower case)
 
My device is a Broadcom BCM4312 and I enable it by plugging into my router, downloading updates to the system, then enabling it by clicking the "proprietary drivers are available" icon that comes up in the upper panel on the screen. Or by clicking SYSTEM>>ADMINISTRATION>>HARDWARE and having it scan for devices that have a driver available for download. I use the STA driver on Ubuntu 10.04 LTS 64 bit and it works perfectly.
 
Hopefully this helps and if you need more, please post your questions and the info on your wireless device.

---

