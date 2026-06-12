---
title: "Unnecessary Kernel Modules"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by Sutur on 2007-11-07
Hi. I've gone through a lot of tutorials on how to speed up your boot times, tweak your system to free up resources etc.

For example, I found that reading NTFS filesystems through playing a track in XMMS actually used more than something like Firefox at times. So I reformatted in reiserfs and gained a boost! (And more probably)

However, I remember installing Slackware a few years ago and remembered it's impressive performance and weight. I also noticed that an lsmod on my system back then returned a couple of modules at best, whereas now with Ubuntu 7.10 it returns a list of modules too long to see in a full-screen console.

Does anyone know of a website or thread that lists what each module does, since modinfo isn't so descriptive and I haven't had much luck with google (oddly enough).

I think reducing the amount of modules running could free up a significant amount of resources. After all a faster, slacker kernel is better, right?

---

### Post by az on 2007-11-07
No, not really.  More things are loaded on-demand these days in comparison to a few years ago.  Back then, everything was compiled into the kernel and you needed intimate knowledge of your hardware to be able to install.  That also obliged the distribution to compile-in a ton of options - which leads to a fatter and possibly slower kernel.

Today, much of the kernel's functionality is loaded as needed.  This means that more modules are loaded but your kernel has fewer compiled-in options.  The result is that your kernel is as efficient as it can be today.

And whether rieserfs is more efficient depends on your needs.  I doubt you will see any performance difference between ext3 and reiser for normal desktop use.  Where Reiser is better is when your filesystem has millions of small files.

---

### Post by Sutur on 2007-11-07
> **az said:**
> And whether rieserfs is more efficient depends on your needs.  I doubt you will see any performance difference between ext3 and reiser for normal desktop use.  Where Reiser is better is when your filesystem has millions of small files.

I've always chosen reiserfs over ext3. A while back I did a lot of homework on forums, websites, tutorials and charts. In the end I decided reiserfs wiped the floor with ext3 but sadly for me, I don't remember why, so I look a fool!

Anyway I wasn't comparing it to ext3, it was NTFS! I'm sure you'll agree there's no comparison there :-)

Thank you for clearing up the module stuff for me. However, I'd still like an opportunity to remove a few modules that I wont need, and I'm sure there are few just by name I think I don't need.

But I'd rather know what they do before I flick any switches ;-)

---

### Post by Handssolow on 2007-11-07
> **az said:**
> No, not really.  More things are loaded on-demand these days in comparison to a few years ago.  Back then, everything was compiled into the kernel and you needed intimate knowledge of your hardware to be able to install.  That also obliged the distribution to compile-in a ton of options - which leads to a fatter and possibly slower kernel.

Today, much of the kernel's functionality is loaded as needed.  This means that more modules are loaded but your kernel has fewer compiled-in options.  The result is that your kernel is as efficient as it can be today.

And whether rieserfs is more efficient depends on your needs.  I doubt you will see any performance difference between ext3 and reiser for normal desktop use.  Where Reiser is better is when your filesystem has millions of small files.

Should I have any kernel modules loaded?
My Gutsy's Sytem log shows in  /var/log/messages the line
local host kernel: No module symbols loaded - kernel modules not enabled

Is it normal not to have any modules loaded?

Asrock 939Dual-VSTA AMD Athlon 64 x2 4200+ 
onboard ethernet Lan and C-Media CM6501 7.1 soundchip
Geforce 6600GT Nvidia based AGP video card
IDE HDrive with 2.6.22 -14-generic
Sata 64 bit currently disconnected

---

### Post by az on 2007-11-08
> **Handssolow said:**
> Should I have any kernel modules loaded?
My Gutsy's Sytem log shows in  /var/log/messages the line
local host kernel: No module symbols loaded - kernel modules not enabled

Is it normal not to have any modules loaded?

Asrock 939Dual-VSTA AMD Athlon 64 x2 4200+ 
onboard ethernet Lan and C-Media CM6501 7.1 soundchip
Geforce 6600GT Nvidia based AGP video card
IDE HDrive with 2.6.22 -14-generic
Sata 64 bit currently disconnected

To show the list or running modules, run:

lsmod

---

### Post by Handssolow on 2007-11-08
Thanks az
lsmod yields a long list of "modules" I assume that have been loaded.
What's the significance of the line No module symbols loaded - kernel modules not enabled

---

### Post by az on 2007-11-08
> **Handssolow said:**
> Thanks az
lsmod yields a long list of "modules" I assume that have been loaded.
What's the significance of the line No module symbols loaded - kernel modules not enabled

I think that's only one line of a multi-line message.  Can you show the ten lines before and after that line?

---

### Post by Handssolow on 2007-11-08
> **az said:**
> To show the list or running modules, run:

lsmod

Some lines in  /var/log/messages from my 32 bit Gutsy OS

Nov  8 17:01:01 localhost syslogd 1.4.1#21ubuntu3: restart.
Nov  8 17:01:01 localhost kernel: Inspecting /boot/System.map-2.6.22-14-generic
Nov  8 17:01:01 localhost kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Nov  8 17:01:01 localhost kernel: Symbols match kernel version 2.6.22.
Nov  8 17:01:01 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Nov  8 17:01:01 localhost kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
Nov  8 17:01:01 localhost kernel: [    0.000000] BIOS-provided physical RAM map:

Is it normal that no kernel modules are enabled at this early start of the boot up process?

---

### Post by az on 2007-11-09
It's not saying there are no kernel modules loaded.  It's saying that kernel debugging modules are not loaded so no debugging symbols are loaded.

---

### Post by Handssolow on 2007-11-09
Thanks az, seems rather obvious to me now!

---

