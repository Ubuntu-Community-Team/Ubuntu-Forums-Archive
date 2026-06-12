---
title: "Tried to upgrade, nothing will boot"
date: 2017-03-12
forum: Installation &amp; Upgrades
---

### Post by mlogan2000 on 2017-03-12
Hi there. First off, I'm (still) a complete noob with Ubuntu/Linux. I've only tried to getting it working as my computer will not install Windows at all and I'm trying to avoid having a $700 paperweight.  I have done a fair bit of searching and not found the help I need either, so if it's somewhere out there, I do apologize.

At any rate, I've had Ubuntu installed for a few weeks at least now, but it's never been a particularly stable build. At best, I've been able to use it for some intermittent internet use, when Firefox decides to cooperate or Ubuntu is not freezing up.

I am running Ubuntu 16.04 on an Asus K501ux. As I said it's never worked solidly for me and I was hoping an upgrade - when I saw it was available - might help that. Instead, I now cannot get my computer to boot up at all. At best, it will go to the loading screen and stay there. 

When I try to run recovery mode (if I can get to the screen that allows me to), I get a message, after a lot of stuff, that says "end Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)".  I've read quite a bit on others' issues with this, and so I created a USB for Boot Repair. Only Boot Repair will not run either. It goes to the loading screen and stays there. 

With Boot Repair not working, I'm not sure how next to proceed. I'm not sure what info to give as I can't seem to get anywhere that I can use a command prompt to try diagnostic things. 

I did also try creating a fresh USB install of Ubuntu, but that would not run either - gets to loading and stays. 

Please let me know what information is needed. Thank you for your patience.

---

### Post by oldfred on 2017-03-12
Did you install the nVidia proprietary drivers from Ubuntu repository.
And then uninstall before upgrade. All ppa & proprietary drives need to be uninstalled before an upgrade or you will have issues.

Have you tried nomodeset? With Asus you may also need other boot parameters also.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 

Did you install in UEFI or BIOS boot mode? It is a new UEFI system.

        Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    
Do you have good backups? Then a new clean install is an option.

---

