---
title: "Screen resolution problem Xubuntu 15.10"
date: 2017-02-07
forum: Installation &amp; Upgrades
---

### Post by carlos-aular on 2017-02-07
I've gone through the wiki and have followed the steps, yet my default screen resolution simply does not work. I don't know what i'm doing wrong...

Xorg.0.log = [http://pastebin.com/aPxPzasw](http://pastebin.com/aPxPzasw)
xorg.conf = [http://pastebin.com/KhQyKHLg](http://pastebin.com/KhQyKHLg)

---

### Post by Impavidus on 2017-02-07
Possibly related to the graphics driver, which is included in the kernel (or at least made for your kernel), which in turn is outdated as Xubuntu 15.10 is long end-of-life.

Can you check using a live disk of 16.04? Maybe even 16.10.

---

### Post by Bucky Ball on 2017-02-07
> **Impavidus said:**
> ... Xubuntu 15.10 is long end-of-life.

Welcome. As above. If you've just installed this, start again with 16.04 LTS and then post again if you have issues with that. It is a long-term support meaning it is supported for three years with Xubuntu until 2019. 16.10 is supported until the middle of this year (non-LTS has nine months support).

You generally won't get much help with an unsupported release. ;)

---

### Post by carlos-aular on 2017-02-08
I'm going to do a clean installation of Xubuntu 16.04 and then post the results.

---

### Post by Bucky Ball on 2017-02-08
Good plan. Let's hope the problems disappear. :)

---

### Post by carlos-aular on 2017-03-03
xorg.conf  deprecated...

> Custom configuration files follow this priority:  
[LIST]
[*]settings from /usr/share/X11/xorg.conf.d/ 
[*]udev rules (I'm not quite sure about udev priority, maybe less) 
[*]settings from /etc/X11/xorg.conf.d/ 
[*]settings in /etc/X11/xorg.conf 
[/LIST]
  where the good old, still supported xorg.conf has highest priority.  Therefore any rules you put in /usr/share/X11/xorg.conf.d/ loose  validity when other rules with a higher priority are found.  To define a custom configuration without xorg.conf file you need to  create a folder /etc/X11/xorg.conf.d/ where you put your custom device  configuration files in (here your 50-synaptics.conf). However any other  definitions in an existing xorg.conf file will override these, therefore  you need to remove your xorg.conf file.

After edit 10-monitor.conf file, the screen resolution works fine!

---

### Post by #&amp;thj^% on 2017-03-03
Just to add to this...for clairity.
    
To summarize, /etc/X11/xorg.conf isn't deprecated per se, but the process of explicitly generating or writing it is deprecated. You can still write a /etc/X11/xorg.conf if you need one, but most people don't need one.
I leave one in both> /etc/X11/xorg.conf....and> /etc/X11/xorg.conf.d/20-nvidia.conf.
That is just my way of setting up **custom** "conf files" 
Kind Regards

---

