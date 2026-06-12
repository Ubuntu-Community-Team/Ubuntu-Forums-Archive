---
title: "USB drive install of Ubuntu 12.04 Server fails - Problem reading data from the CD-ROM"
date: 2013-06-07
forum: Installation &amp; Upgrades
---

### Post by agentofcode on 2013-06-07
This is a self resolved post that I thought I should share with the community.

**PRELIMINARY** 

[LIST=1]
[*]I'm on a Windows 7 machine prepping a bootable USB for installing on an old HP 
[*]I downloaded the official [Ubuntu 12.04 Server 32bit ISO]("http://www.ubuntu.com/download/server") 
[*]The MD5 checksum checked out OK using [winMd5Sum]("http://www.nullriver.com/products/winmd5sum") 
[*]I created a bootable USB using:
[LIST=1]
[*][LinuxLive]("http://www.linuxliveusb.com/") 
[*]then [PenDrive]("http://www.pendrivelinux.com/") 
[*]and finally [Unebootin]("http://unetbootin.sourceforge.net/") 
[/LIST]
     
[/LIST]
[I](all three are sufficient but none corrected the errors I will mention)
[/I] 
**PROBLEM**
During installation I received the following error message:
> 
**[!!] Load installer components from CD**
There was a problem reading data from the CD-ROM. Please make sure it is in the drive. If retrying does not work, you should check the integrity of your CD-ROM.
Failed to copy file from CD-ROM. Retry?

If I chose **Yes** it failed. So I chose **No** and worked my way back to the main install menu to check the *integrity of my CD-ROM *as suggested by the error*. ***NOTE:** In this case CD-ROM means the bootable USB I am installing from.

**When I checked the integrity I received a failed message**:
> 
**[!] Check the CD-ROM(s) integrity**
Integrity test failed

The nic-pcmcia-modules-3.5.0-23-generic-di_3.5.0-23.35~precise1_i386.udeb file failed the MD5 checksum verification. Your CD-ROM or this file may have been corrupted.


* At this point, I knew the CD-ROM (bootable USB) was not corrupted because I checked its MD5 checksum before creating the bootable drive. So it had to be the file.*

**RESEARCH**
Using the advice from [a post with the same situation]("http://askubuntu.com/questions/127398/usb-drive-install-of-ubuntu-12-04-server-fails-cant-find-components-from-cd-r"), I took the bootable USB back to my Win7 machine and searched for all extensions that ended with **.ude**. I discovered the extension was indeed wrong as assumed in the post. I changed all the wrong extensions I discovered to **.udeb** as suggested.

Once I finished I took the bootable USB back to my potential server and began installing again. Unfortunately I was provided with the same error. No matter what I did I ended up with the same error. It wasn't until I discovered [this page discussing the particular file I was dealing with]("http://packages.ubuntu.com/precise-updates/i386/nic-pcmcia-modules-3.5.0-23-generic-di/download") that I realized the situation is worse than just the extension being incomplete. This is when the full extension actually caught my eye. I saw it should be **~precise1_i386.udeb **and in my case this was not so. It appeared to be very inconsistent for a number of files.

**SOLUTION (parts I corrected are in red)**
**n** = no (wrong file name)
**y** = yes (corrected file name)

