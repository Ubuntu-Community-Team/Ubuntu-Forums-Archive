---
title: "Customizing Ubuntu 11.04 from USB stick"
date: 2012-03-11
forum: Installation &amp; Upgrades
---

### Post by traltixx on 2012-03-11
Hi,
I am trying to custimize my ubuntu 11.04 from USB stick. 
I used this program to create the USB :
Universal-USB-Installer-1.8.5.3.exe from [http://www.pendrivelinux.com/downloa...-Installer.exe](http://www.pendrivelinux.com/downloa...-Installer.exe)
I downloaded ubuntu-11.04-desktop-i386.iso from [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) for the image.
The target machine is a hp/compaq tc4200 laptop without a hard drive or optical drive and the machine I'm using is a windows 7 x64 to create the USB.
So far everything works fine with the image, I can install and run the OS and surf the net, etc.
Anyway, now I want to custimize the image so that skype and a few other applications and drivers are installed by default. Right now, everytime I install skype and restart, I have to re install it.
Do I need a linux machine to create the image? How can I make the USB stick/image on it persist?

---

### Post by UnknownFearNG on 2012-03-11
The reason why programs are not staying installed is because you are running a Live session of Ubuntu. It's basically meant to test the OS before you install it. Nothing gets saved upon reboot.

---

### Post by Kirboosy on 2012-03-11
You can use a tool called [UCK]("http://uck.sourceforge.net/") in order to customize the ISO image. However you will need a working Ubuntu/Linux system to run the tool.


Another approach would be to enable persistence mode on the USB flash drive. I use [LinuxLive USB Creator]("http://www.linuxliveusb.com/") and it works great!

Hope that points you in the right direction.

---

### Post by traltixx on 2012-03-12
Thanks for the pointers. 
I tried downloading LinuxLive and enabled persistance but for some reason, after creating the bootable USB drive, booting the laptop from it, creating random file on the desktop seems to work fine. Only when I reboot to check if the file persists or not is when the laptop won't boot (says 'Non-System disk or disk error').
I've changed the size of the persistance when creating the bootable USB drive from various values (10MB to 1GB in increments of 100MB) and still gives the same error.
 
Also, I noticed that when booting the USB, it doesn't give me the option to run persistant or live..only to 'try ubuntu' or 'install ubuntu' (when i chose 'install' it doesn't work anyway because it requires more than 4Gb of free space which it doesn't have)
 
Anyway, I'll have a look at the UCK tool and see how easy/hard it is to work it.
 
Ok. even more investigating LinuxLive: I can't just restart or reboot the laptop. I have to shut it down, physically remove the USB and insert it again (in the same USB slot) and start up the laptop again and it works. Even doing a shutdown and then starting up still gives the 'Non-System disk or disk error'. Any idea why I have to physically remove the USB (and insert it again) for it to work?

---

### Post by oldfred on 2012-03-12
How large is flash drive? I have 12.04 full install on a 8GB partition on my 16GB flash drive. My laptop does not have a lot of spare space so I do not create an additional / (root) partition like I do on my desktop.


Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

Step by Step Full install 8GB C.S.Cameron Post #7
[http://ubuntuforums.org/showthread.php?t=1719346](http://ubuntuforums.org/showthread.php?t=1719346)
It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

---

### Post by Kirboosy on 2012-03-12
> **oldfred said:**
> How large is flash drive? I have 12.04 full install on a 8GB partition on my 16GB flash drive. My laptop does not have a lot of spare space so I do not create an additional / (root) partition like I do on my desktop.


Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

Step by Step Full install 8GB C.S.Cameron Post #7
[http://ubuntuforums.org/showthread.php?t=1719346](http://ubuntuforums.org/showthread.php?t=1719346)
It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)
+1 Great Links!

---

### Post by traltixx on 2012-03-12
Thanks for those links.
The flash drive is 4GB by the way

---

### Post by oldfred on 2012-03-12
Then 4GB is too small for a full install. You can only run with persistence or buy a larger flash drive.

---

### Post by traltixx on 2012-03-12
Yes, thats exactly what I'm trying to do (persistance not full install). But for some reason LinuxLive's persistance doesn't work on reboot. I have to physically remove the usb drive and insert it again for it to work (see my previous posts). Any ideas why?

---

### Post by Kirboosy on 2012-03-13
I'm not 100% sure as to why it does that but it may have to do with the way LinuxLive unmounts the flash drive the BIOS ignores it until its unplugged and replugged in.

---

