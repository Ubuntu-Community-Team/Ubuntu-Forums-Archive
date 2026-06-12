---
title: "Need serious help installing 10.04 onto my broken laptop"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by commander_fun on 2010-05-13
Hi,

I have a family member's old Dell 710m (x86 32-bit) laptop I'm trying to install Ubuntu 10.04 on and I'm finding out a lot of stuff does not work. [Disclaimer: I know basically nothing about hardware or troubleshooting these things beyond basic Google searches]

Booting from CD - I've tried several times and with 2 different drives; in all cases the installation process inevitably shuts the computer off midway, likely from overheating (the fan goes crazy). I've gone through Dell's boot utilities to test everything system-related (including fan/temp), and they all pass. More, running XP indefinitely does not overheat the computer, even running lots of apps. Apparently it's just a CD thing.

Booting from USB - Touch the USB port with a piece of metal on this thing and the computer immediately powers off. Uninstalling/reinstalling drivers does not help.

Booting from .iso in C:\ using UnetBootin - Gives the exact same error as in [this thread]("http://ubuntuforums.org/showthread.php?t=798992"), every time, no matter whether I choose "Live", "HD", "NetInstall" variants of 10.04 (I boot from disk, not usb obviously). Sadly the thread didn't conclude and Google turns up nothing else.

Possibly relevant: sound doesn't work (not sure if it's speakers or drivers, reinstalling them doesn't help); battery has about 10 seconds of life when unplugged.

Other than that, on XP things run basically okay I was just hoping to install Ubuntu and tinker on a busted old laptop. I've also freed up about half of the disk and defragged before attempting these things. I fully realize this may be more of a hardware issue than anything else but would still appreciate any input on what to do next.

Thanks for any help!

---

### Post by Rich930 on 2010-05-13
you could try wubi.

[http://wubi-installer.org/](http://wubi-installer.org/)

It's an installer that runs inside windows and installs ubuntu. It shouldn't throw up any problems like you've been having.

When you try to install from the CD - is it a CD-R/RW that you've burnt yourself? 
If it's stopping at the same place, is the disc damaged? Try re-burning it or burn another one.

---

### Post by commander_fun on 2010-05-13
> **Rich930 said:**
> you could try wubi.

[http://wubi-installer.org/](http://wubi-installer.org/)

It's an installer that runs inside windows and installs ubuntu. It shouldn't throw up any problems like you've been having.

When you try to install from the CD - is it a CD-R/RW that you've burnt yourself? 
If it's stopping at the same place, is the disc damaged? Try re-burning it or burn another one.

The CD was freshly burned on another computer and transferred directly to the Dell; the install was stopping at random points so I doubt it's an issue.

Just tried Wubi, it abruptly stops the machine in the boot-up process and the screen goes black. Power is still on but nothing is happening. I tried again but in 'verbose' mode, the last thing that happens in something about squashfs, which hangs, then init being shutdown (4 messages). Then some garbled colors flash on the screen and inert blackness.

**UPDATE: **I tried again in "safe graphics mode," now I see the "Installing system" dialog and progress bar. Crossing fingers!

---

### Post by Rich930 on 2010-05-13
glad to hear you're making progress! 
(for now)

hope it works ok in "safe graphics mode"

---

### Post by noisygecko on 2010-05-14
I am also having problems installing 10.04 on a Dell 710m laptop.  I was not able to boot off of 2 different CDs so I ran an upgrade from 9.10.  

The upgrade ran and everything seemed fine till I rebooted.  It goes to a blank screen after the Ubuntu boot screen that is after the GRUB login.

I am booting in "recovery," but I don't really know what to do...  It does come up with the "Recovery Menu".

Does anyone have any ideas on how to debug this?

---

### Post by noisygecko on 2010-05-14
I have been able to get the Dell 710m laptop to boot in recovery mode using the "failsafe x" mode.  So it looks like it is a X configuration problem.

But, when I try to reconfigure X or do anything like that, it doesn't seem to work.  What would be the best way of figuring out what is wrong?

---

### Post by Rich930 on 2010-05-15
> **noisygecko said:**
> I have been able to get the Dell 710m laptop to boot in recovery mode using the "failsafe x" mode.  So it looks like it is a X configuration problem.

But, when I try to reconfigure X or do anything like that, it doesn't seem to work.  What would be the best way of figuring out what is wrong?

Have you tried re-installing X?

[http://ubuntuforums.org/showthread.php?t=184965](http://ubuntuforums.org/showthread.php?t=184965)

---

### Post by noisygecko on 2010-05-15
> **Rich930 said:**
> Have you tried re-installing X?

[http://ubuntuforums.org/showthread.php?t=184965](http://ubuntuforums.org/showthread.php?t=184965)

I haven't tried re-installing X.  I tried reconfiguring it, but that didn't seem to even do anything.

It works with a previous version of the kernel, but not with the latest one.  So far I changed the grub entry to boot the other kernel.  I guess I had two kernels because of upgrading from 9.10.  I haven't had time to try much else.

---

### Post by Catharsis on 2010-05-16
You're suffering from a known issue on intel 855 graphics cards. See:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by noisygecko on 2010-05-16
> **Catharsis said:**
> You're suffering from a known issue on intel 855 graphics cards. See:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Does anyone know what is the preferred work-around for that?

I am currently doing "Workaround D: Use a kernel other than 2.6.32" by booting 2.6.31.

---

### Post by Catharsis on 2010-05-16
> **noisygecko said:**
> Does anyone know what is the preferred work-around for that?

I am currently doing "Workaround D: Use a kernel other than 2.6.32" by booting 2.6.31.

Workaround A should fix it. You can add the command through grub while booting to make sure it works before making the change permanent by entering the terminal comand if you want.

---

