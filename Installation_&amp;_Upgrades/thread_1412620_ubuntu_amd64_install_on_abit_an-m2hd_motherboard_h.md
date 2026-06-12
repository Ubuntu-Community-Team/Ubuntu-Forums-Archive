---
title: "ubuntu amd64 install on abit an-m2hd motherboard hangs"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by Jay Christnach on 2010-02-21
hello dear linux users,

I tried to install ubuntu on the system mentioned above. I already suspected that there would be issues because of the onboard graphic and sound. Well I have a Gentoo distro running on that machine, but only with normal vga video and a soundblaster for my sound. I got a bit tired of configuring gentoo and wanted to give ubuntu a try.

What I found out until now:
Using the expert mode and the text only installer I saw that the hang occurs after the kernel set up usb drivers. (the normal installation hangs with a prompt at the top left of a black console screen, no cation on the disks anymore)
So I tried the install once again with the nousb option and I got the base system installed. Unfortunately the only ps/2 keyboard I still have has some keys that are out of order and now I can't use my usb keyboard.

Maybe I will borrow a ps/2 keyboard or perhaps someone can explain how to load the corresponding modules at boot. I can access the /etc files from my gentoo distro. I suspect that the problem with usb is that there are two flavors (ohci and ehci if i'm right) and the two get loaded instead of just the right one.

The second issue is the graphics which is an nvidia I got working perfectly with the proprietary driver from nvidia. I have the blinking color garbage screen which is described elsewhere on this forum. So I guess I'll have to install this module manually.

My former distro rather long ago was a debian, and I knew the system very well. But any help from here would be greatly appreciated since it could speed up things a bit. I did some searches about my install problem and found nothing useful, so I want to share the experience on this forum.

kind regards

---

### Post by Jay Christnach on 2010-02-22
I removed the nousb boot option in the grub menu.lst just to see what happens and the systems boots normally now! So the problem with usb only occurs with the kernel from the installation cd.
Now on to the graphics problem. I hope a apt-get install will do.
Another strange thing is that the console's cursor is blinking at position 0,0 in the upper left corner and doesn't move when I type.

greetings

---

