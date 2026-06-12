---
title: "Acer Aspire One 751h, Suspend, and a not-so-Lucid Lynx"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Mulenmar on 2010-03-27
Hello, I'm using an Acer Aspire One 751h with a fully-updated Ubuntu 10.04 beta. This netbook has the accursed US15W Poulsbo chipset -- yes, the one that hasn't been properly supported since Jaunty and required a hack for Karmic.:(

If I attempt to enter Suspend-to-RAM mode, it does so just fine -- but upon resume, the screen will not turn back on. Does anyone know how to fix this? I've already tried installing HAL, in the vain hope that some quirk would be detected to reactivate the screen on resume.

Also, the screen is stuck at 1024x768 resolution, but is capable of 1366x768. I have no difficulty working around this on Arch Linux, which still has a 915resolution-static package patched to support this chipset. I can just use that to temporarily patch the BIOS to add the 1366x768 resolution and use v86d to load uvesafb, and then use the framebuffer driver (not VESA) to get the full-but-unaccelerated resolution in Xorg. Problem is, 915resolution was "obsoleted" long ago in Ubuntu. :( How can get the full resolution on this netbook?

And a final note: the VESA driver for Xorg works properly, but is painfully slow on redraws, let alone Flash video playback. (Good thing I use Flashblock.) So I generated an Xorg.conf file and set it to use the FBDEV driver instead (slightly faster, don't know why.) This, however, causes an issue -- "FBDEV driver doesn't support EGA/VGA frames yet". Is this something that will be solved by release time, or am I doing it wrong? :p

---

### Post by Mulenmar on 2010-03-28
[This thread]("http://ubuntuforums.org/showthread.php?t=1428506") might be related to the Suspend-to-RAM issue on my AAO751h, although I suspect that even with whatever is causing this issue fixed, the PSB driver will be needed to make things work.

Just thought it worth mentioning, since someone might sucessfully port the driver eventually. Be nice to have one fewer roadblock on that. :popcorn:

---

### Post by jbernardo on 2010-03-28
With the GMA500 drivers (regular and iegd) not working on any recent xorg (after 1.6.x), your probabilities of having your netbook properly supported on anything more recent than ubuntu karmic or mandriva 2010.0 are very slim.
I have a asus 1101ha, and for now I am sticking with kubuntu karmic. At least it still has, besides the gma500 xorg drivers, lpia optimize builds, which means 10% more battery and 10% more speed.

---

### Post by Mulenmar on 2010-03-28
> **jbernardo said:**
> With the GMA500 drivers (regular and iegd) not working on any recent xorg (after 1.6.x), your probabilities of having your netbook properly supported on anything more recent than ubuntu karmic or mandriva 2010.0 are very slim.
I have a asus 1101ha, and for now I am sticking with kubuntu karmic. At least it still has, besides the gma500 xorg drivers, lpia optimize builds, which means 10% more battery and 10% more speed.

I'm aware of the Xorg version issue, but I remember somebody was working on porting the old driver (looking for the link now). IEGD doesn't work at all with suspend, from what I've read -- and is basically impossible to work with. :???: I've dug through the driver archive and (after about ten minutes) located the IEGD_10_Linux.zip file, but still got nowhere.

I'm very concerned about getting some sort of support for this US15W chipset in Lucid. This is a Long Term Support release, I'm sure Intel will eventually port their IEGD driver to Xorg 1.7, but in the meantime I'd at least like my full resolution, and that seems to require 915resolution. It's the ONE way I've found to get the full 1366x768 resolution without the drivers. 

And for the screen to be turned back on upon resume-from-suspend. :D I can live without suspend, especially with how fast Lucid boots, but the resolution issue is close to being a deal-breaker.

I'll be using Karmic or that ONE version of Moblin that supports IEGD if I can get it set up properly, but I'd still like to lend my meager help with Lucid. :KS


(And before somebody suggests it, I *would* go back to Arch, but I for one would like others to have a choice. Also, there is only one place left with the Xorg 1.6 PKGBUILDS, and it doesn't have xf86-video-fbdev)

---

### Post by Ibidem on 2010-04-10
After spending the afternoon hunting, patching, and attempting to compile grub2 with the 915resolution patch, I checked /boot and realized that -
GRUB 2, as shipped in Ubuntu, includes 915resolution.

---

### Post by Ibidem on 2010-04-14
Try adding to grub2's boot stanza-

insmod 915resolution
915resolution <mode to patch> <display options>
append to "linux ..." the option vga=xxx
Where xxx is the code for the mode that you would have used, had you not patched it.

Random complete BS example (IS NOT CORRECT):
#5c = 1024 x 768 x 16#NOT REALLY; CHECK)
915resolution 5c 1366 768 32
#Patched to 1366 x 768 x 32
    append to kernel line:
vga=791
#NOTE THAT 791 IS CODE FOR 1024 x 768 x 16, THE ORIGINAL RESOLUTION

---

### Post by cantun on 2010-04-20
Ibidem could you please give more detail please

---

### Post by Ibidem on 2010-04-20
First, I   read about it [here]("http://wiki.archlinux.org/index.php/Acer_Aspire_One#Using_intelfb_without_an_initrd"); I have never used 915resolution myself.
Another howto is for [gentoo]("http://forums.gentoo.org/viewtopic-t-117709-view-next.html?sid=0619090459a6c83c85b611d989ff443a").
I guess others can explain better, if they figured out how to do it.  The long and short is that you run 915resolution from grub via the commands
```
insmod 915resolution
915resolution <mode> <x> <y> [color_depth]
#Should look something like this with a GMA500: 
#915resolution 5c 1366 768 32
#Then you have a 1366x768x32bit resolution available, where vga=604 would be.
#For graphics in grub, you might do
set gfxmode=1366x768

```Afterwards, getting X to use the right resolution should be the same as usual for 915resolution.



To get the kernel to use an appropriate resolution, see the links.
If you substitute 1366 for 1024 and 768 for 600, it should work.
Extra kernel options might be like so: 
# video=vesafb:mode=1366x768-32 vga=604

Unfortunately (joke), I have a chipset that now works, and have not had to use these methods myself.  These are how I would try doing things if I didn't.
Ibidem

EDIT: Don't expect suspend to work properly if you use 915resolution.
It relies on changing the resolution BEFORE X starts; a suspend/resume may "fix"  the patched graphics mode, which would mean that there is no way to safely resume, except perhaps switching to a "standard" resolution before suspend.
Hibernate might work, since you will patch the gfx mode BEFORE booting.

If the thread could be moved to "support", that might be good for those with similar hardware.

---

### Post by shaoxuan on 2010-04-25
Hi, I have tried the option Ibidem had proposed, and yes, it works!

The resolution of Acer Aspire One 751h is now 1366*768, but without 2D or 3D acceleration (without PSB driver, that's for sure...).

I have append these code in the /boot/grub/grub.cfg file:

```
insmod 915resolution
915resolution 5c 1366 768
set gfxmode=1366x768
```

---

### Post by nekr0z on 2010-04-29
Has anybody figured out how to make suspend work with this great method? Because every time my machine wakes from suspend, X is killed and all the unsaved work goes to /dev/null, which makes suspend useless and dangerous and life much harder.

---

