---
title: "&quot;Restricted&quot; video driver lost my screen resolutions?"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by bsmith1051 on 2007-04-24
I have a clean and brand-new installation of 7.04 on my Athlon XP machine, with an Nvidia MX400 PCI video-card.  After the initial install I had the correct 1280x1024 resolution but I wanted to try the new "Restricted Drivers Manager" feature.  So I simply enabled the checkbox for "Nvidia Accelerated Video Driver" and rebooted.  The system came-up at 640x480 and with no other options.  So I disabled the 'restricted' driver and rebooted, thinking that this would return my original configuration -- it didn't.  Now I'm stuck at 800x600.  

What's up with this?  It seems pretty piss poor that installing, then immediately uninstalling something doesn't restore the original state.

I've tried searching the forums but, of course, there are a million posts all talking about hand-editing the Xorg.conf file which I thought the new feature was supposed to avoid....

---

### Post by ABCC on 2007-04-24
Ah, I may know what is going wrong. 

That's quite an old video card you have, it could be that youre now using the wrong driver for it. The restricted driver manager merely autoinstalls the newer nvidia driver. There is an nvidia-legacy driver in the repositories which may solve your woes. 

Another thing to look into is your /etc/X11/xorg.conf file. If you want to check that it works without the nvidia driver make sure that it contains the following:

Section "Device"
      Driver      "nv"

Section "Screen"
                Modes           "1280x1024"     "1280x960"      "1152x864"      "1024x768"      "800x600"       "720x400"       "640x480"

In the Modes line, make sure that the highest resolution is the highest one you wish to use.

HTH

ABCC


 'driver' option is set to "nv" and that your resolution is contained in the

---

### Post by helliewm on 2007-04-25
I have exactly the same problem with a nvivida 6100 graphics card which is a new one not a legacy one. Is this a bug?

---

### Post by louistan3 on 2007-04-25
did u guys try doing a reconfigure?

shutdown gnome with 
```
sudo /etc/init.d/gdm stop
```

then reconfigure with
 ```
sudo dpkg-reconfigure xserver-xorg
```

and i believe before it ends it asks to set monitor settings.. 

i suggest doing at least the medium and then select your monitor resolution from the list

hope this helps
:)

---

### Post by ABCC on 2007-04-25
> **helliewm said:**
> I have exactly the same problem with a nvivida 6100 graphics card which is a new one not a legacy one. Is this a bug?

What exactly is going wrong on your pc, are you also stuck at 640x480? And what resolution are you trying to run it at?

With a 6100 card you shouldn't need the nvidia-legacy drivers. It's worth trying to reconfigure your X server the way louistan suggested, personally I like to take a look at it myself before I run any xorg configurator. If you're unsure what it all mean, feel free to post it here. 

HTH

ABCC

---

### Post by helliewm on 2007-04-25
Reconfiguring crashed xorg. And I could not type anything into the Console, my keyboard would not work.

Yes I was stuck at the same resolution as the person in the firstpost, I now need to do a fresh install of Ubuntu but am taking a look sabayon first .

Spent all morning messing around on this:( 

Helen

---

### Post by willcox on 2007-04-25
Hi there!
The same problem was here... You may want to read this,  and everything is OK:
[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)

---

### Post by bsmith1051 on 2007-04-25
How about the OS is improved so as to not self-implode, instead....

On a related note, I just tried booting-up my old Ubuntu install (v6.06 and expecting an Nvidia MX2) on this same computer and -- again -- it doesn't know how to handle the video.  I'd hoped that since it was still an old gen Nvidia that the old setup would work seamlessly on the new card but instead I get 'x server unable to start' and I'm dumped to a command-line.

**Windows is far more robust than this.**

---

### Post by medya on 2007-04-25
[read this ]("http://blog.shevin.info/2007/04/dont-panic-if-you-broke-graphic-in.html")

---

