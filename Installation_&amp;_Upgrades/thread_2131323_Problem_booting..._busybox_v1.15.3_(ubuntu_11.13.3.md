---
title: "Problem booting... busybox v1.15.3 (ubuntu 1:1.13.3-1ubuntu1)built_in shell(ash)"
date: 2013-04-01
forum: Installation &amp; Upgrades
---

### Post by DC80 on 2013-04-01
Hi all,

I have rather a strange problem. I would like to install ubuntu on a old pc (my quess is 2003) but this does not work. I don't know why. The computer is not able to boot from usb so I have to use a cd/dvdrom (live-cd) or PXE boot (which does not work either).

Like the title says, i'll end up on a text based screen with something about busybox and initramfs. There are commands built-in but non of them seems to trigger the installation from the live cd.

And now the strange part. Since i'm not able to use the usb version i have to use the dvdrom version. When i boot from dvd it starts and end up on the busybox screen asking about some commands. First i thought it was the hard drive not being flagged as bootable or something. So i downloaded Gparted and run that. I had the same problem with Gparted, however, Gparted gave me a little more information. It was screaming about a  "open" usb 1,1 port. Then it hitted me, I burned the .iso onto a usbdrive and plugged it in, booted up and it works, So, while not able to boot from usb, apparently it does work in combination with the live cd. 

So ubuntu booted up but i'm not seeing a startscreen if anything. Ubuntu seems to be started in a console but it does nothing. 

note: without the usb-drive i'm getting something like this:

(initramfs) there seems no medium that contains a live file system. 

Can someone help me please???

Kind regards,

DC80

---