**n** firewire-core-modules-3.5.0.23-generic-di_3.5.0-23.35~precise.ude
**y **firewire-core-modules-3.5.0.23-generic-di_3.5.0-23.35~precise[COLOR=#b22222]1_i386[/COLOR].ude[COLOR=#b22222]b[/COLOR]

**n** fs-core-modules-3.5.0.23-generic-di_3.5.0-23.35~precise1_i386.ude
**y **fs-core-modules-3.5.0.23-generic-di_3.5.0-23.35~precise1_i386.ude[COLOR=#b22222]b[/COLOR]

**n **fs-secondary-modules-3.5.0.23-generic-di_3.5.0-23.35~precise1.ude
**y **fs-secondary-modules-3.5.0.23-generic-di_3.5.0-23.35~precise1[COLOR=#b22222]_i386[/COLOR].ude[COLOR=#b22222]b[/COLOR]

**n **message-modules-3.5.0.23-generic-di_3.5.0-23.35~precise1_i386.ude
**y** message-modules-3.5.0.23-generic-di_3.5.0-23.35~precise1_i386.ude[COLOR=#b22222]b[/COLOR]

**n **multipath-modules-3.5.0.23-generic-di_3.5.0-23.35~precise1_i3.ude
**y **multipath-modules-3.5.0.23-generic-di_3.5.0-23.35~precise1_i3[COLOR=#b22222]86[/COLOR].ude[COLOR=#b22222]b[/COLOR]

**n** nic-usb-modules-3.5.0.23-generic-di_3.5.0-23.35~precise1_i386.ude
**y **nic-usb-modules-3.5.0.23-generic-di_3.5.0-23.35~precise1_i386.ude[COLOR=#b22222]b[/COLOR]

**n **nic-pcmcia-modules-3.5.0-23-generic-di_3.5.0-23.35~precise1_i.ude
**y** nic-pcmcia-modules-3.5.0-23-generic-di_3.5.0-23.35~precise1_i[COLOR=#b22222]386[/COLOR].ude[COLOR=#b22222]b[/COLOR]

**n **parport-modules-3.5.0.23-generic-di_3.5.0-23.35~precise1_i386.ude
**y **parport-modules-3.5.0.23-generic-di_3.5.0-23.35~precise1_i386.ude[COLOR=#b22222]b[/COLOR]

**n **pcmcia-storage-modules-3.5.0.23-generic-di_3.5.0-23.35~precis.ude
**y **pcmcia-storage-modules-3.5.0.23-generic-di_3.5.0-23.35~precis[COLOR=#b22222]e1_i386[/COLOR].ude[COLOR=#b22222]b[/COLOR]

**n **speakup-modules-3.5.0.23-generic-di_3.5.0-23.35~precise1_i386.ude
**y **speakup-modules-3.5.0.23-generic-di_3.5.0-23.35~precise1_i386.ude[COLOR=#b22222]b[/COLOR]

**n **squashfs-modules-3.5.0.23-generic-di_3.5.0-23.35~precise1_i38.ude
**y **squashfs-modules-3.5.0.23-generic-di_3.5.0-23.35~precise1_i38[COLOR=#b22222]6[/COLOR].ude[COLOR=#b22222]b[/COLOR]

**n **storage-core-modules-3.5.0.23-generic-di_3.5.0-23.35~precise1.ude
**y **storage-core-modules-3.5.0.23-generic-di_3.5.0-23.35~precise1[COLOR=#b22222]_i386[/COLOR].ude[COLOR=#b22222]b[/COLOR]

**NOTE:** There was one more I fixed. Unfortunately I don't remember what file it was or what I had to add to the file name. However, I'm confident that with this information you now know what to look for if you are in a similar situation.

**CONCLUSION**
From what I gather is that the install process knows what files should exist. If the file name is wrong then it throws an error and displays the file name that it is looking for. The only way it can be found is if it exist. This means it has to be named appropriately. I could not discover why/how the misnaming was happening. I theorize that it has something to do with the character limitation of the Windows environment in combination of the Windows apps used for creating the bootable USB. I conclude with this because the ISO itself checks out OK. It's either that or a tiny Leprechaun in my machine messing with me :)

**PLEASE ELABORATE**
If you have additional feedback, solutions or theories...please share them.

---

### Post by vadimkolchev on 2013-06-07
Something is going wrong here. Probably it is the way your image onto USB. In Windows ImageWriter is known to work ok. Try it, please. If it doesn't help, corrupted files usually mean corrupted image, so try to download once again, or a different one, or just from a different mirror.

---

### Post by agentofcode on 2013-06-07
> **vadimkolchev said:**
> Something is going wrong here.
** I agree**
> **vadimkolchev said:**
> Probably it is the way your image onto USB.
**This is what I thought. I figured it was one of the three bootable USB creators I used. But all had the same exact result. As I mentioned the ISO itself checked out OK during the md5 checksum. This led me to believe it was happening during the bootable USB creation process and why I used multiple applications in hopes one would work.**
> **vadimkolchev said:**
> In Windows ImageWriter is known to work ok. Try it, please. If it doesn't help, corrupted files usually mean corrupted image, so try to download once again, or a different one, or just from a different mirror.
**I have solved my issue but I am curious to know if Windows ImageWriter will work. I will give it a try to see if I get the same result as the other three bootable USB creators. The ISO I have passes the md5 checksum so in theory I shouldn't need to DL another one. Since it checks out OK, this means the corruption must be happening during the USB creation process.**

---

### Post by agentofcode on 2013-06-07
> **agentofcode said:**
> 
**I have solved my issue but I am curious to know if Windows  ImageWriter will work. I will give it a try to see if I get the same  result as the other three bootable USB creators. The ISO I have passes  the md5 checksum so in theory I shouldn't need to DL another one. Since  it checks out OK, this means the corruption must be happening during the  USB creation process.**

I Downloaded [Win32 Disk Imager]("http://sourceforge.net/projects/win32diskimager/"):  **NOTE**:  I assume Win32 Disk Imager is the same as Windows ImageWriter since all  searches led me to it. I could not use Win32 Disk Imager since Ubuntu  downloads come in ISO and not IMG.

---

### Post by url00 on 2013-07-01
This fix works great! Thank you so much for posting.

---

### Post by malexios on 2013-07-09
I registered to say thanks and that this fix worked perfectly. I was using ubuntu-12.04.2-server-i386 with unebootin on Win 7 Here is the list of files that needed to be changed.

> firewire-core-modules-3.5.0-23-generic-di_3.5.0-23.35~precise1_i386.udeb
fs-core-modules-3.5.0-23-generic-di_3.5.0-23.35~precise1_i386.udeb
fs-secondary-modules-3.5.0-23-generic-di_3.5.0-23.35~precise1_i386.udeb
message-modules-3.5.0-23-generic-di_3.5.0-23.35~precise1_i386.udeb
multipath-modules-3.5.0-23-generic-di_3.5.0-23.35~precise1_i386.udeb
nic-pcmcia-modules-3.5.0-23-generic-di_3.5.0-23.35~precise1_i386.udeb
nic-shared-modules-3.5.0-23-generic-di_3.5.0-23.35~precise1_i386.udeb
nic-usb-modules-3.5.0-23-generic-di_3.5.0-23.35~precise1_i386.udeb
parport-modules-3.5.0-23-generic-di_3.5.0-23.35~precise1_i386.udeb
pcmcia-storage-modules-3.5.0-23-generic-di_3.5.0-23.35~precise1_i386.udeb
speakup-modules-3.5.0-23-generic-di_3.5.0-23.35~precise1_i386.udeb
squashfs-modules-3.5.0-23-generic-di_3.5.0-23.35~precise1_i386.udeb
storage-core-modules-3.5.0-23-generic-di_3.5.0-23.35~precise1_i386.udeb


---

### Post by adj7388 on 2013-07-17
A kind soul on the interwebs has provided an automated solution to this problem. This worked for me:
[http://cirrus.ucsd.edu/~pierce/fix_ubuntu_usb/](http://cirrus.ucsd.edu/~pierce/fix_ubuntu_usb/)

---

### Post by danhansendenmark on 2014-02-23
Hi,

I did this post, because even though this thread is marked "SOLVED" the fix didn't work in my case.[I]


With thanks to Mr. David W. Pierce & Mr. Christopher Hinkle[/I]

I've been fighting this all night long.. Now it's early morning and I found the solution. 
There's many different suggestions to the problem out there, and I can see why some are trying to fix it by mounting this and mounting that. It really looks like a mounting error. But please note, that the error in most cases appears after reading from the USB-stick. The real issue is the file names. If you want to install the e.g. Ubuntu 12.04 Desktop there's no problem. If you want to install Ubuntu Server 12.04 you got a problem. 

Mr. AgentOfCode describes the problem pretty good above. 

It doesn't help to choose another method, Unetbootin, Lili USB Creator, Pendrivelinux etc., same error!

Here' the solution! You can use this solution in both Windows and Linux, doesn't matter were you make the bootable USB-stick
Follow this Todo: [http://cirrus.ucsd.edu/~pierce/fix_ubuntu_usb/](http://cirrus.ucsd.edu/~pierce/fix_ubuntu_usb/)

If the link for some reason goes dead, please don't hesitate to leave a note, I've downloaded the scripts and wrote a short ToDo...

I'll leave this solution in the forums I have access to...

Kind Regards,
Dan Hansen
Denmark

---

