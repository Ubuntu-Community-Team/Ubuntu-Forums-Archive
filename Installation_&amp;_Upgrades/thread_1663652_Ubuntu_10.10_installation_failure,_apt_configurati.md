---
title: "Ubuntu 10.10 installation failure, apt configuration problem"
date: 2011-01-09
forum: Installation &amp; Upgrades
---

### Post by scquote on 2011-01-09
Hi! This is my first time installing or using anything linux related and I'm having a problem installing the thing. 

Used both a USB (Unetbootin) and a CD to install but neither works and both give me the same error: 

Apt configuration fail; an attempt to configure apt to install additional packages from the cd failed. 

followed by a 

Installation failed (or something similar). 

Any help is appreciated.

---

### Post by Bucky Ball on 2011-01-09
Go for 10.04 LTS. You will get a smoother ride as a new user. 10.10 has issues at the moment.  ;)

If you have the same issues with that we can start digging ...

Welcome!

---

### Post by scquote on 2011-01-09
Just downloaded; I'll give it a go.

Edit: 10.04 installation worked but I still got the "apt configuration problem" error. I don't entirely know what that means :[

---

### Post by Redsandro on 2011-01-14
I have the same problem when installing **Ubuntu 10.10 x64** from USB created with **unetbootin** and, on a different machine, **Lubuntu 10.10 i386** from USB, also created using unetbootin.

This is a serious flaw in the installer. I don't get what a bug like that is doing in an operating system installer three months after the release. Is there a command to skip the *install additional packages from the (non-existing) cd*?

**-edit-**

[i]Description of problem:
When trying to install Ubuntu 10.10 from USB, ubiquity crashes with this message: "An attempt to configure apt to install additional packages from the CD failed."

Root of problem:
The problem is that the file structure on the usb differs to what is on a livecd and apt-setup is unaware of this.

Workaround:
To resolve this, simply copy the contents of filesystem.squashfs on the iso into the usb stick. Luckily the parts it is reading from this appear to be just apt config files so the fact that you lose symbolic links or permissions on a FAT32 usb stick shouldn't matter.[/i]

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/658865](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/658865)

---

### Post by snehalmasne on 2011-02-05
I used both a USB (Unetbootin) and a CD (10.10) to install but neither worked and both gave me the same error: 

"Apt configuration fail; an attempt to configure apt to install additional packages from the cd failed."

Then I tried the same with 10.04 LTS from CD still its throwing same problem.

Interesting thing is that before some days I successfully did UEC setup with 10.04 LTS and now its not working. WTF !! Is something wrong with me or my devices ?

Someone please help me out... 


Regards,
[Snehal Masne]("http://www.techproceed.com")

---

### Post by Redsandro on 2011-02-05
Just a thought:

10.04, which used to work, is now 10.04.1 on download.
Maybe they 'fixed' something with the same broken installer used for 10.10?

---

### Post by snehalmasne on 2011-02-07
Here goes what happened to me and the workaround I got for successful cloud setup:

I used both a USB (Unetbootin+Universal USB) and a CD (10.10) to install but neither worked and both gave me the same error: 

"Apt configuration fail; an attempt to configure apt to install additional packages from the CD failed."

 Some days ago, I successfully did UEC setup with 10.04 LTS from CD. But even that was also not working. I thought that something went wrong with  me or my devices.

After searching a lot on net, I got following:

> Root of problem:
The problem is that the file structure on the usb differs to what is on a livecd and apt-setup is unaware of this.
 Workaround:
To resolve this, simply copy the contents of filesystem.squashfs on the  iso into the usb stick. Luckily the parts it is reading from this appear  to be just apt config files so the fact that you lose symbolic links or  permissions on a FAT32 usb stick shouldn't matter.



I don't think that's the problem, as I was getting same error while using CD. As setting up the cloud is part of my project work, I spent almost a week and many CDs but all failed. 



I thought its somehow related to the broken filesystem. So I tried  [**Universal USB Installer**]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") to create bootable USB with PartedMagic (you can try paragon partition manager also) and deleted all partitions from HDD. Then created primary and extended partitions followed by the installation of UEC on extended partition. It worked for 3 other machines as well. 



It's worth trying. All the best !!




Regards,
[Snehal Masne]("http://www.TechProceed.com")

---

### Post by dagoss on 2011-02-20
I was experiencing this problem when installing lubuntu 10.10.  I had used unetbootin to create the boot the USB disk.  I used the exact same disc image, but I created it with the USB start-up disc creator that comes with Ubuntu.  That disc worked just fine after that.

I'd suspect that this issues has something to do with unetbootin, since everyone in this thread that seems to have run into this problem created the disc that way.

---

### Post by Redsandro on 2011-02-20
I'm wondering, why are major problems like this never fixed during a release? Is there some kind of policy that only minor changes are allowed within a release?

---

### Post by phatmat on 2011-02-28
okay people i know i am a new user, but i have found the solution!
In fact i joined just to help with this one lol

anyways, the problem seems to be Windows User Account Control.

I have tested this on several computers now (2 desktops, 1 laptop)

I was only able to have a successful installation (after using all 3 computers) after disabling UAC.

SO DISABLE UAC!!!! Then re-try using the application (it seemed to do it for alot of applications actually)

dont we all hate it anyways lol

Let me know if this has helped any one please!

:popcorn::KS:D i like smiley's

---

### Post by xaivern on 2011-03-09
I am getting the same error... Ive tried doing what is mentioned here but its not working. The UAC is disabled, i cant wipe my hard drive and start new because I cant backup most of it so im trying to install on a new partition and it always stops with the cd thing...

---

### Post by slythfox on 2011-11-15
Windows UAC is most probably entirely irrelevant.

I had installed Ubuntu 11.10 to my usb drive using UNetbootin on Windows. It installed fine on one machine, but the other machine I gave said error. After a few tries on this one machine, I switched to Universal USB Installer. Once I had booted up the Ubuntu live image, I ran the following command to remove the offending script [(as suggested here)]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/658865"):

```
sudo rm /usr/lib/ubiquity/apt-setup/generators/40cdrom
```

I am not sure which one of these fixed the problem since I tried them both at the same time.

---

### Post by Bucky Ball on 2011-11-15
This thread very old and very dead but your tips might help someone ... ;)

---

### Post by MisterTwisty on 2011-12-12
Same issues here using Unebootin to copy the Ubuntu 11.10 iso to my USB stick. The solution for me was to reformat the usb stick within windows as a "FAT" file system prior to running Unebootin. Installation worked a dream after that.

---

### Post by Innocent Devil on 2012-01-22
> **slythfox said:**
> Windows UAC is most probably entirely irrelevant.

I had installed Ubuntu 11.10 to my usb drive using UNetbootin on Windows. It installed fine on one machine, but the other machine I gave said error. After a few tries on this one machine, I switched to Universal USB Installer. Once I had booted up the Ubuntu live image, I ran the following command to remove the offending script [(as suggested here)]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/658865"):

```
**sudo rm /usr/lib/ubiquity/apt-setup/generators/40cdrom**
```

I am not sure which one of these fixed the problem since I tried them both at the same time.

Thanks,
This really solved my problem, when i was installing from USB

---

