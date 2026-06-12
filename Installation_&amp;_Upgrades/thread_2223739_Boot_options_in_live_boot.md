---
title: "Boot options in live boot"
date: 2014-05-12
forum: Installation &amp; Upgrades
---

### Post by dougx1richards on 2014-05-12
Hi all,

I'm very interested in trying out ubuntu and ditching Windows. I think I've done everything correctly to boot from either a USB or a CD (I downloaded the iso file and burned it to a CD, I also created a bootable USB with pendrivelinux USB installer).  The problem is I get to the page where it asks me if I want to try or install, I click try and my screen goes black with just a white cursor line blinking in the upper left hand corner.

I read in another thread ([link]("http://ubuntuforums.org/showthread.php?t=1613132")) a suggestion to hit F6 before I choose try and click nomodeset. I was going to try that but I want to make sure that doesn't change any settings when I go back to Windows. Can anyone tell me if I click nomodeset is that just a temporary setting while I am running ubuntu from USB or CD?

Thank you

Windows8 64-bit
nvidia geforce 750Ti
i7-4770
Gigabyte G1 Sniper Z87

---

### Post by mörgæs on 2014-05-12
Hi, welcome to the fora.

Everything including nomodeset and other boot options in a live boot are temporary. Just go crazy playing with it.

---

### Post by sudodus on 2014-05-12
Yes the whole live session including boot options is only temporary. It will not touch the internal disk drive unless you really do that manually, for example start the installer.

-o-

- It might be a good idea to keep Windows and create a dual boot system, where you can select either Ubuntu or Windows at boot (in the grub menu). 

- There might be problems because of UEFI if Windows 8 is installed with UEFI.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

- There might also be problems with the graphics card, but I have seen a recent post here at the Ubuntu Forums, that describes how to install a proprietary driver that works with your card. See this link

[http://ubuntuforums.org/showthread.php?t=2214805&p=13021101#post13021101](http://ubuntuforums.org/showthread.php?t=2214805&p=13021101#post13021101)

---

### Post by dougx1richards on 2014-05-12
[SIZE=3]Thanks [COLOR=#000000]mörgæs [/COLOR]and[COLOR=#000000] [/COLOR][COLOR=#000000]sudodus[/COLOR]. I'm pretty excited to get in and play around with ubuntu, and learn all about it.[/SIZE]

---

### Post by mörgæs on 2014-05-12
Good. If this solves your problem please mark the thread so.

---

### Post by dougx1richards on 2014-05-12
Unfortunately this did not help. I went through the steps again to run ubuntu from a USB using LinuxLive USB Creator. I got one step further this time, a screen came up with ubuntu in large font, with four dots below it, but then my screen went blank. This time there was no cursor, it just went blank. I'll have to tackle it again tomorrow. I'm guessing it has something to do with my computer and not how I created the USB.

Any thoughts or suggestions?

Thanks again.

---

### Post by sudodus on 2014-05-13
You can also try the other boot options.

But a good tip is to install a proprietary nvidia driver according to post #3. I think you can do it in text mode, if the graphics does not work with any of the boot options. Add the boot option **text** manually.

See this link [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

