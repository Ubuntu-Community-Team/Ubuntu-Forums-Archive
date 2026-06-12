---
title: "Legacy Dual-Boot drive U16.04/W7 - OS undetected"
date: 2021-01-12
forum: Installation &amp; Upgrades
---

### Post by 0georgebaldwin0 on 2021-01-12
Up until a few weeks ago I was running Mate 16.04 and W7 as a single drive dual boot set-up on my Lenovo T520. This ran for several years with minimal problems and whilst I was sorting out my new 3 SSD set-up I'd still be using it. When everything was working well, I just put the original dual-boot drive on one side.

 I would now like to resuscitate an OS-less Tosh C50 using that same drive but I can't get it to boot. At first I was just getting a message saying "OS not detected" and now I've disabled smart boot I  just get to the "grub rescue" prompt. I've tried using some of the suggestions I've found to identify drives and update etc but there's no response to any commands. I retested the drive in the Lenovo and it still works fine but I can't see what I've missed in the Tosh BIOS config....I'm assuming that's the root of the problem.

As always, I'd be most appreciative of any suggestions.

---

### Post by gdesilva on 2021-01-12
Here is a good tutorial on how to boot from the grub-rescue prompt

 [https://linoxide.com/linux-how-to/grub-rescue-commands/](https://linoxide.com/linux-how-to/grub-rescue-commands/) 

You would want to make sure that BIOS is in legacy boot mode and that Lenovo was using the same boot mode - ie not UEFI boot mode.

---

### Post by CelticWarrior on 2021-01-12
> [COLOR=#000000]I would now like to resuscitate an OS-less Tosh C50 using that same drive but I can't get it to boot.[/COLOR]
If this is what you want you need to understand the differences between the BIOS mode of your old installation and the likely default UEFI mode of the new machine which is incompatible. The only hope for getting it to work is following the advice in post #2, i.e., enabling Legacy/CSM boot mode only in the new machine firmware that is UEFI, no longer BIOS. Please note it may not have the required compatibility mode (Legacy AKA CSM AKA "BIOS" mode) but most still have it so you may give a go.

Now, honestly, what you want to do you SHOULDN'T. 
First of all, Windows 7 is out of support and shouldn't be used as a daily driver connected to the internet. End of story, there no reason or excuse that justifies the use of unpatched OSes, it's dangerous to the user and everybody else considering it can be used for criminal activities very easily due to not having the current security updates.
Secondly, regarding the old Ubuntu, there's really no point in trying to make it work in a totally different hardware and, even worse, years apart. Even if you manage to do so it will take a LOT more time than a fresh installation and end up with subpar results.

Please do the smart thing: Backup your personal files and install a new, supported release of Ubuntu, in the proper UEFI mode in the new machine. You may reuse the drive, of course, but not what's installed there and you should start by creating a new GPT partitioning instead of the MBR it currently has. And if you need Windows then install Windows 10 as dual-boot.

---

### Post by grahammechanical on 2021-01-12
Please put the hard drive back in the Lenovo, run a Live Session, open GParted and take a screenshot of the hard drive partitions as represented in GParted. Post the screenshot in this thread. We use the insert image icon to the left of the quote bubble icon.

If you are getting a Grub rescue prompt then the motherboard is accessing the hard drive and Grub is loading but cannot find its boot files at /boot/grub. That is my guess. The layout of the partitions might or might not help.

Regards

---

