---
title: "&quot;VFS: Unable to mount root fs on unknown-block(0,0)&quot; during install"
date: 2017-02-10
forum: Installation &amp; Upgrades
---

### Post by kuroyuki4 on 2017-02-10
Hi everyone!

I'm having a small issue with my Ubuntu 16.04 USB installation disk. I'm trying to install it on an older desktop (Presario SR5333WM), and I get a kernel panic every single time, before it even reaches the Ubuntu splash screen.

I've also tried using a LiveCD with the same version burnt onto it. It didn't do anything different. Both are AMD64 (the CPU is also x64), and both of them seem to work on every other computer I've tested it on so far. Would anyone happen to know what the problem could be? I've even tried wiping the hard drive, with no success.

Specs:

256 MB DDR2 SDRAM
AMD Athlon 64 X2 5200+
Seagate ST3360320AS
Nvidia GeForce 6150SE (I'm not sure about this one)

I had to replace the RAM earlier this month, because the old one failed. I only had a 256 MB stick on-hand.

---

### Post by DuckHook on 2017-02-11
Welcome to the forums, kuroyuki4,

Your specs and especially the RAM are too under-powered for anything except possibly Lubuntu. It's the lightest-weight of all the 'buntus, but in all honesty, I doubt you will be happy even with Lubuntu unless you add more memory. You might wish to consider Puppy, Slitaz or Tiny Core, which are designed to run on very old or resource-limited systems.

However, lack of resources does not usually lead to kernel panics, so I would also suspect a HW issue. You mention past RAM issues . Have you checked to make sure the new RAM is okay? What about the RAM controller?

Another possibility is to forego a GUI altogether and run it as a server of some kind. Once you get rid of the GUI, your old desktop gets a new lease on life.

---

### Post by mörgæs on 2017-02-11
Agree with the post above: RAM is a severe limitation.

If you happen to find some more then the next problem is the 6150 graphics processor which needs special treatment. One way of dealing with it is to install Lubuntu and add closed-source drivers as soon as you get the option, that is during install and not after a reboot.

---

### Post by kuroyuki4 on 2017-02-11
I actually had plans to upgrade the hardware in the future. I was just testing to see if I could get any 'Buntu or other distro running on it.

The RAM I currently have installed seems to work just fine in Windows XP (the OS I have installed right now). The slot adjacent to it doesn't work though; the entire system spontaneously crashes if anything is plugged into it.

I'll definitely consider installing one of the OS's you suggested. Hopefully these will work just fine.

---

### Post by DuckHook on 2017-02-11
> **kuroyuki4 said:**
> …The slot adjacent to it doesn't work though; the entire system spontaneously crashes if anything is plugged into it.This suggests a wonky RAM subsystem. Linux access RAM differently than Windows, especially an OS as ancient as XP, so it is possible your kernel panic won't be solved with any distro. However, one of the many nice things about Linux is it's free. No issues trying out as many LiveUSB distros as you like.

Let us know how it goes.

---

### Post by kuroyuki4 on 2017-02-11
Interesting... I was always under the impression most operating systems accessed RAM in a similar fashion.

If that's the case, I might not get any distros working on it. Still, I'll try a few out and see if I have any luck getting one to run.

---

### Post by DuckHook on 2017-02-11
There will be a clear difference between 32-bit and 64-bit for example. They *must* use RAM differently if only because of the different address lengths. You might try a 32-bit Lubuntu to see if this makes a difference in stability.

---

### Post by kuroyuki4 on 2017-02-14
I just tried 32-bit Lubuntu to see if I would get better results. Nothing changed at all, unfortunately; it kernel panicked again, before it even loaded the installer.

---

