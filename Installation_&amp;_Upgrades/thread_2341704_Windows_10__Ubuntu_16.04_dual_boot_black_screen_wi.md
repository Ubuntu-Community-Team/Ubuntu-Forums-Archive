---
title: "Windows 10 | Ubuntu 16.04 dual boot black screen with hdmi connected monitor/nvidia"
date: 2016-10-30
forum: Installation &amp; Upgrades
---

### Post by austinj on 2016-10-30
[B]I'm trying to setup a dual boot with windows 10 and ubuntu 16.04 on a samsung ssd and UEFI bios. 

[/B]

[LIST]
[*]I created an Ubuntu flash drive with **rufus**.
[*]Once I select either "try Ubuntu" or "install Ubuntu" from the GRUB menu I get stuck on a black screen.
[*]My usb peripherals get power (light up) so I believe this is a problem with my asus monitor which is attached to an **nvidia gtx970** via **HDMI**.
[/LIST]

I don't have a DVI cable handy. Is there any other way to fix this and is the cable indeed the issue? 

thanks in advance!

---

### Post by oldfred on 2016-10-30
Often nomodeset required with nVidia cards/chips, until you install proprietary nVidia driver from repository.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

What brand/model system?
Gigabyte Z170 Nvidia 970 16.04   UEFI Settings required                         
 [http://askubuntu.com/questions/792012/nvidia-geforce-gtx970-problem-ubuntu-16-04](http://askubuntu.com/questions/792012/nvidia-geforce-gtx970-problem-ubuntu-16-04) 
    Asus z97-A with nVidia GTX 970 Maxwell Ubuntu  15.04
[http://askubuntu.com/questions/615896/ubuntu-15-04-uefi-cannot-install-blank-screen-no-signal?noredirect=1#615896](http://askubuntu.com/questions/615896/ubuntu-15-04-uefi-cannot-install-blank-screen-no-signal?noredirect=1#615896) 
   NVIDIA 970  with 14.04 - Bucky Ball
[https://ubuntuforums.org/showthread.php?t=2336142&p=13540433#post13540433](https://ubuntuforums.org/showthread.php?t=2336142&p=13540433#post13540433)

---

### Post by austinj on 2016-10-30
it's gigabyte. thanks, I'm trying it now!

worked. Thanks, I saw that solution but was so new I didn't know I could press "e" to make the change.

---

### Post by oldfred on 2016-10-31
You can change post to solved.

Did you have to make setting changes in UEFI/BIOS to have correct video work, like first example posted?

---

### Post by austinj on 2016-10-31
edited, just had to press e at grub and switch to "NOMODESET", didn't have to change anything in the bios. once I installed the nvidia drivers everything worked well.

---

