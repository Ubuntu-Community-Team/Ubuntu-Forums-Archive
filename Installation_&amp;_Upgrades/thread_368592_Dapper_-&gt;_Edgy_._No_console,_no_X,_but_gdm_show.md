---
title: "Dapper -&gt; Edgy . No console, no X, but gdm shows up"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by floogy on 2007-02-23
Hi there,

I tried to do an upgrade from dapper to edgy. Unfortunately I got several, up to 100 packages which are from an "unknown" source. Shame on me: I bet that was due to pinning to debian in hoary or breezy(?).

I got several errors, and the gksu update-manager -c method was interrupted. It told me to fix it with -f.

Thanks to --force-overwrite, and switching from apt-get dist-upgrade -f to aptitude dist-upgrade -f and vice et versa, I managed it to do the upgrade. A last try said, that there is nothing left to be upgraded or configured. Up to 100 packages were removed. I thought: That's fine! Let's try a reboot!

Now it seems, that there aren't any console, and gdm isn't able to start anything. gdm is veeeeryy slooow, and it takes about more than one minute to type the password in, after one typed the user name in the field.

With CTRL+ALT+F1 - F6 I only see a black screen with a blinking cursor :(

I started with these kernel options: nosplash vga=788 fb=false xserver=vesa

The recovery mode doesn't work either :((

Thank in advance! I'm stuck.. :(

---

### Post by jimbren on 2007-02-23
> With CTRL+ALT+F1 - F6 I only see a black screen with a blinking cursor 

I wonder if the screen is just off to the side somewhat?  What happens if you try and enter characters on the screen?  Do they appear?

jimbo

---

### Post by floogy on 2007-02-23
No, I can not enter anything - it's a dead cursor.

I don't think, that ttyS0 has got something to do with it, but anyway here it is:
> [  242.214035] ttyS0: LSR safety check engaged!
[  242.214675] ttyS0: LSR safety check engaged!

That might be due to the framebufferdevice:
> Feb 23 21:54:05 localhost kernel: [   40.731840] vga16fb: initializing
I'm wondering if that's possible, because I thought, that nosplash vga=788 fb=false xserver=vesa will avoid the framebuffer to load???

> Feb 23 21:54:05 localhost kernel: [   40.699554] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x4c00
Feb 23 21:54:05 localhost kernel: [   40.702256] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x4c40
Feb 23 21:54:05 localhost kernel: [   40.709677] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
Feb 23 21:54:05 localhost kernel: [   40.712233] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
Feb 23 21:54:05 localhost kernel: [   40.714791] PCI: Unable to reserve mem region #2:8000000@c0000000 for device 0000:01:00.0
Feb 23 21:54:05 localhost kernel: [   40.717350] nvidiafb: cannot request PCI regions
Feb 23 21:54:05 localhost kernel: [   40.731840] vga16fb: initializing
Feb 23 21:54:05 localhost kernel: [   40.731846] vga16fb: mapped to 0xffff8100000a0000
Feb 23 21:54:05 localhost kernel: [   40.734430] fb1: VGA16 VGA frame buffer device

---

