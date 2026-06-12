---
title: "Convert Broken Gutsy Intall to Hardy"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by burgerearl on 2008-04-24
I tried to install Gutsy on my desktop last year. After some installation issues, I was able to install but never got a functioning GUI (details here: [http://ubuntuforums.org/showthread.php?t=623421](http://ubuntuforums.org/showthread.php?t=623421))

Right now I have:

Functioning GRUB that can successfully boot XP
Dysfunctional Gutsy install (video problems described in other post)

This (I believe) is on one XP partition and a typical set of Ubuntu partitions.

I'd love to give Ubuntu another shot on my desktop. What would be the easiest way for me to get Hardy installed alongside XP? Personally, I'd prefer to ditch the Gutsy install completely and install with Wubi, but I'm open to any suggestion that will work.

Thanks!
Jake

---

### Post by forestpixie on 2008-04-24
You could do either obviously - depending on how your partitions are fixed. IF you want to install Hardy you can point the install at the original partition by choosing manual at the partitioning stage. There should be at the least 2 partitions for linux - 1 will be marked as swap 1 won't be.

When you get to the partition part - highlight the partition that isn't the swap, edit it and on the edit page choose / as it's mountpoint. That will overwrite the original installation.

To use wubi I believe that it will use 3- 4Gb on your xp install partition - but I'm not that sure of the space it takes.

---

### Post by burgerearl on 2008-04-25
Thanks for the tip. I'm having some delays downloading the live CD, so I'll get back to you when I can to share how it worked.

---

### Post by burgerearl on 2008-04-29
OK, sorry for the long delay. I'm closing in on finals at school and haven't had much time to tinker.

I ended up trying wubi. It actually asks how much space to use, rather than defaulting to 3 or 4 GB. The wubi install went great (I have a GUI... yay!). No problems, everything I've tried to do so far in Hardy is working fine.

Two follow on questions that I'm not 100% sure belong in this thread, so please let me know if I should post them somewhere else:

1. I get two weird quirks while booting:
[INDENT]a. My monitor displays "input not supported" for 10-15 seconds after the splash screen and before the scrolling list of boot actions (not sure what you'd call that). In any case, I don't really need to change this, but I'm sort of curious what I'm missing.[/INDENT]

[INDENT]b. During that list of actions, it sits for 2-3 minutes on "swapfile swap" (I'll have to reboot and double check the exact message, but that's the gist of it). It hasn't hung yet and as far as I can tell there's no problem, but it is sort of obnoxious. It would be great if I could reduce this delay.[/INDENT]

2. My boot sequence currently consists of: selecting my XP install in the GRUB menu Gutsy set up, then selecting Ubuntu from the bootloader that wubi/hardy set up (not sure which bootloader it is).

Since I'm definitely not going to use Gutsy (and never really could), I'd like to reclaim that hard drive space. I've looked around, and I think I know how to go about this, but wanted to double check. My thinking is to first remove GRUB by running
```
fdisk /mbr
```from my XP command prompt, then resizing my windows partition (to the full size of the drive) with gparted. Can anyone verify that restoring the windows bootloader won't screw up the wubi bootloader?

Thanks for the help

Jake

---

### Post by Moop on 2008-04-29
I think the command you run after booting from the XP cd and choosing the repair option is ```
fixmbr
``` 

I've never used wubi but if it's running inside of XP then fixing your mbr shouldn't make a difference to wubi. But I don't really know how that works.

---

