---
title: "feisty won't boot"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by anatole on 2007-05-14
hi,
i just updgraded from edgy to feisty using the update manager, and right now i'm typing from a windows box since my new system won't boot. i disabled the splash to see the boot messages, here are the last lines:

```
[18.900959] hda_codec: Unknown model for ALC882, trying to auto-probe from BIOS...
[24.235478] NET: Registered protocol family 10
[24.235615] Io: Disabled Privacy Extensions

```
it stops at the same place when booting in recovery mode, too.
I tried to boot the old kernel (edgy's one), it boots fine, i just cannot get X to start as it complains about loading nvidia drivers (regardless of using nvidia or nv in xorg.conf).

i don't even have a guess why my system hangs on booting, so any help would be appreciated, thanks:)

---

### Post by dannyboy79 on 2007-05-14
i can't say for sure but the normal suggesitons are to be sure you have the latest bios and try out these boot options.

noapic
nolapic
irqpoll

if you don't use a laptop, than the noapic shouldn't really be a bad thing. I believe apic controls power management to conserver power when it's not actively running but I am not sure.

---

### Post by anatole on 2007-05-14
> **dannyboy79 said:**
> i can't say for sure but the normal suggesitons are to be sure you have the latest bios and try out these boot options.

noapic
nolapic
irqpoll

if you don't use a laptop, than the noapic shouldn't really be a bad thing. I believe apic controls power management to conserver power when it's not actively running but I am not sure.

now it hangs at detecting hard disks or setting up usb, depending on the combination of the boot options used.

---

### Post by jerrylamos on 2007-05-14
If you get to the hangs on detecting hard drives or USB, there are a couple things to try in my post "Workarounds" on "Installation & Upgrades":

My fix: put in an extra cable to put the IDE hard drive on IDE2, while the CDROM is on IDE1. Ubuntu booted right up, no "can't access tty" errors.  That changed the timing on detecting hard disks and USB such that it happened to work - for me.

Here's a quote from one of the key developers:

"Ben Collins said on 2007-04-18: (permalink)
The quick workaround for this on an installed system is to add "piix" to /etc/initramfs-tools/modules, and run "sudo update-initramfs -u"

"For installing a system, add break=top to the kernel cmdline via the bootgfx menu. Once at a busybox prompt, run "modprobe piix". Then "exit" the shell. Once the system is installed, the above work around will also be needed."

I haven't tried the latter fix.  I think he means push F6 when the boot options appear, then add 
break=top
just after quiet splash.

Then when it does break, that is come to a stop with a command prompt, do:
modprobe piix

My system "happens" to work with the CD R/W drive on IDE1, and two IDE hard drives on IDE2.  "If it isn't broken, don't fix it" so I haven't tried Ben's fixes.

Some other people's experiences are in
[https://bugs.launchpad.net/ubuntu/+s...20/+bug/106864](https://bugs.launchpad.net/ubuntu/+s...20/+bug/106864)

Cheers, Jerry

---

### Post by anatole on 2007-05-14
> **jerrylamos said:**
> If you get to the hangs on detecting hard drives or USB, there are a couple things to try in my post "Workarounds" on "Installation & Upgrades":



but this only happens if i enter the aforementioned boot options... normally, it gets past usb and hard drives, and hangs at this "Io: Disabled Privacy Extensions" part.

---

