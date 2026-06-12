---
title: "Kernel panic on Feisty LiveCD"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by Kilnr on 2007-10-02
**UPDATE**: check out [the tenth post](http://ubuntuforums.org/showpost.php?p=3467256&postcount=10) for the last evolutions in finding the culprit!

**SOLVED**: read the last post on this page to see what I had to do to solve the problem.

-----

I got a new computer, and I wanted to install Feisty on it, but I got the following error messages:
```
Call Trace:

[<c0274eec>] pcibios_sort+0x5c/0x180
[<c01fc318>] pci_get_device+0x18/0x20
[<c03f9221>] pcibios_allocate_resources+0x21/0x150
[<c03fa6d9>] pcibios_init+0x79/0x90
[<c0100511>] init+0x111/0x330
[<c0103126>] ret_from_fork+0x6/0x20
[<c0100406>] init+0x0/0x330
[<c0100400>] init+0x0/0x330
[<c01044c7>] kernel_thread_helper+0x7/0x10

Code: $bunch_of_numbers

EIP: [<c00f0488>] 0xc00f0488 SS:ESP 0068:c18e5f30

<0>Kernel panic - not syncing: Attempted to kill init!
```

Things I've tried:
- CD check. Doesn't work, gives the same error message. However, I'm not sure if it's due to a faulty CD, because when using an old 6.06LTS CD, I don't get the same message, but my computer does lock up when loading hardware drivers.
- Memtest. Didn't show up with any errors, which was to be expected, since I'm running Windows XP on this computer as well.

What I suspect could be the problem is my graphics card, because of all the mentions of "pci" in the errors. It's an nVidia 8600GT PCI Express card, and I don't have any regular PCI cards in my computer, so that's what I suppose the errors are referring to. Does a PCI Express card require the alternate CD?

I'm really at a loss here. Hope someone can help.

My system specs:
P4 Prescott 3.0GHz HT
1024MB DDR2 RAM
MSI NX8600GT
IDE: 80GB drive and DVD-ROM
SATA: 160GB drive

---

### Post by Kilnr on 2007-10-02
Anyone?

I know I said I doubted the error being due to a faulty CD, but you never know. Is it possible to run a checksum against an already burned CD? My bandwith is very limited, so I'd rather not have to redownload the ISO.

---

### Post by picopir8 on 2007-10-02
Skip the Live CD and try the alternate CD.  Live CD struggles with hardware that it does not recognize (newer hardware not available when live CD was created), the alternate CD should at least limp along to get you installed and then download updates to get you totally up and running.

---

### Post by Kilnr on 2007-10-02
I'll give that a try. By the way, the CD wasn't faulty, I checked with the md5sums.txt file...

---

### Post by idkwot on 2007-10-02
hmm, i had this happen before but i cant remember what the problem was, ill let you know if i remember :[

---

### Post by Kilnr on 2007-10-02
Using the alternate CD gives the exact same error... Must be something with my hardware, then, but what? :confused:

(It's not the CD drive, I changed that already.)

---

### Post by Kilnr on 2007-10-02
I just downloaded the Gutsy beta, and unbelievably, I got the same error message. If it were due to too new hardware, one would think using Gutsy would've circumvented the problem... So what *is* the problem? :mad:

I really hope someone can help on this, I'm going crazy.

---

### Post by jfinkels on 2007-10-02
Hmmm...try taking out any cards plugged into your PCI ports. I have no idea if that will effect the kernel load, but give it a try...

---

### Post by Kilnr on 2007-10-03
So this time I actually managed to complete the installation. I added "pci=nosort" to the command line. With the LiveCD this didn't work (it locked up when it was loading hardware drivers), but it did with the Alternative CD. Strangely enough, when it was installed and I tried booting, my computer locked up, again at the loading of hardware drivers...

Could it help to add "pci=nosort" to the kernel options in the grub menu.lst?

Also, what does "pci=nosort" mean?

> **jfinkels said:**
> Hmmm...try taking out any cards plugged into your PCI ports. I have no idea if that will effect the kernel load, but give it a try...
Don't have any. :P

---

### Post by Kilnr on 2007-10-03
Major update! (Or at least, I feel I'm getting closer :))

I removed "quiet splash" from the kernel line in /boot/grub/menu.lst, so that I could see what was happening, and apparently where my computer got stuck was in a "sub-activity" of Loading Hardware Drivers, namely: "agpgart: Detected an Intel 915G chipset". This is strange, since in the BIOS I disabled the integrated video chip.

Perhaps I could have gotten answers sooner if I mentioned I had that chip, but there you go... :(

So how do I disable this chip for Ubuntu. Can it be done with a parameter on the kernel line in the grub config, or what?

[edit] A friend suggested I blacklist the integrated chip by adding the following to /etc/modprobe.d/blacklist

```

#blacklist intel onboard drivers
blacklist agpgart
blacklist intel_agp

```

I can't try it now, since I'm in class, but would this have a chance of working?

[edit] So **it worked**! I simply added those lines to the blacklist file and booted. Of course X crashed, but that was nothing a simple sudo dpkg-reconfigure xserver-xorg couldn't solve. :D

---

### Post by jfinkels on 2007-10-03
That's great news! I'm impressed by your tenacity and resourcefulness :D

---

### Post by Versusnja on 2007-10-07
Hi!

But where can I find this black list? And how can I add these lines to the black list?
I mean I'm installing from an alternate CD (Ubuntu 7.04). I boot to grub menu (the last working point) and I assume I must change something in booting parameters?...

My situation is 100% same: I disabled my Intel onboard video in BIOS and it is still being detected during loading drivers.
I started [another thread for it]("http://ubuntuforums.org/showthread.php?t=569659"), but this one now seems to cover quite the same issue.
I have nVidia 5700 AGP card and I can't figure out how can I blacklist the &^%$^%$ onboard video. :confused:

---

### Post by Kilnr on 2007-10-08
Sorry for the late reply. I already had a Windows XP partition on this box, so I used [_these drivers_](http://www.fs-driver.org/) to be able to access my ext3 partitions from within Windows. That's how I changed the blacklist. I suppose you also could use an Ubuntu Live CD, and mount the existing root partition.

[edit] About that last bit, what was I thinking, an Ubuntu Live CD won't boot... Some sort of terminal-only live cd, then, perhaps.

---

### Post by Versusnja on 2007-10-08
Thanks for the helpful reply. I'll try that now.

[SOLVED] Kilnr, you're my saver, man! :) At least I booted without errors. Now I will fight with reconfiguring xserver-org.

So, my problem was that Ubuntu installation detected my onboard Intel video instead of nVidia 5700 card despite the onboard video was disabled in BIOS.
My solution was:
1) installing from an alternate CD
2) installing the ext3 partition drivers in XP (10x Kilnr, see [this post]("http://ubuntuforums.org/showpost.php?p=3495117&postcount=13"))
3) blacklisting the Intel onboard video with a Notepad (see [this post]("http://ubuntuforums.org/showpost.php?p=3467256&postcount=10"))
and then I successfully booted to Linux.

---

### Post by Versusnja on 2007-10-09
Here is a complete solution for this problem:
[http://www.albertomilone.com/nvidia_intel_integrated.txt](http://www.albertomilone.com/nvidia_intel_integrated.txt)

---

### Post by Versusnja on 2008-02-29
After some mess with installing kubuntu and ubuntu 7.10 i foudn one more workaround to the onboard video problem.

Before installing Ubuntu press F6 twice and select "Expert mode". Go through the whole installation process. On some points questions may become too confusing - simply press enter to select default option.

Before selecting "Finish installation", choose "Execute shell".
Then
```

cd /target/etc/modeprobe.d
nano blacklist

```

and add the following lines to the end of the blacklist

```

#Disable / blacklist onboard Intel video
blacklist intel_agp
blacklist agpgart

```

Then press ^X, save the file and type exit to return to the installation.
Select "Finish installation", reboot without a CD.

It may happen (and it most probably will) that xserver won't start. Then enter dpkg-reconfigure xserver-xorg and reconfigure your xserver.
After that enter startx.

Hope this helps.

[EDIT] If you own a nVidia card. Try this [HOWTO configure nVidia]("http://www.albertomilone.com/nvidia_intel_integrated.txt").

---

