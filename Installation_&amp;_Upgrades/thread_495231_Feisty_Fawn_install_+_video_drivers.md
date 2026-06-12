---
title: "Feisty Fawn install + video drivers"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by foxmuldr on 2007-07-07
When I boot from the Feisty Fawn CD it won't display anything on my Nvidia GeForce 8800GTX display unless I manually choose something like 1280 x 1024 x 32.  If I choose that value then it works just fine.  I'm posting this message from the Live CD boot right now.

After I install Ubuntu the loader comes up at boot-time.  If I choose Ubuntu and begin I can see the hard drive flashing, but the screen remains blank like it does if I don't choose 1280 x 1024 x 32 on the Live CD.

How can I fix this?  I tried "xforcevesa" but that did not help.  I really have no idea how to proceed.  I am a competent DOS + Windows user, but this is my first experience with Linux.  Please help. :D

Thank you.

---

### Post by ejw2076 on 2007-07-07
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Did you try envy?  that worked for me no problem.  I did end up having to reload my xorg conf file a couple times, but I got it going without any problems.

---

### Post by Pumalite on 2007-07-07
Try: sudo dpkg-reconfigure xserver-xorg

---

### Post by foxmuldr on 2007-07-07
> **ejw2076 said:**
> Did you try envy?  that worked for me no problem.  I did end up having to reload my xorg conf file a couple times, but I got it going without any problems.

Two things:
1)  When Ubuntu starts to boot, I don't see anything.  I have no idea how to get it into text mode or vesa mode or anything like that so it will at least boot and display something.  I'm totally new to Linux.

2)  I don't know what "reload my xorg conf file" means. :)  Right now I'm booting off the Live CD.  It seems like any changes I make to this version are lost each time I reboot.  My Ubuntu installation is installed onto a particular partition on my hard drive.  I can see the files there, but have no idea what needs to be updated.

I'm really a total newbie to Linux.  I think envy will do what I want.  I just don't know how to get to the point where I can see anything in the hard disk install of Ubuntu so I can do something.

- Rick

---

### Post by foxmuldr on 2007-07-07
> **Pumalite said:**
> Try: sudo dpkg-reconfigure xserver-xorg

I did that on the Live CD boot.  How do I get to a point where I can do it on the installed one where the screen comes up totally blank?

- Rick

---

### Post by Pumalite on 2007-07-07
Are you dual booting? With what? Did you check your iso ( Md5sum). Did you check CD for integrity before install? If dual booting with Vista, you have to do the partitioning from WITHIN Vista. How much memory do you have? If 256 MB RAM or less>'Alternate Xubuntu CD'

---

### Post by foxmuldr on 2007-07-07
> **Pumalite said:**
> Are you dual booting? With what? Did you check your iso ( Md5sum). Did you check CD for integrity before install? If dual booting with Vista, you have to do the partitioning from WITHIN Vista. How much memory do you have? If 256 MB RAM or less>'Alternate Xubuntu CD'

Everything is working fine.  I am dual booting with Vista's boot loader.  That part works just fine.

The problem I was having was with the display.  The screen was blank.  I've figured out that you need to boot in "recovery" mode to use "sudo dpkg-reconfigure xserver-xorg" if your screen is totally blank.  I had read somewhere else that Ctrl+Alt+F1 will bring up the terminal screen after xwindows is supposed to start (or something like that) where it could be typed in.  But, that didn't work for me.

After running sudo... it seems to work just fine.  I'm now using my Nvidia driver in 1920 x 1200 mode and it's great.  I can't get it to rotate to 1200 x 1920, but that's another problem for another thread.

FWIW, I think expecting someone to know how to get to a terminal, how to have any idea about xserver, xorg, sudo, anything like that, is too much.  It seems to me from these forums that video issues are a standard problem.  So, why not have it always default to VESA and then at least work, albeit very slowly compared to the real graphics driver?

Also, why not have some information on the main bootup window which says:  "If you have a blank screen during startup, try this one" and then it automatically defaults to VESA, just like the option on the Live CD menu has.  Just a thought.

I've heard so may good things about Ubuntu.  Once I've gotten the video issue thing figured out, I am finding out that I like it very much.  But up until that point, it was of no use.

I do appreciate your help.

---

