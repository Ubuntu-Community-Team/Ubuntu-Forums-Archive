---
title: "Boot Windows 7 from an external drive after installing Lucid"
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by eshwar_andhavarapu on 2010-08-11
Hi,

i currently have lucid installed on my laptop hard drive. i took this drive out and then on a new drive in its place i have installed windows 7. reason why i couldn't put windows 7 on the same drive is that i have a BIOS based system and the hard drive is GPT based not MBR. therefore, i couldn't get windows back on it.

I figured that using an esata expresscard interface i should be able to use the Windows 7 drive externally without much speed penalty since ExpressCard in my case is implemented on PCI Express and not USB.

So i can update grub using ```
update-grub
``` and Windows 7 appears on the list. However, when i select this option during boot, it gives me errors that indicates that the external drive cannot be found (not surprising)

My guess is that when GRUB appears, the external hard drive has not been detected yet, and the modules for the expresscard may only be loaded during the boot process of lucid.

So I am wondering if there is anyway I can get this to work. meaning use lucid on my main drive and boot to Windows 7 from the external drive time to time.

---

### Post by dabl on 2010-08-11
Does your external drive appear in BIOS?  You might need to set it to boot first (before the internal drive) in the boot device sequence.  Then you'll need to disconnect it prior to booting Linux.  Also the partition that has Windows on it needs to have the "boot" flag set on it.

Grub and Linux get their clues about your storage device interfaces, and drives, from BIOS, except for USB devices.

---

### Post by oldefoxx on 2010-08-11
If you are not real sure how things are set internally, you can download and burn a bootable CD of gparted.iso, or use the gparted or partition editor that shows up on the LiveCD somewhere under System.  If you can't find it there, go into su mode in terminal and do apt-get install gparted or get the Symagtic Package Manager to install it for you.  None of these installs effect your install of Ubuntu unless done under Ubuntu itself.  They may also seem redundant, but the versions do differ somewhat, and the info and choices vary slightly as well.

As to dealing directly with Windows7 I can't help you and won't try.  My association with windows is now limited to older versions and via the VM method, a matter of personal choice.  The previous reply looked somewhat promising in that regard though.

---

### Post by eshwar_andhavarapu on 2010-08-12
> **dabl said:**
> Does your external drive appear in BIOS?  You might need to set it to boot first (before the internal drive) in the boot device sequence.  Then you'll need to disconnect it prior to booting Linux.  Also the partition that has Windows on it needs to have the "boot" flag set on it.

Grub and Linux get their clues about your storage device interfaces, and drives, from BIOS, except for USB devices.

Nope it doesn't show in BIOS. I guess that is the problem I am trying to workaround anyway. I even tried by disconnecting my internal drive so that the only hard drive available to boot from was the one over eSATA ExpressCard.

---

### Post by eshwar_andhavarapu on 2010-08-12
> **oldefoxx said:**
> If you are not real sure how things are set internally, you can download and burn a bootable CD of gparted.iso, or use the gparted or partition editor that shows up on the LiveCD somewhere under System.  If you can't find it there, go into su mode in terminal and do apt-get install gparted or get the Symagtic Package Manager to install it for you.  None of these installs effect your install of Ubuntu unless done under Ubuntu itself.  They may also seem redundant, but the versions do differ somewhat, and the info and choices vary slightly as well.

As to dealing directly with Windows7 I can't help you and won't try.  My association with windows is now limited to older versions and via the VM method, a matter of personal choice.  The previous reply looked somewhat promising in that regard though.

Thanks oldefoxx! but I am familiar with your suggestion of synaptic/gparted etc. its unfortunate that i still need to have windows around. My processor does not have hadware virtualisation support so the VirtualBox performance is not where i like it :) otherwise I'd comfortably ditch windows.

---

### Post by JBAlaska on 2010-08-12
When win 7 came out in beta, I tried to install it to a external USB HD, and it told me it would not run on a external drive. I haven't tried installing the final, but I assume it's the same deal.

---

### Post by eshwar_andhavarapu on 2010-08-12
> **JBAlaska said:**
> When win 7 came out in beta, I tried to install it to a external USB HD, and it told me it would not run on a external drive. I haven't tried installing the final, but I assume it's the same deal.

It actually does run through esata if that esata port is hooked to the main SATA controller on the board. As in not via PCI Express, ExpressCard I mean.

---

### Post by dabl on 2010-08-12
I'm going to stick my neck out and say that, if your BIOS is not capable of reading the external hard drive (actually the expresscard), then Grub is never going to see it at boot time, and you will not be able to boot an OS from it.  Sorry.

---

### Post by eshwar_andhavarapu on 2010-08-12
> **dabl said:**
> I'm going to stick my neck out and say that, if your BIOS is not capable of reading the external hard drive (actually the expresscard), then Grub is never going to see it at boot time, and you will not be able to boot an OS from it.  Sorry.

seems like the likely outcome of all this. was wondering if there was a way to custom load some drivers to see the card and then boot from that. gets fancy i suppose!

---

