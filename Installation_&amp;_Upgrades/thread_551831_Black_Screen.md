---
title: "Black Screen"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by JohnnyTricksta on 2007-09-15
Hey guys,

I've seen similar problems as mine but I have yet to see a solution (or a solution that I could understand how to do). I downloaded ubuntu and restarted my computer to install it. After I hit install, it went to a black screen and quickly gave me two errors. I'm not able to catch all of it since it just flashes it quickly.

The first error is something about a BIO's bug (my bio's are up2date)
The second one is about a failing to allocate memory resources. 

It would then go to the next page where it checks everything and return a few more errors which I'm not able to catch. Then after that, the screen would go black.

So then I tried the alternate version. I popped it in and tried it out. It still showed me the same first two errors, but it installed fine with no errors. After it finished installing, it told me to reboot, which I did, then it came up with the same two errors again, then went the the ubuntu loading screen (the one with the scrolling bar). After that, it went black again.

Any ideas?

HP dv6000
2GBs RAM
NVIDIA GeForce Go 7200

Thanks!
Jordan

---

### Post by Pumalite on 2007-09-15
Check this:
[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

---

### Post by JohnnyTricksta on 2007-09-15
> **Pumalite said:**
> Check this:
[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)
Thanks for the link. However, I can't even get into Ubuntu. Right after the splash screen it goes black. When I push F6 it doesn't do anything

*EDIT* Also, when I boot using the noapic parameter, it doesn't help either

Any ideas?

---

### Post by Pumalite on 2007-09-15
Are you using the Alternate CD?
If you have finished installing and you end up with a black screen, maybe all you need is configure xserver.
Ctrl+Alt+F1 to get a command line, then:
sudo dpkg-reconfigure xserver-xorg, go with most defaults, choose 'vesa' as the driver. Then: startx.

---

### Post by JohnnyTricksta on 2007-09-15
> **Pumalite said:**
> Are you using the Alternate CD?
If you have finished installing and you end up with a black screen, maybe all you need is configure xserver.
Ctrl+Alt+F1 to get a command line, then:
sudo dpkg-reconfigure xserver-xorg, go with most defaults, choose 'vesa' as the driver. Then: startx.
Do I need to boot from the alternate cd? I was just booting from my HDD since I was able to install Ubuntu using the alternate cd. I just can't get past that splash screen

---

### Post by Pumalite on 2007-09-15
I you already installed Ubuntu; when you boot from hard drive and you get to black screen, then try my commands.

---

### Post by JohnnyTricksta on 2007-09-15
> **Pumalite said:**
> I you already installed Ubuntu; when you boot from hard drive and you get to black screen, then try my commands.
When I waited until the black screen it wouldn't do anything when I did the ctrl. + Alt. + delete. However, if I pushed it before the splash screen it looks like it's loading a bunch of things (I'm not sure what it's doing), but it still won't bring up a command line :(

---

### Post by Pumalite on 2007-09-15
It's Ctrl+Alt+F1

---

### Post by JohnnyTricksta on 2007-09-15
> **Pumalite said:**
> It's Ctrl+Alt+F1
Sorry, I meant to type that. I did do ctrl+alt+f1. I typed ctrl alt delete out of habit

---

### Post by Pumalite on 2007-09-15
You might not have your system installed. Let's see. Get a Knoppix: [http://www.knoppix.org/](http://www.knoppix.org/), boot from it (it mounts all partitions automatically) and see if you can get menu.lst
You will be as root: cat /boot/grub/menu.lst
Post it here.

---

