---
title: "linux-image-2.6.31-15 amd64 breaks grub2 and start up"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by masterpop on 2009-11-27
Hi,

After updating linux-headers-2.6.31-15 and restarting GRUB2 gave Error 15. Much googling I managed to re-install Grub2 and tweak the bios to correctly load. However, I now have a new problem...

in the boot sequence, i see the following:
1. GRUB loading
2. the white ubuntu logo for about 5 seconds
3. blank screen briefly
4. * Starting NTP server ntpd

then i get 

Ubuntu 9.10 masterpop-desktop tty1
masterpop-desktop login: _

at this point the system is stuck in a loop with the cursor jumping from the "login" place to the top left, and the entire screen flickers continuously.

Before updating the image, the load sequence was the same, but the tty1 screen only briefly came up before the ubuntu splash screen came on.

Anyone else experienced similar or have any idea how to solve it?

I have no option to Press ESC when GRUB Loading to try and load a previous image....

any help much appreciated.
thanks

---

### Post by Dambirds on 2009-11-28
I am having this same issue...

---

### Post by namok on 2009-11-28
Press Shift.

---

### Post by masterpop on 2009-11-28
It seems quite a few are having similar issues. I've come accross other threads related, best to follow this one as more details and ideas:

[http://ubuntuforums.org/showthread.php?t=1335464&page=3](http://ubuntuforums.org/showthread.php?t=1335464&page=3)

---

### Post by whitefort on 2009-11-28
Update gave me the same problem on both my laptops, but my desktops were OK.
Someone gave me this 'solution'

1.  Turn on computer
2 Press/hold shift to see the grub menu
3 Select the '14' kernel instead of the new '15'.

Ubuntu should boot just as it did before this wonderful update.

Then I downloaded startup manager from Synaptic, and set it to load the '14' kernel by default.

I've heard that the problem is because the video driver needs to be reinstalled after the kernel update, but this didn't fix the problem for me.

---

### Post by Dambirds on 2009-11-28
I get the same problems with booting 14  :(   can anyone tell me how I can reinstall the video driver from the terminal?

---

### Post by darkod on 2009-11-28
@dambirds
If you have Nvidia or ATI boot the recovery mode (with networking to have internet access) if possible and use EnvyNG. In terminal:
sudo apt-get install envyng-core envyng-qt

You can use it in text mode with:
envyng -t

The rest is easy. I installed the new driver without removing the current (the menu will give you the options). It worked straight away for me (my problem was not related to this original thread).

---

