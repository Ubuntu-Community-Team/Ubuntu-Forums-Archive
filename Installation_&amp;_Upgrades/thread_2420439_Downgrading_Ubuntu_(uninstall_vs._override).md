---
title: "Downgrading Ubuntu (uninstall vs. override)"
date: 2019-06-05
forum: Installation &amp; Upgrades
---

### Post by seeminglyhuman on 2019-06-05
I'm new to Ubuntu, i recently installed the experimental version (19.04) rather than the LTS version. 
I performed a dual installation, so i still have Windows 10 on my PC.

I'm supposed to be running a fair amount of programs that are not yet compatible with Ubuntu 19.04; is there a way for me to downgrade my Ubuntu version? 
A peer of mine suggested re-running the dual installation process (as i did initially) but with Ubuntu 18.04, mentioning that it may be possible to overwrite the hard drive space that's been allocated for Ubuntu 19.04 rather than an actual uninstallation process.

Does anyone have experience changing or uninstalling Ubuntu versions?

Thanks in advance!

---

### Post by cruzer001 on 2019-06-05
Maybe this is what you want?

[https://ubuntuforums.org/showthread.php?t=2276580&p=13277932#post13277932](https://ubuntuforums.org/showthread.php?t=2276580&p=13277932#post13277932)

As far as I know, that still applies.  I do not use the live installer.
Having windows backed up is always a good idea when doing major changes.

I have not seen much going on with software compatibility problems.  What software is this?

Edit
The live installer also (use to) have a option to install over the existing install.

---

### Post by ajgreeny on 2019-06-05
The info in that link to an old thread is still more or less correct but there are two comments I will make.

[LIST]
[*]First, and perhaps obvious to you, but the numbered .partitions mentioned will probably not exist on your machine.
[*]Second,assuming your Windows 10 was preinstalled before you purchased the computer, it will undoubtedly be using UEFI firmware, not MBR/BIOS, so will not have a choice of where the bootloader, grub, is installed; it will by default go into the ESP/EFI partition, generally a small 200GB partition formatted as fat32, so should be easy to recognise, but you will not have a choice to make.
[/LIST]

The rest as far as I can see is OK so do not fear doing this again; just be certain you have backups of your Windows 10 and can restore that OS should anything go wrong.

---

### Post by mastablasta on 2019-06-07
> **seeminglyhuman said:**
> 
A peer of mine suggested re-running the dual installation process (as i did initially) but with Ubuntu 18.04, mentioning that it may be possible to overwrite the hard drive space that's been allocated for Ubuntu 19.04 rather than an actual uninstallation process.


there are no uninstall processes for OS. ever hear of anyone uninstalling Windows (the OS no the desktop as you could remove that in win 3.11 and earlier) or Andorid?!

do not overwrite. you should format the part of the drive where ubuntu is installed and then install 18.04 there.

> [COLOR=#000000]I'm supposed to be running a fair amount of programs that are not yet compatible with Ubuntu 19.04; [/COLOR]

which ones? maybe you just need to add PPA or snap to 19.04 install? furthermore depending on how they are packaged, they might work just fine on 19.04. they are just declared to work on 18.04. same like oyu can run winXP software on win 10. you don't need to actually install winxp to run it.

---

### Post by seeminglyhuman on 2019-06-07
So im trying to run a CERN program called ROOT (mostly for data analysis and physics computations)

I've tried different things to get it to function on experimental Ubuntu but i've reached a point where an error message is no longer displayed, it sort of just stalls on me.

---

### Post by Rubi1200 on 2019-06-07
The program may not run even on 18.04.

See the prerequisites here:
[https://root.cern.ch/build-prerequisites#ubuntu](https://root.cern.ch/build-prerequisites#ubuntu)

How did you install it initially?

Using these instructions?
[https://root.cern.ch/building-root](https://root.cern.ch/building-root)

---

### Post by cruzer001 on 2019-06-07
I find the same as rubi

So I went to the site (ROOT) and looks like you have to compile it.  Their instructions only go up to 16.04, this could be what your coworker was talking about when suggesting a downgrade.  I would have to dig thru their site and confirm 18.04 is supported.  When you installed ROOT on 19.04 you encountered no errors? No missing depencendies?

If you have to install 16.04 it will be supported till 2021.  18.04 is supported till 2023.  19.10 supported for only 9 months.

---

