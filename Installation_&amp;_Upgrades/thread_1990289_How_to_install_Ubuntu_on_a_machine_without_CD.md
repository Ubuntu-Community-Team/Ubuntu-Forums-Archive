---
title: "How to install Ubuntu on a machine without CD"
date: 2012-05-29
forum: Installation &amp; Upgrades
---

### Post by UlfDunkel on 2012-05-29
I have wasted the whole day trying to install Ubuntu 12.04 Server on a ThinClient PC which only has a CF-Card with 1GB RAM, plus USB ports, but no other hard drive and no internal CD/DVD drive.

Whatever I try, all installations always want to get files from a CD-ROM which I don’t have actually.

I tried to install from a 2GB USB stick which always failed because the installation process meant that at least one file had a wrong checksum.

Then I tried to prepare the CF-Card the same way, with the same bad result. It seems as if I either use the wrong installation image (ubuntu-12.04-server-i386.iso from the Ubuntu site), or as if the Installer software has an issue with this archive. I used the Universal USB Installer from [www.pendrivelinux.com](www.pendrivelinux.com) to prepare the USB stick and the CF-Card using Windows 7.

Do I really have to bite the bullet and get me an external CD/DVD drive just for this damned Ubuntu server installation on the ThinClient? No way out?

Any hints, comments and booohs are really appreciated. :)

---

### Post by kc1di on 2012-05-29
Go to the page and read the section install without CD.

Also if the machine has a usb port you can install from a flash drive. 
how did you prepare the flash drive?
If you have access to another machine. even a windows on I would download and install unetbootin and prepare the flash drive using it.  work great here anyway.
here's the page for unetbootin
[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")
Good luck 
give a shout if you need more help.

---

### Post by lukeiamyourfather on 2012-05-29
> **UlfDunkel said:**
> 
I tried to install from a 2GB USB stick which always failed because the installation process meant that at least one file had a wrong checksum.

Try a different USB flash drive.

---

### Post by UlfDunkel on 2012-05-30
> **lukeiamyourfather said:**
> Try a different USB flash drive.

I tried two different USB sticks, and also tried to directly write the installation data to the CF-Card. No change.

When I tried to install PuppyLinux, it succeeded without any issues, but the Ubuntu installations always fail.

I prepare the USB sticks either using „Universal USB Installer 1.8.9.8“ (Windows 7) or using the current Windows version of UNetbootin. I tried Ubuntu 12.04 LTS Desktop as well as Ubuntu 12.04 LTS Server.

I am now going to try Ubuntu 12.04 Alternate i386. But I guess the result will be the same again: The machine doesn’t recognize the USB stick as a USB CD-ROM, or there will be MD5 checksum issues again.

Do you know another distribution for the following purposes:

- small distro
- Apache2
- PHP5
- OpenVPN
- Firefox 12 (which also requires xorg or similar)

---

### Post by UlfDunkel on 2012-05-30
> **UlfDunkel said:**
> When I tried to install PuppyLinux, it succeeded without any issues, but the Ubuntu installations always fail.

All other installations but PuppyLinux fail from the USB stick, whatever I try. :(

Do you know how to upgrade from Puppy to Ubuntu on the machine itself?

---

### Post by lukeiamyourfather on 2012-05-30
> **UlfDunkel said:**
> All other installations but PuppyLinux fail from the USB stick, whatever I try. :(

Do you know how to upgrade from Puppy to Ubuntu on the machine itself?

Puppy Linux has nothing to do with Ubuntu so there's no upgrade path to it. You might try the alternate install ISO for Ubuntu instead of the live ISO.

---

### Post by UlfDunkel on 2012-06-04
I guess my main issue with this thin client is, that it only provides a CF-Card with 1GB storage. So I am quite sure that every attempt to install Ubuntu 12.04 will fail as long as the storage device hasn't at least 4GB space, right?

I guess I have to look for a LTSP version of Ubuntu? Or is there another really small distro of Ubuntu which I could try?

---

### Post by nicolasforum89 on 2012-06-04
Thank you for the tip !

---

### Post by mastablasta on 2012-06-04
> **UlfDunkel said:**
> I guess my main issue with this thin client is, that it only provides a CF-Card with 1GB storage. So I am quite sure that every attempt to install Ubuntu 12.04 will fail as long as the storage device hasn't at least 4GB space, right?

 
You need at least 8GB for full install i believe. So if you have a USB stick you can install to that (from a USB stick).
> 
 I guess I have to look for a LTSP version of Ubuntu? Or is there another really small distro of Ubuntu which I could try?
 There is. it's called mini.iso. here is a nice how to: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
 
 
note that:
>  
After this minimal install (using Ubuntu 12.04 as an example for these screenshots), the total installation size is a little over 1 GB. 

so the place you are instlaling to needs at least 2GB. Liek i said if there is a USB port free you can attach an 8GB USB flash drive and install to that.
 
did you check the md5sum before creating a live USB?: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 
Beside from Puppy you could try Slitaz (doesn't need much space) or maybe Ubuntu based Bodhi Linux is also small on install. not quite sure though. edit it also needs: 1.5g HD space

---

