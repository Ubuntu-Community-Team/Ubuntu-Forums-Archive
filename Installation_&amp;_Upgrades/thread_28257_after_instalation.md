---
title: "after instalation"
date: 2005-04-19
forum: Installation &amp; Upgrades
---

### Post by areks on 2005-04-19
Hi 

I'm using Ubuntu now for 2 weeks. In general I like it very much, but I would like to ask few questions. Before I was using Mandrake (9.2 and 10) for nearly one year, and tested few other distributions (SuSe, Fedora, Xandros). 

First I would like to tell you about my installation experience. (Maybe it help you in next version.)

First I installed it on standard PC box. This was easy. Unfortunately everything except installation CD was commented out in source.list, so I was not able to add some basic (for me) elements (like Polish language support) after installation. Fortunately I tested before some Debian distributions so I know that to do.

Then I went for my laptop. It was more complicated. First I choose Polish as language for installation. Then installer could not understand why I want Polish language and London time zone. By going backward and forward I set it up to something but I end up in some more 'manual installation mode'. Somehow it happened that installer asked me about root password. It was mistake to set it up, as I was not able to do any administration task from my normal user, and was not able to login as root (with X server running). At this point reinstalling Ubuntu was the easiest option, as I don't remember how to administrate users from command line.
After setting it up like at office (in English), I got it running but with the smallest possible resolution. I found in forum how to edit xorg.conf for my laptop and now it is working without problem.

So it is working, but if this will be my first Linux distribution I will not be able to make it running. Also problems I got was strange for me. No distribution had problem with internationalization (except Xandros - but they make clear which languages they support). None had problem with my display on laptop.
On the other hand Ubuntu detected without problem my wireless network cards, both in PC and laptop, and only SuSe did it before.
So I think it is great Linux distribution, but not from users who just change from Windows.

I also think installer should have some option like 'use all Linux partitions'. It will be little help for this who change distribution, and have also Windows on computer. Other distributions have this, so testing them in more easy.

I must say that there is also many thinks I already love about Ubuntu. 
Debian packaging is brilliant idea. 
I love Nautilus. (The only think I liked in Windows was File Explorer. Konqueror was really annoying in KDE.)
... and much more little things.

------------------------------------------------------------

Now I try to customize it and if someone could help me with few little things I will be really thankful.

I'm wondering if in Gnome is anything like klipper from KDE. I know I can run it in Gnome (like any KDE application) but it will be nice to have something 'native' for Gnome.

In general where I could fund some list (with description) of Gnome utility applications - except Synaptic :)

Is it possible to make keyboard shortcut to star application? I would like to start terminal, nautilus, FireFox, etc. just by pressing some key combination.

Is it possible to have different background on different desktops? I would like to have black on one of them. I found it easier to work in Gimp if there is no background.

Thank you in advance
Arek

---

### Post by erkki70 on 2005-04-19
Hi,
Some stuff for you in order to customize. ;-)
[QUOTE=areks]I'm wondering if in Gnome is anything like klipper from KDE. I know I can run it in Gnome (like any KDE application) but it will be nice to have something 'native' for Gnome.[/QUOTE]
[http://gcm.sourceforge.net/](http://gcm.sourceforge.net/)
 
[QUOTE=areks] In general where I could fund some list (with description) of Gnome utility applications - except Synaptic :)[/QUOTE]
[http://en.wikipedia.org/wiki/List_of_GNOME_applications](http://en.wikipedia.org/wiki/List_of_GNOME_applications)
[http://www.gnomefiles.org/](http://www.gnomefiles.org/) (not supported but loads of stuff)

[QUOTE=areks] Is it possible to make keyboard shortcut to star application? I would like to start terminal, nautilus, FireFox, etc. just by pressing some key combination.[/QUOTE]
[http://foolish.fedorausers.org/gnome_keyboard_shortcuts/](http://foolish.fedorausers.org/gnome_keyboard_shortcuts/)

[QUOTE=areks] Is it possible to have different background on different desktops? I would like to have black on one of them. I found it easier to work in Gimp if there is no background.[/QUOTE]
[http://wallpapoz.sourceforge.net/](http://wallpapoz.sourceforge.net/)

Have fun and hope it helps.

Cheers,
Erkki

---

### Post by NaplesBill on 2005-04-19
I agree with you on the video issues with some systems.  The first motherboard I tried with ubuntu 5.04 did not work with the integrated video until I changed the xorg.conf to the 'vesa' driver.  I also had issues with integrated sound chips on both the original mb and the one I'm using now.  I think the ubuntu distro is great otherwise.

As far as Synaptic, I love it.  Just make sure you turn on the "universe" and "multiverse" repositories.  I had some trouble with dependencies before doing this step.  The search function, in Synaptic, has worked great too.  Just make sure you change the search "name" to "name and description" or something like that.

---

### Post by areks on 2005-04-20
> Have fun and hope it helps.

Yes. Thanks a lot. 

Arek

---

