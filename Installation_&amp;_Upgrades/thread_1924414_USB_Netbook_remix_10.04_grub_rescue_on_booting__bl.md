---
title: "USB Netbook remix 10.04 grub rescue on booting / blinking cursor"
date: 2012-02-12
forum: Installation &amp; Upgrades
---

### Post by tommyleinen on 2012-02-12
Hi there,

I have searched and found similar issues but so far no success in solving.... here is how I got into this position:

Netbook HP Compaq CQ10-500SA running Win 7. I wanted to run Ubuntu Netbook Remix (v10.04) off a USB stick, to keep the main OS intact. I then decided (probably stupidly), rather than use the full 8Gb Stick for UNR,  I would create 2 FAT32 partitions with gparted, so the first one can be used for storage (windows will only see the first partition), and the 2nd one would run the UNR OS.

I used a second usb version of UNR (which was created using usb-creator) to boot into the "install linux" option, and went ahead with the install process onto the 8GB USB stick, using the 2nd sdb partition. Firstly, I created a swap partition of ~1200Mb, then did the rest of the install as Ext3 to the rest of the free space.

On first run, the OS ran fine, I also rebooted and again it worked okay. However the wireless card was not working. I trawled for an answer and followed this procedure:

[https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html)

This is the last command I ran:

echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist

[FONT=Verdana]I then decided to reboot into windows as I couldn't work out the type of wireless card, and thought it would be easier to determine from device manager in windows.


Now when it boots up (without UNR usb) I first get the red compaq splash screen with the choice of hitting esc. for boot options, and I then get a black screen:
Grub loading.
error: no such device: 45229bb5-7a5b-4f3c-89d2-c9db5b2ffc8c.
grub rescue>_  [blinking cursor]
[/FONT]
If I try to boot from USB into linux, I simply get a blinking cursor directly after the compaq splash screen.

I have tried holding down space, shift, shift + e, but I am not able to do anything!


It appears Win 7 is still there intact (from running Win 7 Recovery disc), but the Grub is corrupt or something and will not allow either OS to boot. I just don't know what to do to solve! 

Apologies for the essay, but I think too much info is better than too little,

Any help is greatly appreciated. :confused:

---

### Post by tommyleinen on 2012-02-12
Found this [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

will post back with any results

---

### Post by tommyleinen on 2012-02-12
Fixed thanks to [talsemgeest]("http://ubuntuforums.org/member.php?u=397508") ! :popcorn:  Still have the wifi issue though but will tackle that another day.

---

### Post by tommyleinen on 2012-02-13
Wireless card issue solved by: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

followed the steps for STA.

---

