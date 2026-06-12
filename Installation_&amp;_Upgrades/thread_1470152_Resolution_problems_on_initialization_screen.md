---
title: "Resolution problems on initialization screen"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by galvao on 2010-05-02
Greetings.

I did a dist-upgrade from Karmic to Lucid. Everything *seems* to be running OK, but there's one thing that's really nerve wrecking:

When I boot my computer, the "Loading" screen - before the splash screen where everything is initialized shows up - appears on an absurdly low resolution (not sure exactly which). So the graphics are awful, the text is too big and so on.

Aside from that, before the Loading screen shows up - right after "GRUB is loading" - a lot of characters (like plus signs) fill two lines of the screen. I think this might also be because of the resolution...

So bottom line is: 

1) Is there a way to fix this?
2) Should I be concerned enough to go with a full fresh install?

TIA,

---

### Post by kamikazepsi on 2010-05-02
try this

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

---

### Post by galvao on 2010-05-02
Thanks for the quick reply. I'm following those steps, but when I sudo update-grub2 I get this message:

cannot open `/boot/grub/video.lst' for reading: No such file or directory

May I proceed or I need to change something first?

---

### Post by Tynach on 2010-05-02
I THINK I had the same problem as you, but I'm not sure. At any rate, here's the guide that solved all my problems (and supered GRUB):

[http://lab.frontseed.com/entry/enable-frambeuffer-ubuntu-karmic-koala-using-grub2](http://lab.frontseed.com/entry/enable-frambeuffer-ubuntu-karmic-koala-using-grub2)

---

### Post by galvao on 2010-05-02
Well, thank you all for trying, but this is starting to make me nervous:
After applying the solution for video.lst found [here]("http://ubuntuforums.org/showthread.php?p=9087057"), I now get, after sudo update-grub2:

Generating grub.cfg ...
/usr/sbin/grub-probe: error: cannot stat `/boot/grub/locale'.
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.

So this is becoming too much of an annoyance to keep doing this and that. I'm really frustrated, I've been hearing for quite sometime that "dist-upgrade got a lot better and now you can do it without any problems", but the truth is that I'll spend the rest of my life doing damn fresh installs each time I have to upgrade Ubuntu.

Sorry, but I really needed to get that out of my chest. Here I go to yet another fresh install.

Thank you guys again for the help

---

### Post by Tynach on 2010-05-02
The problem isn't with the distupgrade. I had the same problem on both my laptop (dist-upgrade), and my desktop (fresh install so I could get 64-bit instead of 32-bit).

I didn't understand that first link, and I think maybe those steps might be a bit riskier (because they aren't explained very well). But the link I posted seemed to work well.

I'm duplicating the procedure on my laptop now, so I'll tell ya if it really is a problem with dist-upgrade or not.

---

