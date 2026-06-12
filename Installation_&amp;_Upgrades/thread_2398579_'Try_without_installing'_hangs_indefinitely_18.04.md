---
title: "'Try without installing' hangs indefinitely 18.04?"
date: 2018-08-14
forum: Installation &amp; Upgrades
---

### Post by badprogrammer99 on 2018-08-14
I have an Alienware 15 r3 with windows 10, and I'm trying to dual boot it with Ubuntu 18.04. I used to have it dual-booted with Ubuntu 16.04,and it worked fine, but I had to send it in for some repairs, and they reinstalled Windows over everything. I created a bootable usb with Rufus and the amd64 iso, but whenever I boot from the usb, it hangs indefinitely on a splash screen. It has the Ubuntu logo and 5 dots, 4 of which turn orange before it hangs. I tried booting into text mode, and I get a bunch of messages of the form: "A start job is running for ____", where the blank is either Snappy Daemon, Disk Manager, Network Manager, or a few other things. After a few minutes those start jobs fail, and I get messages like: "Failed to start ____. See systemctl status ____.service" where the first blank is Snappy Daemon, etc, and the second blank is some service that relates to it (for Snappy Daemon it was snapd.service). It then stops and restarts those services and I get the errors again and again. I've let it run for about 20 minutes before losing hope that it was going to finish. A picture of the error messages is below. I don't know if I can open a terminal while it does this, so I think the only way to fix it would be a kernel boot option or something from the grub command line, but I'm not sure. Can anyone help me figure out how to boot into ubuntu from a live usb without this error? Thanks.[IMG]https://i.stack.imgur.com/yuGyu.jpg[/IMG]

---

### Post by ubfan1 on 2018-08-14
Do you have Nvidia video hardware?  Try editing the grub menu to add the word "nomodeset" to the line starting with "linux" at the "quiet splash" words.  If you install, your first boot will need the nomodeset too, until you update your packages and add the Nvidia proprietary drivers (Software and Updates/ Additional drivers tab).  Add the "universe" software source if it is not already checked.

---

### Post by badprogrammer99 on 2018-08-14
I probably should have stated what I've tried. I tried the nomodeset parameter and I got the same issue (it did work a while ago when I was installing 16.04). I've also tried to make Rufus do both the iso and the dd image. The dd image got a little bit further, but it still froze with the same messages.

---

### Post by ubfan1 on 2018-08-14
Lets eliminate a few other things:  Did you hashcheck the downloaded ISO?  Did you run a media check on the instal media?  Did you run a memory check (maybe the shop left a memory card loose)? Does the USB work on other machines?  Did you try the USB stick in another USB port?

---

### Post by Harist_Julianto on 2018-08-15
same problem with me. didnt work make live usb with latest Rufus either Etcher  for ubuntu 16.04.5 and 18.04 on my old Axioo notebook (nvidia 105m).  mybe because they are latest ubuntu?.

---

