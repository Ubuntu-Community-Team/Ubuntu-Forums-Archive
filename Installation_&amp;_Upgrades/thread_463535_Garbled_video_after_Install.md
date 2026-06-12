---
title: "Garbled video after Install"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by GeorgeG5 on 2007-06-03
Hi all,

I have been trying to install Feisty on my Fujitsu Siemens celeron machine. Both Xubuntu and Ubuntu have the same problem but I have had Kubuntu working on there previously.

The problem is that the live CD comes up fine and install goes fine, on reboot the video is all horizontal bars, sort of interlaced and unreadable though you can see a mouse cursor jumping about as the mouse is moved.

Video is SIS memory sharing, other Linux/BSD (eg OpenSuse running fine) and microdollar stuff works fine and at no point in the install am I asked to select a video resolution (the panel is 1280x1024).

I am using the 386 version despite the processor actually being 64 bit but I think this should be OK.

Hoping someone can help and thanks in advance.

George

---

### Post by confused57 on 2007-06-03
> **GeorgeG5 said:**
> Hi all,

I have been trying to install Feisty on my Fujitsu Siemens celeron machine. Both Xubuntu and Ubuntu have the same problem but I have had Kubuntu working on there previously.

The problem is that the live CD comes up fine and install goes fine, on reboot the video is all horizontal bars, sort of interlaced and unreadable though you can see a mouse cursor jumping about as the mouse is moved.

Video is SIS memory sharing, other Linux/BSD (eg OpenSuse running fine) and microdollar stuff works fine and at no point in the install am I asked to select a video resolution (the panel is 1280x1024).

I am using the 386 version despite the processor actually being 64 bit but I think this should be OK.

Hoping someone can help and thanks in advance.

George
Boot into recovery mode, this should give you a console prompt, then type the command:
```
dpkg-reconfigure xserver-xorg
```

See this guide:
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

You would probably need to select the "sis" video driver...I believe for now that is the only thing you should change.

You could also boot into recovery and change the driver in your configuration file:
```
nano /etc/X11/xorg.conf
```
page down to the video driver section and change the driver to "sis", with the quotes.
Ctrl+X, Y, enter...this will save the setting.

Make sure it's a capital X and (one)(one)....

Enter "reboot", without quotes, to reboot your pc, or
shutdown -r now

---

### Post by TheNemeses on 2007-06-04
for me it says there is no such file as /etc/x11/xorg.conf when i do it, it tupoens up blank, what igves?

---

### Post by confused57 on 2007-06-04
> **TheNemeses said:**
> for me it says there is no such file as /etc/x11/xorg.conf when i do it, it tupoens up blank, what igves?
Read the last part of my reply again.
> Make sure it's a capital X and (one)(one)....

Enter "reboot", without quotes, to reboot your pc, or
shutdown -r now

Edit:  Added quote from previous reply.

---

### Post by GeorgeG5 on 2007-06-04
Thanks Confused,

That worked fine, I just did the xorg reconfigure and it's all fine and dandy.

Interesting though why the live disk selects a working config for the video but the installer writes something different.

George

---

