---
title: "Ubuntu VBox Full Screen Mode"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by TecWorx on 2010-05-04
I have Ubuntu 10.04 LTS installed in VirtualBox (3.1.6) as a guest OS. I've installed the latest Guest Additions. My Host OS is Linux Mint 8.

With a Windows Guest I can take advantage of the maximum resolution of my LCD monitor (1280 x 1024), and I can also move my mouse in between Guest and Host OSes. How do I accomplish this with an Ubuntu Guest? It does not recognize my monitor (HP 1740) and the maximum resolution available is 1366 x 768, which of course is applicable to a wide screen LCD. My monitor is square and I need the before-mentioned 1280 x 1024 setting. I've also activated the 3D setting in VBox, but it doesn't help.


Thanks

---

### Post by bmuluu on 2010-05-04
Start by installing Virtual Box guest additions in the guest OS.
Reboot after installing then try switching to full screen mode.

---

### Post by TecWorx on 2010-05-04
Thanks, but I already mentioned that I have installed the Guest Additions. Rebooting is a no-brainer - I've already done that.

---

### Post by HarvMan on 2010-05-07
Hi,
 
I am experiencing the exact same issue ... the only difference is my host OS is Windows XP.  All had worked just fine in Ubuntu 9.10.

---

### Post by madAndroid on 2010-05-09
I was experiencing this until I downloaded the VirtualBox Additions ISO under the downloads section on the VirtualBox website - VBoxGuestAdditions-3.1.7

hope this sorts the problem out for you too :D

---

### Post by HarvMan on 2010-05-09
Hi, thanks for the advice.  I downloaded Guest Additions 3.1.7 and still no improvement.

---

### Post by HarvMan on 2010-05-10
Hi, after further research I found this post #4: [http://ubuntuforums.org/showthread.php?t=1153853](http://ubuntuforums.org/showthread.php?t=1153853)

Essentially, I ran the following to install Guest Additions and the full screen option is now functional.
I have never done this before ... previously only used VirtualBox Devices > Install Guest Additions...
(the media was already mounted for VBOXADDITIONS_3.1.7_59409)

user@ubuntu:~$ sudo /media/cdrom0/VBoxLinuxAdditions-x86.run
Verifying archive integrity... All good.
Uncompressing VirtualBox 3.1.7 Guest Additions for Linux.........
VirtualBox Guest Additions installer
Removing installed version of VirtualBox Guest Additions...
tar: Record size = 8 blocks
Building the VirtualBox Guest Additions kernel modules
Building the main Guest Additions module ...done.
Building the shared folder support module ...done.
Building the OpenGL support module ...done.
Doing non-kernel setup of the Guest Additions ...done.
Starting the VirtualBox Guest Additions ...done.
Installing the Window System drivers
Installing experimental X.Org Server 1.7 modules ...done.
Setting up the Window System to use the Guest Additions ...done.
You may need to restart the hal service and the Window System (or just restart
the guest system) to enable the Guest Additions.
Installing graphics libraries and desktop services components ...done.

---

