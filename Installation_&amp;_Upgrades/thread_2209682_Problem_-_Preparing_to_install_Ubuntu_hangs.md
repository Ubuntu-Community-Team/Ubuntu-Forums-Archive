---
title: "Problem - Preparing to install Ubuntu hangs"
date: 2014-03-06
forum: Installation &amp; Upgrades
---

### Post by princeofthecity on 2014-03-06
[COLOR=#333333][FONT=UbuntuRegular]Attempting to do a complete install of Ubuntu 12.04.4 LTS (32-bit) on my Asus Eee PC 1018P netbook with 2GB RAM, 250GB HD.

I created a bootable USB with LiLi and the Ubuntu 12.04.4 LTS iso and was able to successfully boot from the USB. However, at the point where I tell Ubuntu to actually install the OS (with checkboxes checked to install latest updates for flash etc and the checkbox checked for fluendo mp3) it seems to just hang with the spinning wheel going. I have the netbook plugged into a power source and the ethernet is also connected.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I let this happen overnight thinking I would wake up to the next step in the installation or just that it completed but it was still hanging. I was able to click out of the installer and the os was running, however, I believe it is just running directly from the USB stick and not from my netbook's HD. I also was able to open up Mozilla and get a webpage so I know the connectivity is there to allow the installer to download whatever updates it needed during installation.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Has anyone had this happen to them at all? I didn't see anything in the Eee PC installation documentation [here]("http://www.linuxliveusb.com/help/guide/step4").

Additionally, my second attempt seems to be yielding the same results - this time I created my bootable USB with LinuxLive (LiLi), in Step 4 I had the unchecked to Enable launching LinuxLive in Windows (requires internet to install) which, if I am reading the [documentation]("http://www.linuxliveusb.com/help/guide/step4") correctly, means Ubuntu will be virtualized when the machine is booted from the resulting bootable USB.  I am trying to do a complete install, replacing Windows OS.

Has anyone experienced this or know of a thread where I may be able to get a better understanding of how to resolve this?
[/FONT][/COLOR]

---

### Post by coldraven on 2014-03-07
I do not know why you are having a problem but I have had none installing Xubuntu 13.10 on this eeePC 900.
The only difference is that I used Unetbootin to make a bootable (1GB) SD card. I have never heard of or tried LiLi.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I could have used a USB stick but as a 700MB iso fits nicely on my 1GB card I use it for all my installs. It seems a waste to use an 8GB stick.

---

### Post by einfach3 on 2014-03-07
[FONT=lucida sans unicode]I'm Having the exact same Problem with the following system:
GA-Z87-HD3
i7 4771
32GB RAM
Asus Xonar Souncard
AC68 WLAN Card
multiple HDDs
one SSD

But it looks like our systems are completely different. When did you download the Image? have you already tried booting from DVD?
I checked the Installation Media before running the Installation and it showed no errors so i assume this is true...

I Managed to get further with the following settings:
[COLOR=#333333]Optimized defaults loaded, boot from DVD, only one HDD attached - no SSD, soundcard removed

Because I want ubuntu to be installed to my SSD i aborted then an since then never managed to get to that 3rd screen again :(

Edit: I'm using the 64bit Image though but same version

I'm currently thinking about trying to install ubuntu from within Windows...
I also opened an Ask-ubuntu-Question:
[/COLOR][/FONT][http://askubuntu.com/questions/430721/ubuntu-12-04-installation-hangs-after-first-two-screens](http://askubuntu.com/questions/430721/ubuntu-12-04-installation-hangs-after-first-two-screens)

---

### Post by mastablasta on 2014-03-07
> **princeofthecity said:**
> [COLOR=#333333][FONT=UbuntuRegular]Attempting to do a complete install of Ubuntu 12.04.4 LTS (32-bit) on my Asus Eee PC 1018P netbook with 2GB RAM, 250GB HD.

I created a bootable USB with LiLi and the Ubuntu 12.04.4 LTS iso and was able to successfully boot from the USB. However, at the point where I tell Ubuntu to actually install the OS (with checkboxes checked to install latest updates for flash etc and the checkbox checked for fluendo mp3) it seems to just hang with the spinning wheel going. I have the netbook plugged into a power source and the ethernet is also connected.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I let this happen overnight thinking I would wake up to the next step in the installation or just that it completed but it was still hanging. I was able to click out of the installer and the os was running, however, I believe it is just running directly from the USB stick and not from my netbook's HD. I also was able to open up Mozilla and get a webpage so I know the connectivity is there to allow the installer to download whatever updates it needed during installation.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Has anyone had this happen to them at all? I didn't see anything in the Eee PC installation documentation [here]("http://www.linuxliveusb.com/help/guide/step4").

have you tried to check that the image is good?
are you running installer inside live OS? are there any error messages?
if i understand you are installing 12.04 which iwll be the only os on the disk. is that correct' so you used first option to use the whole disk on install.

> 
Additionally, my second attempt seems to be yielding the same results - this time I created my bootable USB with LinuxLive (LiLi), in Step 4 I had the unchecked to Enable launching LinuxLive in Windows (requires internet to install) which, if I am reading the [documentation]("http://www.linuxliveusb.com/help/guide/step4") correctly, means Ubuntu will be virtualized when the machine is booted from the resulting bootable USB. I am trying to do a complete install, replacing Windows OS.
[/FONT][/COLOR]
that's not how that one works. what it does is create a folder on USB disk where it puts portable virtualbox. when you click virtualize this key in windows it iwll run the OS in windows inside virtualbox.

---

### Post by princeofthecity on 2014-03-07
> **mastablasta said:**
> have you tried to check that the image is good?
are you running installer inside live OS? are there any error messages?
if i understand you are installing 12.04 which iwll be the only os on the disk. is that correct' so you used first option to use the whole disk on install.

The first time I attempted the install, I realized I was running a live OS as I had the checkbox in Step 4 of the bootable USB creation in LiLi checked to Enable launching LinuxLive in Windows (requires internet to install).  The second time I recreated my bootable USB with that checkbox unchecked and got the same results only this time when I attempted to bail out of the install it looked like the OS wasn't as fully present (if that makes sense) as it appeared to be when I bailed out of the first install, which I think was running LinuxLive through virtualbox?

I may try creating a new bootable USB with a different USB stick and I will try grabbing a fresh 12.04 LTS image and see what happens.

If I am completely replacing my Windows 7 OS with Ubuntu I couldn't imagine anything Windows related interfering with my install so I think this may be either an issue with my USB stick or my 12.04 LTE image?

---

### Post by einfach3 on 2014-03-08
Hi again, I was able to solve the problem now, I downloaded the alterate-image which installed ubuntu right away.

Before this was working I also tried to install 13.10 which was only working if made it like this:
- open installer and click through until spinning wheel appeares
- while stil having the Installer opened mount some volumes from the HDD (can be anything, I just created an empty volume with gparted)
- close the installer and rerun, suddenly I was able to install....

Hope this information can help you solving the problem.

---

### Post by princeofthecity on 2014-03-08
I actually was able to install last night finally.  Here is what I did:

I booted up my machine from the USB created with LiLi just like previously, however, this time I figured I'd give the 64-bit iso a shot.  When I got to the first screen where Ubuntu asked me if I wanted to try Ubuntu or install it, I chose try.  Then, after playing around a little, testing ethernet wired connection in Mozilla, etc, I ran the launcher on the desktop to install Ubuntu and that actually worked.

Once I had the OS installed I shut down, removed USB from the left port and booted back up and I was good to go.  So far the only issues I had were the second updater for Broadcom wireless driver hung.  But it was weird, when I did a hard reboot it seems like the driver was actually installed and the system just wasn't able to tell me, and thus the download and install window just sat there with the spinning wheel.  I am able to connect to my wireless network and it seems to be working fine.

Can someone either tell me how to mark this post as Solved or just do it for me, as I don't think I have enought street-cred on here yet to do it myself.

---

### Post by BlinkinCat on 2014-03-08
Hi,

Here you go - [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Cheers - ;)

---

### Post by princeofthecity on 2014-03-10
Nice, thanks!

---

### Post by mastablasta on 2014-03-11
I am glad you solved it.

I would just like to comment on this in case anyone else comes to this thread:
> **princeofthecity said:**
>  The second time I recreated my bootable USB with that checkbox unchecked and got the same results only this time when I attempted to bail out of the install it looked like the OS wasn't as fully present (if that makes sense) as it appeared to be when I bailed out of the first install, which I think was running LinuxLive through virtualbox?


that action installs portable virtualbox on the USB key and you then indeed run the operating system isnide virtualbox. Which is a nice way of safely to show the oprating system on someone elses computer without rebooting their system.

---

