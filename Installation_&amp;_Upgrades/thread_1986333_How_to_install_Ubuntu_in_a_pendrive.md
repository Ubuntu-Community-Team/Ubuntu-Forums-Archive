---
title: "How to install Ubuntu in a pendrive?"
date: 2012-05-24
forum: Installation &amp; Upgrades
---

### Post by Shiryu on 2012-05-24
I want to have a pendrive (USB drive) with (K)Ubuntu and some apps, including Firefox and Java, and use it in any computer.
Fast loading would be good, I would rather disable unneeded features such as graphical enhancements to gain speed.
I want to be able to save personal files (documents, images, ...) in the pendrive when I use the this Ubuntu installation.

It would help us to access bank account through web, because we have many Windows users and Windows is not safe to access bank account due to malwares.

I do not like Unity and I prefer the normal Gnome without inverted window or KDE.

How to build a pendrive with Ubuntu?

Thanks.

---

### Post by wilee-nilee on 2012-05-24
A pendrive for bank usage is suggested as a no save that is what makes it safer.

But if you want one persistent (saves stuff) unetbootin does this with ubuntu. it is on the web and in the ubuntu repos.

I use this one myself, it will build a persistent and have multiple ISO's as well. The persistent is for only one though.

[http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

---

### Post by HalfNote5 on 2012-05-24
use remastersys to create an ISO backup of your system, and then use unetbootin's "Use Custom ISO" feature to load the ISO into your flash drive.

Remastersys may require adding some sources. If "sudo apt-get remastersys" fails, 
add the following to your /etc/apt/sources.list

deb [http://www.remastersys.com/repository](http://www.remastersys.com/repository) squeeze/
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) squeeze/


and then do:

sudo apt-get update


Then the following should work:

sudo apt-get install remastersys unetbootin


Cheers!

---

### Post by HalfNote5 on 2012-05-24
Note: My copy of Remastersys has been uninstalling itself after each use.  You (hopefully) won't have the same problem, but if you do, then

sudo apt-get install remastersys

will put it right back where it belongs. = )

---

### Post by Old_Grey_Wolf on 2012-05-24
I'm not sure I understand exactly what you want. :)

I have done a normal install of Ubuntu on an 8 GB thumb drive (USB drive). Once it is installed and booted, you can modify it just like any hard drive install. 

I removed my hard drive when I made the thumb drive so that grub wouldn't try to offer the other operating system's grub on the hard drive. Nor did I want to take the risk of messing up my hard drive install. After I made the thumb drive I re-installed the hard drive.

I installed Ubuntu on the thumb drive by using a live CD/live USB and following the same procedures I would use to install it on a hard drive. Then I modified it the same way I would a hard drive install; deleting apps, changing DE, etc.

It works just like a hard drive install except that a thumb drive is not as fast as a hard drive. I have to boot it occasionally to get software updates. I also save any personal files to it as if it is a hard disk.

---

### Post by HalfNote5 on 2012-05-24
Also, if you're using the unetbootin/remastersys combo, you can not only customize your system, but you can make the resulting USB drive persistent (meaning you can save files, and such) OR you can leave the live-boot NON-persistent, and make a second partition on the USB drive.

That way, no matter what happens, your install stays fresh and uncorrupted.

The only downside is that the second partition isn't available under Windows.

---

### Post by C.S.Cameron on 2012-05-24
If you want a (K)Ubuntu pendrive that boots in any computer just use Startup Disk Creator to make a persistent Live USB.
It is available on the Live CD.
Use "Stored in Reserved extra space" to set persistence size.
If you copy the casper-rw file and rename it home-rw you end up with a separate home file that you can use in future upgrades.
Alternately you can make casper-rw and home-rw partitions.

A Full install also works pretty good but requires more space and takes longer to make, advantages over persistent are debatable.

Remastersys is cool if you want to start with a custom setup but takes the most work to make a bootable flash. You can use persistent partitions or files here also. with a persistent home-rw, you can renew your system without loosing your settings.

---

### Post by yeehi on 2012-05-25
Use [Linux Live USB Creator]("http://www.linuxliveusb.com/")

Have fun with your pendrive!

---

### Post by JOHNNYG713 on 2012-05-25
Download the ISO of your choice
open Startup disk creator
set the amount of storage ( persistance) you want
and install
This will run as a live system but you can still change it as you wish and install and save files, and will remain on the next boot
If you wish to install  the ISO as a hard drive install to your pen drive then ether burn a CD/DVD (Or use another pendrive),  install the ISO and boot to the live session, plug in the pendrive you want to install to as a hard drive and install to it as you would normaly to any installed hard drive!
Carry on ! Hope this helps you out !
Note Unetbootin will work also in place of startup disk creator !

---

### Post by HalfNote5 on 2012-05-25
> **C.S.Cameron said:**
> ...Remastersys is cool if you want to start with a custom setup but takes the most work to make a bootable flash. You can use persistent partitions or files here also. with a persistent home-rw, you can renew your system without loosing your settings.

Precisely = )

I suggested Remastersys because usually when I want to make a USB live drive, I want it to have all the goodies I've carefully installed on the system and tweaked (such as a crap-tonne of WiFi drivers for all contingencies). I don't usually want it to just be the stock ISO. 

However, if that's what Shiryu is LOOKING for, then yes, using Remastersys for that purpose would be a pain in the tail.  ; )

---

### Post by C.S.Cameron on 2012-05-25
If you are using it for banking you should probably at least use an encrypted home.
I have not tried this with a persistent install, I know it works with a Full install like post 5 suggests.
Thumb drives are easy to loose.
For banking I do as post 2 suggests, no persistence. you could still make a custom disk with Remastersys, just no persistence.

---

### Post by Shiryu on 2012-05-27
Thanks.

I  installed the Live Kubuntu and it works.
It is very slow and it came without Java. The bank requires Java.

We will not store data about bank, we will use it for payments, transfers and shopping.

Two partitions would be good, the system and apps partition without  persistence, and the personal files partition, with persistence.

I would like to install a lightweight Gnome, but the main version of Ubuntu comes with Unity.

I do not have any physical CD and I do not to know how to install it in the pendrive with the same way of hard drive installation.

Will I have to install and configure the system, create an image with Remastersys and install it in the pendrive?

---

