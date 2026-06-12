---
title: "Xubuntu not recognizing all my RAM"
date: 2012-01-17
forum: Installation &amp; Upgrades
---

### Post by peyre on 2012-01-17
My computer came with 2GB of RAM (PC2 6400) on one stick, but the motherboard supports up to 4GB.  I bought a second 2GB stick (also PC2 6400) and installed it.  The BIOS recognizes all 4GB just fine, and during the RAM check it says it's running at dual channel interleaved.

However, when Xubuntu (v.11.10 32-bit) boots up, the task manager says I have _**2.5**_GB, of all things.  I expected to see either 3.5GB or 2GB--but 2.5GB?  That's just weird.  Anyone know what might be going on here?

---

### Post by Toz on 2012-01-17
32-bit OS'es (x86 architecture) are only capable of addressing 3GB of memory. To access all 4GB, you will need to either install the 64-bit version or install the PAE kernels. As to why its reporting only 2.5GB, is it possible that you have an integrated video card that using the missing .5 (or so) GB?

What do the following commands return:
```
free -m
```
```
lspci -vnn | grep -A10 VGA
```

---

### Post by peyre on 2012-01-18
Yikes!  I've never heard of a video card taking up 500MB of main system RAM, but well we've all been surprised before.  Here's my output:

```
leon@peyre:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2518       2037        480          0        665        574
-/+ buffers/cache:        798       1720
Swap:         2043          0       2043
leon@peyre:~$ lspci -vnn | grep -A10 VGA
01:00.0 VGA compatible controller [0300]: nVidia Corporation G94 [GeForce 9600 GT] [10de:0622] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device [1043:82ec]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at a0000000 (64-bit, prefetchable) [size=512M]
	Memory at d0000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at c000 [size=128]
	[virtual] Expansion ROM at d3000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia_current, nvidia_173, nouveau, nvidiafb

```

---

### Post by raja.genupula on 2012-01-18
Yeah your graphics drivers are taking 512 MB of RAM . I agree with Toz . to get your RAM completely better to install either 64-Bit OS or PAE kernels .
use this link for more information 
[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

All the best.

---

### Post by peyre on 2012-01-18
Ah!  Ok.

Now, 64-bit *buntu would give me the extra RAM between 3.5 and 4, I assume.  But any idea why my RAM showing now as 2.5 instead of 3?

I'll check out the PAE link.

---

### Post by KdotJ on 2012-01-18
> **peyre said:**
> Ah!  Ok.

Now, 64-bit *buntu would give me the extra RAM between 3.5 and 4, I assume.  But any idea why my RAM showing now as 2.5 instead of 3?

I'll check out the PAE link.

As said, 32bit can only address up to 3gb... which yours is, but the graphics card is taking up half a gig... hence showing as only 2.5gb

---

### Post by peyre on 2012-01-18
Wait, 32-bit OSs in general, or 32-bit *buntu specifically?  My understanding is that the RAM limit of 32-bit operating systems is 3.5GB.  My XP machine at work, and my wife's at home, show 3.5GB.  And now I've just booted my work machine with the Xubuntu disk, and [FONT="System"]free -m[/FONT] shows a total of 3.5GB:
```

         total    used     free   shared    buffers    cached
Mem:      3529     770     2758        0         94       448

```

I might very well be missing something here.  I'm just curious what it is.

---

### Post by raja.genupula on 2012-01-18
aah! you know guys this issue not leaving me alone . thats why i have googled but a solution  i've got regrading the limit of RAM .

[http://www.zdnet.com/blog/hardware/clearing-up-the-3264-bit-memory-limit-confusion/3124](http://www.zdnet.com/blog/hardware/clearing-up-the-3264-bit-memory-limit-confusion/3124)

---

### Post by peyre on 2012-01-18
Very good!  Manually installing PAE did the trick.  System Monitor is now showing 3.9GB of RAM (take that, Win32 users!).  For those who might not know such things--which included me until this morning--apparently PAE is an extension, for lack of a better word, to 32-bit kernels to allow them to handle up to 64GB.  It seems to be along the lines of "a workaround, rather than a fix".  The actual fix, of course, would be to use a full 64-bit OS--which I'll probably do next time I need to reinstall Xubuntu on this machine.

For anyone experiencing this issue, the instructions and background are available at Raja's link ([https://help.ubuntu.com/community/EnablingPAE]("https://help.ubuntu.com/community/EnablingPAE")).  Essentially, you do the following:

In a terminal window, enter 
[FONT="System"]**  grep --color=always -i PAE /proc/cpuinfo **[/FONT]
to check your processor's capability.  If you see [FONT="System"]**[COLOR="Red"]pae[/COLOR]**[/FONT] in there somewhere, your CPU will support PAE.  Move on to the next step.

Also in a terminal window, enter 
[FONT="System"]**  sudo aptitude install linux-generic-pae linux-headers-generic-pae**[/FONT]
and let it run.  A successful install should end without saying anything--you see lots of text scroll down, but no "I'm done" message.

Lastly, reboot.  You should now be able to use all your installed RAM.

---

