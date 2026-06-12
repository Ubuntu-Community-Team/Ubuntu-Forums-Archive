---
title: "Ubuntu (grub?) distorted on try launch"
date: 2014-02-11
forum: Installation &amp; Upgrades
---

### Post by john160 on 2014-02-11
Apologize for the odd title, but I didn't really know how to word it. Anyways I want to install Ubuntu 12.04 LTS onto my 64-bit Dell Inspiron 15 laptop (Intel Pentium) with preinstalled Win 8. I've disabled secure boot and fast boot and have launched from USB stick, but onces I boot into the flashdrive the, what I'm assuming is grub, is disorted - cannot read anything. I can still move the highlighted bar up and down, but I don't know what I'm highlighting. I chose the first highlighted item and it booted me into Ubunto no problem and can run it without any problems, I'm actually posting this from Ubuntu trial run, haven't installed it. 

I do not know why it's distorted, I've booted Fedora on this laptop and it doesn't experience any distortion what so ever. I have two USB flash drives and have used both so it can't be that. I've re-installed the OS onto the flashdrive many times and re-downloaded Ubuntu to no success. So it's become apparent that it's just Ubuntu (or just grub alone). I want to dual boot Ubuntu on this laptop, why I haven't gone with Fedora. I've dual-booted Ubuntu before and this is the first time I've encountered this problem. And I don't want to go ahead with the install without finding a clear solution or answer to this problem, maybe it'll be fixed once installed, but I'm too chicken to risk that. I don't want to install and still have that problem and have a bit of a hassle booting into Ubuntu or Win 8. 

Here are photos I've taken to give a better understanding:

[IMG]http://oi60.tinypic.com/2qb9e8o.jpg[/IMG]

[IMG]http://oi57.tinypic.com/160rmt4.jpg[/IMG]

[IMG]http://oi62.tinypic.com/359xy0l.jpg[/IMG]

[IMG]http://oi61.tinypic.com/2madfb.jpg[/IMG]

---

### Post by oldfred on 2014-02-11
Do you have the new 12.04.4? I think it now has all the updates that were in 13.10 and that also is required for new systems. A few have such new systems that they need 14.04 with even newer kernel & drivers, but it will not be final until April.

If new Haswell system, you need to leave legacy boot on, even when booting in UEFI mode. Some issue with many  Intel chips. See comments:
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

      
 Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)
Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

---

### Post by john1602 on 2014-02-12
I've tried the general 12.04.4 and the 12.04.2 that's specifically for my Dell laptop and both still don't work. I've tried 13.10 and that works just fine for me, no distortion. But I want to install LTS. I've tried many methods and still no success.

---

### Post by grahammechanical on 2014-02-12
> [COLOR=#000000] I want to install LTS. [/COLOR]

At the end of April you will be able to upgrade from 13.10 to 14.04 LTS. That may be the simple way to go. Two and one half months wait.

Regards.

---

### Post by Bucky Ball on 2014-02-12
> **grahammechanical said:**
> At the end of April you will be able to upgrade from 13.10 to 14.04 LTS. That may be the simple way to go. Two and one half months wait.



^^^
This. Install 13.10 and enjoy! You'll have a good idea about Ubuntu by the time 14.04 gets here and an upgrade will be a couple of button clicks away in April and you can stay with 14.04 LTS for five years if you like. But the good news if you want to only run LTS is that LTS upgrades to LTS. Thus, 14.04 will upgrade directly to 16.04 LTS, and so on, leapfrogging the interim releases. ;)

---

