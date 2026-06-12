---
title: "Installing without Formatting"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by StealthSoul on 2007-04-19
I have lots of stuff on my Hard Drive, with XP on it atm.

Is it possible to Keep all my files and not format, I have 2 partitions, 1 with just music movies games etc and another with programs and windows XP. Can I install Ubuntu 7.04 without losing any files?

---

### Post by smartboyathome on 2007-04-19
You could, if you partitioned a new piece of drive...

---

### Post by StealthSoul on 2007-04-19
Ok, so I'd need a new partition? How big should I make this partition? I'm planning to use it just for ubuntu

Can I use Partition Magic to make a new partition?

Also - Is it easy to remove a partition if I decide not to use ubuntu?


If I install ubuntu on a different partition, will I be able to make it so when I boot up my PC i have the choice of booting either windows xp or ubuntu?

---

### Post by Podex on 2007-04-19
The new Grub should automagically detect your Windows XP as it did on my computer. So yes you should be able to chose between Ubuntu and Windows XP.

I don't know Partition Magic. I used Gparted to make my partitions when I wanted to have both Ubuntu and Windows XP on the same hard-disk. When you boot the Ubuntu LiveCD you can start Gparted (I think it is already on there) and make your partitions in there.
Ultimately it wasn't such a good idea to put both OS's on the same hard-disk, it gave me quite a few problems with Windows. So I bought another hard-disk :P

---

### Post by az on 2007-04-19
By default, the installer will offer to shrink your existing windows partition to make room for Ubuntu.  It will do the partitoining dirty work for you.  

If it doesn't, reboot and defragment your xp system.  Start the installation again and you should then get the option -  The installer will not risk partitioning if it thinks it will fail, it is very cautions.  It works very well and most people have installed a dual-boot system that way.

---

### Post by StealthSoul on 2007-04-19
> **az said:**
> By default, the installer will offer to shrink your existing windows partition to make room for Ubuntu.  It will do the partitoining dirty work for you.  

If it doesn't, reboot and defragment your xp system.  Start the installation again and you should then get the option -  The installer will not risk partitioning if it thinks it will fail, it is very cautions.  It works very well and most people have installed a dual-boot system that way.

I have to install a Dual Boot System?

I haven't had a 2nd OS before so i'm not sure about this..

Also, will it give me a recommended size for the new partition or do i have to pick a size? If I pick a size, How big shall I make it?  I just want Ubuntu on it. Also: Where will it take space from?? The partitions are using up all of the hard drive atm, will it take it out of the D drive? I dont want any space taken from my C drive.. Will it let me choose where to take space from?

Can anyone explain to me how to use Dual Boot with Windows XP and Ubuntu, too?


> **Podex said:**
> The new Grub should automagically detect your Windows XP as it did on my computer. So yes you should be able to chose between Ubuntu and Windows XP.

I don't know Partition Magic. I used Gparted to make my partitions when I wanted to have both Ubuntu and Windows XP on the same hard-disk. When you boot the Ubuntu LiveCD you can start Gparted (I think it is already on there) and make your partitions in there.
Ultimately it wasn't such a good idea to put both OS's on the same hard-disk, it gave me quite a few problems with Windows. So I bought another hard-disk :P

Oh? What problems did you have with putting 2 OS one the same HD?

---

### Post by az on 2007-04-19
> **StealthSoul said:**
> I have to install a Dual Boot System?

I haven't had a 2nd OS before so i'm not sure about this..

Also, will it give me a recommended size for the new partition or do i have to pick a size? If I pick a size, How big shall I make it?  I just want Ubuntu on it. Also: Where will it take space from?? The partitions are using up all of the hard drive atm, will it take it out of the D drive? I dont want any space taken from my C drive.. Will it let me choose where to take space from?

Can anyone explain to me how to use Dual Boot with Windows XP and Ubuntu, too?




Oh? What problems did you have with putting 2 OS one the same HD?

See here:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

You will be asked which partition you would like to resize.  

Do you have to dual boot?  Well, if you want to run two different operating systems on the same machine, yes.  That's what dual-booting is.

---

### Post by louieb on 2007-04-19
>  Is it possible to Keep all my files and not format**Yes** if your machine is fast and has a lot of memory you can use VMWARE and run Ubuntu inside of it. Or just use it as a live CD. IF you go that route there are better Live CDs out there.
>  Can I install Ubuntu 7.04 without losing any files?**Probably**   Do you know Murphy's Law. Well it states that if anything can go wrong it will. I've set up several dual boot systems, most of the time things go just fine. Once I had  to  reinstall XP.  
Since this is your first time and are not sure of what your doing **backup all your data.** Have your XP disk handy. Most important **pay attention** to the questions the installer is asking you.
>  Can anyone explain to me how to use Dual Boot with Windows XP and Ubuntu, too?Yes but I don't want to write another how to on it. If its still not clear after ***reading the links az gave you***:  see the Dual Boot link in my signature. Or the psychocats   link.

---

