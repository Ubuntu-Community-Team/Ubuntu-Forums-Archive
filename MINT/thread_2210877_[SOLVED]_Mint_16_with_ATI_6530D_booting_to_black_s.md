---
title: "[SOLVED] Mint 16 with ATI 6530D booting to black screen"
date: 2014-03-13
forum: MINT
---

### Post by Carl H on 2014-03-13
I have an ATI 6530D graphics card. A couple of months back I installed Mint 16 as a second distro to my Xubuntu 13.04 and got the notorious booting to a black screen problem. 

None of the the usual and well documented methods did anything other than vary the size of the font in the boot sequence.

I have eventually got it working, so in case it's useful to anyone else, this is how I did it.  (Not all my own work, it's based on a combination of things I found on the net and other forums)

1. Boot up and when the black screen appears, press some of the cursor keys and a box appears with an X server error.

2. Press CTRL + ALT + 1 to get a tty terminal.

3. Log in as root. The password is your own password that you set during installation.

4. Remove the Xorg drivers. 
```
 apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
```

5. Reboot

6. Repeat steps 1-3 

7. ```
apt-get update
```

8. ```
apt-get install fglrx-amdcccle-updates
```

9. ```
aticonfig --initial
```

10. Reboot.

All being well, you should now boot up into the Mint desktop. 

As Mint 16 is based on Ubuntu Saucy, then there's a chance that this might also work if you're strugging with a Saucy installation.

---

### Post by Carl H on 2014-07-05
The above also works for Ubuntu 14.04

---

### Post by Carl H on 2014-07-25
This also works for Linux Mint 17. If you boot the install CD with the 'Compatability Mode' option, you won't get the black screen and you can just open a terminal and enter the commands - no need to reboot after purging the X drivers either.

---

