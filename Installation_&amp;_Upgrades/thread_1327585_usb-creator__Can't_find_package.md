---
title: "usb-creator : Can't find package"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by amosmj on 2009-11-15
I just got a netbook for my wife and despite my best efforts, it has XP on it. I'm trying to put Ubuntu on it and need to do so with a USB drive. I'm using my own laptop which features Ubuntu to set up the install. I'm following the instructions from the Netbook install page ([https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)) and it says to use the command line "sudo apt-get install usb-creator". When I run this I get "Couldn't find package usb-creator".

I've looked under add and remove for the correct app and don't see it. I'm running 8.04 on this computer. What is it that I'm overlooking and need to do to make this happen?

---

### Post by darkod on 2009-11-15
usb-creator was only introduced in 9.04 and later I believe.

You could create the USB stick on the XP netbook, I know very easy way to get it ready in windows.

But before that, my personal recommendation is to download both UNR and desktop 32bit images. Put first one on the usb stick, try it with Try ubuntu option, and then the same for the other. I am saying this because UNR (Netbook Remix) has different layout of menus, etc that you might find strange. I went directly for UNR for my netbook and two days later installed desktop 32bit over it. :)

---

### Post by darkod on 2009-11-15
Instructions for usb stick in windows:
1. Google and download software called unetbootin. It's free.
2. Download the ubuntu ISO (or more of them) that you want.
3. Start unetbooin and in ISO part select the iso you like to use.
4. In the bottom part select your usb stick windows letter.
5. Click on OK (I think) and it's done.
6. When asked do not reboot, no need, just close unetbootin.

Very IMPORTANT: Unetbootin will overwrite the ubuntu menu. To enable the ubuntu menu do:
1. Open the stick and in the root find and rename syslinux.cfg to syslinux.old
2. In folder isolinux find and rename isolinux.bin to syslinux.bin, isolinux.cfg to syslinux.cfg
3. Go back and rename the whole folder isolinux to syslinux

You will now be able to boot with that stick and get the standard ubuntu menu at start. Keep it safe. :)

---

### Post by amosmj on 2009-11-15
Darkrod, that worked like a charm. The first time I tried changing all the file names it told me it couldn't find the kernel. I tried it without and everything installed wonderfully. The menu looked pretty close to what I'm used to so it went well. I used the Netbook install because I had it handy but I've told my wife that if she wants a more windows like experience I can install the desktop version. So far, so good. She's currently working her way through the games folder, I think I'm in trouble for not having mentioned it sooner. :)
Thanks again

I'm not sure how to mark this as solved but it is definitely solved. Thank you.

---

