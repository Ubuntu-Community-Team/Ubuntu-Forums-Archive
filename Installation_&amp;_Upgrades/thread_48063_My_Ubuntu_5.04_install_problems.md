---
title: "My Ubuntu 5.04 install problems"
date: 2005-07-11
forum: Installation &amp; Upgrades
---

### Post by Aijaz Akhtar on 2005-07-11
I installed Unbuntu on Saturday, but it installed the base system only and later it never booted normally, just hanging or the screen was black after Grub booted. The rescue mode brought me to console all right, but startx etc did not work.
Yesterday again I attempted to boot Ubuntu in normal mode (Grub worked fine, I could boot into Windowsâ€™98 as well), and I reached a yellow screen this time, for the first time, but no log in or any thing. However As I found the LEDs showing busy, I attempted to hit Ctrl-Alt-F2, thinking that I would boot into root without password. But that did not work. And mind it, so far I had not selected any password for the root, but only for a user. So Sudo failed. Nevertheless, I ran xfree86, and it saved a conf file after it asked the name of the file. But nothing happened. Startx said, for the first time, Xserver already running (perhaps) at run level 0. I returned with Ctrl Alt F5 but nothing. But then when I hit Ctrl Alt F1, I was taken by surprise. Here there was a screenful of entries, installing this and setting up that, and in the end, â€˜Insert Ubuntu CD to install more packages.â€™ And when I followed these instructions, all went well and I got the login screen all right, and could log into my user name. Fortunately when I went to configure user names and passwords, it let me change the root password when it asked the password, I gave the userâ€™s that I was logged into). But later when I attempted to log off and log in as root, it did not allow me to log in as root at that log in screen. (This is the minus point to me, as all that configuration I cannot manage in console). All was working well, then I opened Kyneptic planning to experiment to install Abiword for which I had the rpm in a CD, and when I hit Add CD menu, it hanged. And after that it has never been possible to boot into X again.

---

### Post by Martin Witte on 2005-07-11
What video driver got installed, as to me this looks like a video driver issue. It seems the vesa driver supports most hardware, if that works try the driver for your video card. you can fd the video driver in file /etc/X11/xorg.conf, in ' Section "Device" '.

---

### Post by al7kz on 2005-07-11
Hi Aijaz:

"so far I had not selected any password for the root, but only for a user. So Sudo failed. "

When you sudo, user your user password, not root password.

al7kz

---

