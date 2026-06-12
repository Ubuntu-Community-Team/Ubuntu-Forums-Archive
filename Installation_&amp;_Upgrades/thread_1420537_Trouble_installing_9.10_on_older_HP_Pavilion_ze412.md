---
title: "Trouble installing 9.10 on older HP Pavilion ze4125"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by bishdogg on 2010-03-03
Hi, I'm fairly new to linux, but I have an old laptop that I'd like to bring back to life. I recently installed a new hard drive and now trying to install 9.10. However, when I select either the option to install ubuntu or run it from the cd, I get nothing but a blank screen. I even tried installing it under safe graphics mode but had the same result.

Any idea of what may be the problem or what I can do to start troubleshooting on my own?

Thanks

---

### Post by khelben1979 on 2010-03-03
Try an older version of Ubuntu to see if you manage to get it installed.

It's possible that the Linux kernel which is shipped with Ubuntu Karmic don't like the hardware in your laptop.

---

### Post by bishdogg on 2010-03-04
Ok, I might have to try installing an older version.

So far, I've been able to get ubuntu installed using the alternate cd. However, when the install rebooted I ended up with the same blank screen. After I had to restart the laptop I was presented with the GRUB menu, but then my keyboard wouldn't work at all for me to even select a menu option.

---

### Post by bishdogg on 2010-03-05
Thanks for the suggestion to try an older flavor. After a couple tries, I was able to get Jaunty Jackalope installed installed ok. In the end I had to install it without a network connection and then patch it after the fact.

Now I'm having trouble with my wireless card. It seems to be causing my laptop to freeze and I have to reboot it. Its a D-link dwl-650+ which I'm finding a lot of people have trouble getting to work correctly in linux.

---

### Post by khelben1979 on 2010-03-05
Do you have the possibility to disable the wireless network card or remove it?

---

### Post by bishdogg on 2010-03-05
Yes, I am able to remove it. The only way I'm able to connect to the internet is via a wired connection.

I'm going to try to follow this tutorial using the drivers for my card.

[http://www.uluga.ubuntuforums.org/showthread.php?t=324148&highlight=dwl+650](http://www.uluga.ubuntuforums.org/showthread.php?t=324148&highlight=dwl+650)

Post #79 seemed to be able to get this to work.

---

### Post by brucewagner on 2010-03-25
Ok, I did a Google search for:  HP Pavillion ze4125 Ubuntu

....and I found this thread.

So, of course, I'm dealing with the identical symptom.... once you select to "run ubuntu without changing the computer"... the little white underline curser for a few seconds... then a black screen.

SO...  

(1)   Is Jaunty Jackalope the final answer?

(2)   Did you have to upgrade the amount of memory, by the way?

( I really should learn to google these things BEFORE I begin attempting to install Ubuntu on old machines... )

---

