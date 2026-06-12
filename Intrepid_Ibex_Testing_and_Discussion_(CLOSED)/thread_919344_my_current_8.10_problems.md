---
title: "my current 8.10 problems"
date: 2008-09-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by listener on 2008-09-13
I would appreciate some advice, and possibly some help, on this issue.  I am quite new to Ubuntu and to Linux entirely.  I wanted to install onto my other machine, and with the alpha 4 available, it seemed like the thing to do - possibly a mistake as I've read some of the material on contributing, and honestly, I don't feel capable of contributing even bug reports very reliably, due to health issues and not always being available.

It has not been a mistake for ME, as I am loving it. I just have been wondering whether or not to try to see if others are having any of the issues I AM having, so they can be looked into.  Considering the updates I've received and some things I've seen in the logs, it looks like much of it is known.  Also, I'm not entirely familiar with what makes it completely Ubuntu for testing, but pretty sure that currently mine is NOT.  

The things I'm seeing are:
I must always boot with 'last good boot'.  Possibly related to a post I just saw regarding initrd.img not being in the current boot config.  
Neither screensaver nor monitor-suspend work.  At least, not monitor-suspend, it may be set before screensaver.  It goes off, comes right back.
I play music currently with Rhythmbox, using Alsa, and after a while, Rythymbox locks up, and no sound until I log out and back in.  No sound at all.

I am up on my updates, my NM is also current and working fine in static IP.  I do get lots of error messages in the logs which I don't understand really at all.  I have a computer background but with a lot of this type stuff, not really at all.

Thanks a lot, and I hope if I cannot follow up at least this is not a pain.  No complaints, just the best I can do with reports.  Lots of new stuff working great.

Bob

Setup is: AMD x2 processor 5600+, original model Asus M2V mobo
4gig ddr2
nVidia geForce 7600 (something like that)
Extra (generic) sata2 drive controller PCIEx1
Dual monitor
KVM switch / Logitech mouse working fine
... and I'm booting HD1 from grub on HD0
8.10 desktop

---

### Post by cariboo on 2008-09-13
> last good boot

I see it as the same thing as in windows where if you screw something up so badly that it won't start, at least you've got a way to get up and running again. Just use the regular start option.

Screensavers haven't worked for me for the last two alpha's, I think monitor power down is related.

When rhythmbox locks up, don't log out, try in a terminal:

```
sudo alsa reload
```

This will reload all the sound drivers.

With a lot of the error messages, if things are running ok just ignore them. If you want to know what is causing the error, remember Google is your friend. The error messages are logged, the logs are located in /var/log. If you really want to know what is happening, find an error message and paste it into a google search, you will more than likely find more responses than you really need.

Any bugs you find, get a login for [Launchpad]("https://bugs.launchpad.net/") and either search to see if there is a work around for it, or see if it has already been reported, and if it hasn't been reported, create a bug report.

Overall I have found Intrepid to be really stable once it is installed. There are a couple of things that didn't work right away during the installation, but it took less than 5 minutes to set things right

Jim

---

### Post by listener on 2008-09-13
Thanks a lot! 

As long as I know the second two issues are known, I don't worry.

I haven't been able to boot the regular way for quite some time.  It may be something about my setup, that's entirely possible.  But I've checked it all out, and everything is just the same except I'm loading the previous kernel release instead of the one ending in 3.  Although I have it.  There may be something with the actual Ubuntu config, but I really haven't tinkered with much there.  The partition uuids are the same, etc.

I am very happy to know that errors in the logs don't necessarily indicate problems.  I probably shouldn't even bother looking at them.  Sometimes they seem to indicate something I should correct, but I'm never sure.  Will use google more!

Thanks again

Bob

---

