---
title: "Upgrade to Ubuntu 10.10 from 9.10 (Karmic)"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by wannahavelinux on 2010-10-25
Hi,

My environment

Dell Inspiron 700M (Intel 755GM Graphics), 2GB RAM
Connected to Vizio 50" Plasma

I was running 9.10 just fine with TV at 1360x768 resolution and Laptop with 1200x800 resolution. I was able to turn off laptop screen using xrandr or lxrandr.

Yesterday I did a fresh install of 10.10. I am facing a couple of issues:

1. Both laptop and TV can run only at 1024x768.
2. Xarndr/lxrandr cannot find any displays. I ran X -reconfigure and copied xorg.conf to /etc/X11. It now sees only one display as unknown and 1360x768 now only covers 75% of the TV screen and laptop cannot got to 1200x800. I cannot turn off laptop screen.
3. I keep on getting logged out randomly every few minutes.

Are there any known issues with newer version and older hardware? Should I go back to 9.10?

Help is much appreciated.

Thanks,

---

### Post by mörgæs on 2010-10-25
Hi, welcome to the forum.

Have you tried 10.04?

---

### Post by wannahavelinux on 2010-10-25
Thanks. 10.04 CD starts to bootup, does lot of cd reads and then later on gives me a baln screen. I then used alternate cd to text based install. When 10.04 got installed and it rebooted, I got the same blank screen again (during OS boot). So definitely, 10.04 has issues too :(.
 
 
> **mörgæs said:**
> Hi, welcome to the forum.
 
Have you tried 10.04?

---

### Post by sikander3786 on 2010-10-25
Going back to 9.10 is not advised as support is scheduled to end soon, less that 5 months. You'll have to do a fresh install then so why not now.

> I got the same blank screen again (during OS boot

Yes, that is a known problem with Lucid. See here for a workaround.

[http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)

Try to boot of an Ubuntu 10.04 Live CD and add the nomodeset paramater by pressing any key just after the computer starts booting from the CD. After you see a menu containing "Try Ubuntu" and "Install", press F6 and select nomodeset and continue booting. It will surely take you to the desktop where you can test your hardware with 10.04.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

What is your current setup? Did you wipe 10.04 and installed 10.10? Do you want the issues in your 1st post to be addressed or the one's regarding 10.04?

---

### Post by Sylslay on 2010-10-25
try 10.04.1, best linux at the moment, 

and workaround the black screen wtih something like:

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
:guitar:

PS . 
Not supirse with 9.10 -> 10.10.

---

### Post by wannahavelinux on 2010-10-25
Thanks Sylslay and Sikander3786. I will try 10.04 and report back. Right now playing a little more with 10.10 before giving up :)

---

### Post by wannahavelinux on 2010-10-26
Ok, so here is what I was able to do so far. On 10.10, I ran X -configure to create xorg.conf and i915.modeset=1 in kernel command line and was able to see two displays. But if I make the 2 displays different and make my external monitor to be 1360x768, it seems it only shows 1024 pixels in width and then rest of the screen on the monitor is blank. Moving the mouse in blank area, actually takes the cursor to laptop screen, suggesting that laptop screen overlapping starts at 1025th pixel onwards. I tried dragging the laptop before external monitor or below/above the external, monitor, but applying changes brings the laptop screen back to right of external monitor :(.

On Lucid (10.04.1), I was at least able to go beyond blank screen with i915.modeset=1. With nomodeset or i915.modeset=0 or any other combination of the 2, the laptop will power off on its ownas soon as it starts beyond changing the option. With i915.modeset=1, there was lot of flicker on external monitor. The install started but the laptop got hung towards the end. I am not sure, if the hang was due to screen going blank (no keyboard activity) or thew screen went blank due to laptop got hung. I let it sit on the blank screen for an hour so that if install is going on behind the scene, it will finish and then I rebooted the laptop. No good. It didn't even start to boot for me to add i915.modeset=1 again on the installed kernel.

At this point I have reinstalled 9.10 (karmic) again. Will retry when it goes out of support :(. However, if you have any suggestions for me to try, I can try with live cd.

Thanks

---

### Post by mörgæs on 2010-10-26
Using 9.10 is not a bad option. It is a great release, and I will use it myself till support runs out. 

If you have the space, you could install one of the other releases (or 11.04 alpha/beta, when that time comes) for experimenting and still have a working 9.10.

---

