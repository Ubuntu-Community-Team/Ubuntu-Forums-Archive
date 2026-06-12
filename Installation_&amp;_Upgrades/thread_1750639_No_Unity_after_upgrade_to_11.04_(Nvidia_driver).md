---
title: "No Unity after upgrade to 11.04 (Nvidia driver)"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by anthonyvo on 2011-05-05
I was running 10.10 with an Nvidia Quadro FX1500 and was able to get the effects (Compiz) working after following the manual driver install (found [here]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html")) and editing my xorg.conf file (read about it [here]("http://ubuntuforums.org/showthread.php?t=1659556").)

After this upgrade, Xserver (my desktop) wouldn't even launch. It just kept going into a terminal for log in. Not bad - better than not being to do anything at all.

I removed all my nvidia drivers
```
sudo apt-get remove --purge nvidia-*
```
and then created a new xorg.conf file (and later moved to /etc/X11) using
```
Xorg -configure
```

That now allows me to log in to my desktop. However - no Unity. I've read that some people have had luck with the Nvidia 173 drivers, but not here.

When I downloaded the current nvidia driver for my card (Quadro FX 1500) from nvidia, and went to install it manually using (from the directory where the download is)
```
sudo sh NVIDIA-Linux-x86-270.41.06.run
```
Eventually, it errors out with this:
> 
The compiler used to compile the kernel (gcc4.4) does not exactly match the current compiler (gcc4.5)...


Any ideas? 

For the record, I can't boot from a thumb drive ("boot error") or CD (both were created and tested on a Windows 7 machine.)

-Anthony

---

### Post by anthonyvo on 2011-05-06
Just a quick update: Now that I have my desktop back (albeit in Classic with no effects) I'm going to try to create a LiveCD here in Ubuntu and do a fresh install.

Stop me if I'm barking up the wrong tree.

-Anthony

---

### Post by Hedgehog1 on 2011-05-06
A clean install is always a safe bet.

Umm... Don't forget to backup your files.

Do you have a separate '/home' partition?

***The Hedge***

:KS

---

### Post by anthonyvo on 2011-05-06
Thanks. I have everything backed up on a separate drive (automatically every 7 days) and online.

I don't have a separate home directory, but will create one for this new install. I don't want to go through this again.

I'll let you know how it goes. Just tested the new LiveCD (thumb drive) I created in Ubuntu and it works like a charm (using it now as I type.)

Cross your fingers and pray to the Canonical gods for me...

-Anthony

---

### Post by dino99 on 2011-05-06
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by anthonyvo on 2011-05-06
hey thanks for that link! very helpful moving forward.

---

### Post by anthonyvo on 2011-05-06
Success! Kinda...

After the clean install, I booted up and got the "Cannot display this video mode" (or something along those lines) After a few seconds, it disappeared and I got the login screen. I logged in, got the message that I can't run Unity, and installed all the updates it prompted me to install...

It said there were proprietary drivers available and so I installed the Nvidia-173 driver (because I had read some had success with it.) Well, after installation and another reboot, I finally have Unity!

The bad news is that it's in 640x480 resolution! Baby steps I guess...

-Anthony

---

### Post by anthonyvo on 2011-05-06
So, I did another clean install (instead of just removing the Nvidia-173 driver - just to make sure nothing lingering,) and this time I installed the Ubuntu updates (did not require restart) and then, this time around, chose Nvidia-current and BOOM!

Got Unity and in my monitor's resolution!

Now - to catch up with 3 days of work.

Thank you!

-Anthony

P.S. For the record, a day or two ago there were no Ubuntu updates, so perhaps something was updated to allow the nvidia drivers to finally work. I don't know, but just happy it's working now.

---

