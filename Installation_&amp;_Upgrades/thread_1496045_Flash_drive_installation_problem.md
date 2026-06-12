---
title: "Flash drive installation problem"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by MyiEye on 2010-05-28
So, I had been that it was possible to simply boot up with a live CD and then install Ubuntu onto a flash drive and have a true installation on your Flash drive as easy as pie.

So, I tried it and it seemed to look quite promising. However, when the flash drive is not in, I am given a Grub error 21 and can't boot into either Windows 7 or Ubuntu (9.04 in this case). I was hoping that Grub would be entirely on the flash drive, but I'm very new to all this, so maybe what I'm attempting is entirely impossible. Either way, strangely enough I didn't get the chance to try using the flash drive on any other computers to see if it actually would boot as I left for the weekend and figured that I should leave my flash drive because it was my friend's laptop.

So, is it possible to get a complete/true installation of Ubuntu on a flash drive or portable hard drive? Can I get Grub to stop getting in the way so Windows can just boot happily?

Thanks.

EDIT: So, after digging around a bit more I feel minorly more educated meaning that I now see what happened. The bootloader Grub was definitely installed to the internal hard drive rather than to my flash drive. So, to rephrase my questions I would ask: How do I get Grub off of the internal hard drive? Once that is done how can I get Grub onto my flash drive?

Thanks again

---

### Post by oldfred on 2010-05-28
Welcome to the forums.

What boot loader do you want in your internal? Windows?

I would boot into your flash drive and install grub to the flash drive MBR first. 
You will have to know if you flash drive is sdb or something else, then you can just run this and the last screen choose sdb.
sudo dpkg-reconfigure grub-pc

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

From Ubuntu you can install a generic windows boot loader:
Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

---

### Post by MyiEye on 2010-05-28
Great stuff, shouldn't be much of a hassle to set things straight, thanks a lot. And, yes, I'm looking for a Windows 7 bootloader, so that tutorial should do just fine.

One very related question. This will fix everything up exactly the way I want it, but would there be a way to install Grub in the proper place (On my flash drive) in the first place without unplugging my internal hard drive?

---

### Post by oldfred on 2010-05-28
During install on the last partition screen when it says ready to install, there is an advanced button that lets you choose where to install grub.

Install karmic Screens shown with advanced button
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

---

### Post by MyiEye on 2010-05-31
It looks like I most likely misinterpreted the problem. I had a live CD to test the reconfiguration of grub to my flash drive and that worked just fine, but when I actually booted into ubuntu from my flash drive same command gave me a reply of "grub-pc not installed". I thought the purpose behind that command WAS to install it....I don't know.

You would probably know what went wrong so maybe I should just walk you through exactly what I did.

So I booted up with a live CD and installed Ubuntu right to my flash drive, considering I didn't know about that "advanced" option, I guess I installed the bootloader to whatever the default is. Now if my flash drive is not in. Grub throws up an error 21 and won't do anything.

Anything wise words to offer to an uneducated novice such as I?

---

### Post by oldfred on 2010-05-31
While this discusses external drives your flash is an external drive.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

### Post by MyiEye on 2010-06-01
I think that somehow the installation was. Bit messed up because not much was working, but I managed to use Lilo on a live CD to restore the windows bootloader and then I reinstalled ubuntu, putting the bootloader in the right place and all is well. Thanks for the help, all is well :)

---

