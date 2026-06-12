---
title: "ubuntu 10.10 fail to boot: Gave up waiting for root device"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by vivien_yan on 2010-10-24
Hi, I'm new to Ubuntu and I'm trying to install Ubuntu 10.10 64bit on my Dell Precision T7500.

After the installation, the computer tried to reboot but failed. the message I was getting was

Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
  -Check rootdelay= (did the system wait long enough?)
  -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! root=UUID=/... does not exist

I searched in the forums and found several threads asking for help on the same problem. Most of them seemed to be solved by changing root=UUID=/.... to root=/dev/sdXY in the grub.cfg file. I did the same thing but I still got the same message. Instead of saying root=UUID=/.... does not exist, now it says root=/dev/sdc1 does not exist.

I actually turned to Ubuntu 9.10 64bit and it worked perfectly. But then the same problem appeared when I tried to upgrade from 9.10 to 10.04. 

Can anyone help? Thanks!

---

### Post by banjo man on 2010-12-01
I'm running into this problem as well.

I have an IBM Netfinity 5600 eServer (dual P3) that I'm trying to get Ubuntu Server 10.10 i386 up and running on.

Previously I could boot the desktop version just fine (installed from the Alternate CD).

---

### Post by Cpl.Punishment on 2010-12-29
Did you ever get this resolved? I am having the same issue with 10.10.

---

### Post by Cpl.Punishment on 2010-12-29
My issue was resolved, so I thought I would mention it. I turned off my computer and unplugged my 2tb HD. I then turned on the computer without the drive. I turned it off again, plugged in the drive, and turned it on. My drive was recognized and booted into Ubuntu.

This may have been the case, and I think most people have this issue... httx://www.linux-radar.net/ubuntu-gave-waiting-root-device.html (replace the x with p, and paste it into your browser).

I wasn't sure if it is proper to paste a link to another site. I am sure I could find out if I re-read the rules.

---

