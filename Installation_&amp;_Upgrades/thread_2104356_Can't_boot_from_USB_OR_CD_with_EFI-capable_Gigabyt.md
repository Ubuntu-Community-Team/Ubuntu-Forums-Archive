---
title: "Can't boot from USB OR CD with EFI-capable Gigabyte 78LMT-S2P"
date: 2013-01-12
forum: Installation &amp; Upgrades
---

### Post by malenkylizards on 2013-01-12
Hello all.  I downloaded the 64-bit Ubuntu 12.10 .iso, and both burned it to a DVD, and copied it onto a 16 GB USB thumbstick using the startup disk creator on my ubuntu 12.10 laptop.  I then tried to install it on a new computer I just built, with a Gigabyte 78LMT-S2P motherboard on it.  The little googling I've done shows people having all sorts of problems with Linux and this particular motherboard, ( for instance [http://www.rodsbooks.com/gb-hybrid-efi/](http://www.rodsbooks.com/gb-hybrid-efi/) ) but I don't really understand what EFI is.

I have been doing this with all hard drives unplugged from the motherboard, hoping this would eliminate some of the problems people have mentioned.  Anyway, here's what happens:

So for trying to do the DVD, I insert the DVD then start up the computer.  I hit delete to open bios, and set the fail-safe defaults, then make the following changes:
EFI CD/DVD Boot Option = NON-EFI
First Boot Device = CDROM

I reboot, and then it gets stuck on the "Boot from CD/DVD:" line.  Sometimes, the text output all changes from white on black to green on black.  Once, I got a screen of ascii garbage.  It's worth mentioning that the DVD drive is a possible culprit, because it was taken from the last computer and plugged into this.  It had no problems before.  When the system starts up, the DVD light flashes a regular green several times, and then stops.  I haven't been able to find a meaning for that kind of pattern.  It opens, closes, and spins up just fine as far as I can tell.

Now, trying the thumbstick, I do the exact same as above except I set First Boot Device = USB-HDD.  I've also tried USB-FDD, to no avail.  In either case, the output is "Verifying DMI Pool Data ...........\nBoot error\n".  

Please let me know what I can do to fix this problem.  I'm sure I'm not giving you all the information I can, but I don't know exactly what else would be pertinent.

---

### Post by malenkylizards on 2013-01-12
Bump.  I'm really uncertain about further steps I can take with this, if it won't a flash drive or a DVD.

---

### Post by 101kitty on 2013-01-13
sounds like to me there there could be a hardware problem, everything you explained to me sounds like your motherboard is glitching, try to update you bios, it could work or it could not but its worth a shot, if you bios is all ready updated try and downgrading it.

---

### Post by oldfred on 2013-01-13
My older Gigabyte BIOS only system only boots flash drives under the hard drive option. I tried for a long time to boot from USB options as it had many. I knew flash drive worked as it booted my laptop. Only by accident, did I find that when changing hard drives & had flash plugged in did it appear as a boot option. Flash must be correctly configured as bootable to be seen.

How large is hard drive and do you have Windows? If drive is MBR you will want to install in BIOS/legacy/CSM mode, but if drive is gpt you will want to install in UEFI mode.

---

