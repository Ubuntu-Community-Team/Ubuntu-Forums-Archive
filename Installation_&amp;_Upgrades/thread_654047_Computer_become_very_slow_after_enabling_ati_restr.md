---
title: "Computer become very slow after enabling ati restricted driver."
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by zybrid on 2007-12-30
Hi!

Sorry for my bad English. 

After installing Ubuntu 7.10 32bit alternative on my computer which have a new Core2Quad 6600 (2.4hgz), i can´t seem to get the ati restricted driver to work. I have reinstalled the system 3-4 times and tried a couple of other solutions (ways of installing)

After fresh install of the OS, i run the system-update and update to the latest (around 168 updates)

I Reboot, everything works fine as usual. Surfing some websites with flash and so on. 
Ubuntu runs very fast.

When i active the ATI Restricted Driver, the program downloads the latest driver to me and installs it without problem.

When i have rebooted, the system is VERY slow. I can enter my loginname at GDM Login Screen, but its so slow.

After 2-4 minutes the gnome desktop appears and is very very very slow, like 2FPS or something.
I can´t seem to do any thing, only a hard reset works.
Well, i can get into console, but its 2minutes respondtime to every command.

It´s like running a vista on a pentium 100mhz. slooooooooooow!

---

I have tried reinstalling 2-6 times. 

I tried installing the binary drivers with some strange howto, it worked with compiz effects and so on, but it was kinda slow. Like Vista on a pentium 400mhz  :)

I tried installing the ati restricted driver BEFORE the big update, but that gets almost the same results

Worth mentioning is that i have installed the system exactly in the same way on a laptop and 2 desktops in my home.

For getting the compiz effects running on without errors the other computers i disable composite extension and installing xserver-xgl package.

I hope someone can help me! :(

I love ubuntu, but this problem isn´t for "all human beings"

Best Regards
Linus

---

### Post by oldsoundguy on 2007-12-30
I have had nothing but problems with ATI cards NOT doing what they are supposed to do when using the drivers FROM ATI.  So much that I have removed the ATI cards from my 3 Linux computers and put in nVidea cards, which WORK with both the Ubuntu drivers AND the nVidia sourced drivers! (and work BEAUTIFULLY!)
MAYBE ATI will catch up in the future, but at present, they are NOT there yet!

---

### Post by kellemes on 2007-12-31
Please look in /var/log/Xorg.0.log (after a problematic session)
There should be errors or warnings about your problem.

---

