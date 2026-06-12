---
title: "(initramfs) Unable to find a medium containing a live file system"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by goathunter on 2010-08-17
Hello I have just bought a new ASUS N82JQ laptop and am trying to install Ubuntu 10.04 on it. Am trying to set it up as a dual boot system with windows 7 and ubuntu and the backup windows partition.
 

It is currently running windows 7.

System specs

CPU i7 - 720QM
VGA nVIDIA GeFORCE GT 335M VRAM:1GB
2GB memory

When I try to install from flash drive it goes to ubuntu loading screen and comes up with this

> BusyBox v1.13.3 (Ubuntu 1:1.13.3-ubuntu11) built in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) Unable to find a medium containing a live file system

Tried a different usb port, loaded up fine, but then it crashed. Rebooted and then back to the same error message.

Any help with this would be much appreciated
cheers

---

### Post by Herman on 2010-08-17
So, just to clarify, is your question about how to make a bootable Ubuntu Startup USB?
Does your Ubuntu USB work in other computers? 

Have you tried using the Ubuntu Startup Disk Creator, ('System', 'Administration', 'Startup Disk Creator') for making your 'persistence' installation your USB drive?
Or are you trying to make your Ubuntu install CD in your USB some other way?
.

---

### Post by goathunter on 2010-08-17
Hello.
Yes the flash drive was made using ubuntu startupdisc creator.

I know how to make a usb key, it was my usual method of install on my old laptop (i always did fresh install, not upgrades).

I am just trying to work out why my bootable flash drive won't install on my new laptop.

Will try to get hold of a blank cd-r and see if I can install that way. Also will try to make a new bootable flash drive but use unetbootin instead.

cheers

---

### Post by b_koepke on 2010-08-30
Hey, 

I was thinking of getting this laptop as well. Were you able to get ubuntu to boot? Also, is the backlight hardware controlled, or are you basically boned unless someone develops an application for it?

Thanks.

---

### Post by juliobahar on 2010-10-19
so what is the solution for this error that I seem to have with my ubuntu 10.10 64-bit Live USB


```
(initramfs) Unable to find a medium containing a live file system
```

---

### Post by C.S.Cameron on 2010-10-19
I think I have seen this message with a bad download, check the isos MD5SUM.

---

### Post by juliobahar on 2010-10-21
> **C.S.Cameron said:**
> I think I have seen this message with a bad download, check the isos MD5SUM.
Yes you are absolutely right, I had a bad iso download of ubuntu.

Redownloading the iso and recreating the Live USB solved the problem.

Thanks

---

### Post by mspacek on 2010-11-22
For me, the problem was that I had my USB key plugged into one of the two USB 3.0 ports on my Thinkpad W510. Plugging it into one of the normal USB 2.0 ports fixed this. I guess USB 3 driver support in the livecd bootloader isn't quite there yet. This was in 64-bit Maverick.

---

### Post by ds9 on 2011-03-16
> **mspacek said:**
> For me, the problem was that I had my USB key plugged into one of the two USB 3.0 ports on my Thinkpad W510. Plugging it into one of the normal USB 2.0 ports fixed this. I guess USB 3 driver support in the livecd bootloader isn't quite there yet. This was in 64-bit Maverick.

Same goes for me on an HP Elitebook 8540w and Pinguy OS 11.04 Pre-Alpha  (64) bit based on Ubuntu. 

It looks like a general USB 3 issue : 
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/565047](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/565047)  (HP Envy 15 user)
[http://ubuntuforums.org/archive/index.php/t-1332782.html](http://ubuntuforums.org/archive/index.php/t-1332782.html) (Asus 1018p user)

I tried to search for an option for grub to get boot on USB working, but so far no success ..

---

### Post by SirSlipALot on 2011-06-26
USB3 was the problem for me.

Laptop: Dell Vostro 3550
Ubuntu 10.04.2 amd64 installed on a usb stick from ubuntu

Thanks!
:popcorn:

---

### Post by Kaho on 2011-07-13
Hehe, same here with the USB3 issue :p (I could have searched for a loong time without this thread)

Ubuntu 11.04 (64) on a Dell Vostro 3350

Thanks all!

---

### Post by Agent008 on 2011-07-14
USB3 was a problem for me too, until I read this thread :)
Thanks a lot guys, you saved my life.:)
I am using HP Elitebook 8460p

---

### Post by robeano on 2011-08-15
> **mspacek said:**
> For me, the problem was that I had my USB key plugged into one of the two USB 3.0 ports on my Thinkpad W510. Plugging it into one of the normal USB 2.0 ports fixed this. I guess USB 3 driver support in the livecd bootloader isn't quite there yet. This was in 64-bit Maverick.

The same was true for my Thinkpad W520.  This error:

> BusyBox v1.13.3 (Ubuntu 1:1.13.3-ubuntu11) built in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) Unable to find a medium containing a live file system

went away when I moved my USB thumb drive from to using the USB 2.0 port on the back of the machine.  I also verified that the md5sum was correct.  I had trouble finding the MD5SUMS file.  Go to [http://releases.ubuntu.com/](http://releases.ubuntu.com/) then click into the version you want to check (in my case 11.04), then you can find the correct MD5SUMS file as a link below the Select an Image text i.e. scroll down! :)

---

### Post by spif17 on 2011-09-16
USB3 was a problem for me too, I wanted to install Windows...
Thanks a lot, you save my day ;)
I am using a desktop with an Asus P8H67 motherboard.

---

### Post by TweFoju on 2011-09-25
USB 3.0 for me too

Confirmed

not ISO

i did the same thing, lol i downloaded the ISO 3x, damn wasting time =(

---

### Post by aimwin on 2011-11-16
Acer Aspire 5755G has the same problems.

But some times,
with the USB on the right hand side of the notebook,
now suspect it to be USB 3,
it worked fine many times,
and 
many times if failed.
Once it failed, I recreated new live USB stick,
and it may work for 1 or more time.

Then it failed with the same message of
(initramfs) Unable to find a medium containing a live file system.

[COLOR="Red"][B][I][U][SIZE="3"]
Where is the USB 2,[/SIZE][/U][/I][/B][/COLOR]
I have check the manual,
 **_download from the manufacturer website._**
and found that on the right hand side there are 2 USB ports, 
one with blue (for USB 2 /OR USB 3)
and 
ONE WITH BLACK PORT (for USB 2 only)

So that is why it sometime failed and sometimes not,
so if fail when I insert it into the USB 2/USB 3 PORT, the BLUE port.
and it works because I sert it into THE USB 2 PORT only.

I went into details above since it took me long while to figure it out,
even after I read above posts, so to make the posts more usefull,
especially for the newbies.
================================s

for other notebooks try to plug into other existing ports,
you may be lucky to get one that works as USB 2.

I change to use the "guess USB 2 port" and it works every time.

Thank you for the answers and feed back above.

---

### Post by Tuexnovia on 2013-02-25
I got an Aspire one D257 13DQrr Cpu N455  I wasn't able to install Xubuntu from my USB regarding this problem, I tried with several USB and nothing there's no way.

Well is because my netbook I guess, I had to use wubi and install lubuntu instead. So sad....

---

### Post by oldos2er on 2013-02-25
Old thread closed.

---

