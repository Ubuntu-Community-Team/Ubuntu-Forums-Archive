---
title: "Cannot boot new installation. No onboard graphics."
date: 2012-02-24
forum: Installation &amp; Upgrades
---

### Post by PSUinDC on 2012-02-24
I'm not a linux noob, however I have never had any distro as my main OS. I'm installing Linux on an old P4 that has no onboard video (only a PCI card). 

I've tried installing Ubuntu 11.10, Mint 11, and Mint 12 all with the same results.

In order to even boot these disks, I need to get the "nomodeset" operator into the boot parameters. Once I do that, I can install no problem. 

When I reboot, no matter which distro I have, since it is a single OS machine, I get no GRUB menu to show up... therefore I can't do "nomodeset", and therefore when it starts there are crazy graphical errors (incompatible video card).

I have tried the following:
[LIST]
[*]During installation, I've tried installing Nvidia packages and then installing the distro. No dice. (does that even install the drivers to the installed version, or just the virtual LiveCD version?)
[*]After installation, I've tried booting with the LiveCD, and then changing the /etc/default/grub on the installed version. No dice. I can't run the "update-grub" function, it mentions that my drive isn't mounted to /dev/
[*]I've tried hammering on the 'e' key at startup, hoping that Grub would show up. No dice.
[/LIST]

I know that if I could get GRUB to show up, I could probably get the stupid thing to boot, and then take care of the graphics drivers.  But alas, I cannot.

Any advice here?

---

### Post by darkod on 2012-02-24
When there is only ubuntu, grub menu doesn't show because there is no point for only one OS.

If you press the Shift key after the POST, the menu should show up. You can edit the ubuntu entry with nomodeset and once booted make it permanent in /etc/default/grub.

But don't just keep Shift pressed all the time, the BIOS might think the keyboard is faulty.

---

### Post by PSUinDC on 2012-02-24
> **darkod said:**
> When there is only ubuntu, grub menu doesn't show because there is no point for only one OS.

If you press the Shift key after the POST, the menu should show up. You can edit the ubuntu entry with nomodeset and once booted make it permanent in /etc/default/grub.

But don't just keep Shift pressed all the time, the BIOS might think the keyboard is faulty.

Hmm, in my current iteration of trying to install things... I think I have Mint 12 on there... and I tried the "shift" method to no avail.   Does shift only work on Ubuntu?   I was tapping shift throughout the boot.

---

### Post by darkod on 2012-02-24
Ubuntu that I know of. Sorry, no idea about Mint.

Another option is to boot into live mode, chroot into your installation and edit the grub config file to include the parameter.

---

### Post by PSUinDC on 2012-02-24
> **darkod said:**
> Ubuntu that I know of. Sorry, no idea about Mint.

Another option is to boot into live mode, chroot into your installation and edit the grub config file to include the parameter.

Editing the grub.cfg is something I've never done. I have no problem editing the grub and doing update-grub, but grub.cfg is more code-based.  What you do put into grub.cfg to get a GRUB menu to show up (or nomodeset)? Also, where do you put it? There seem to be a lot of places in that file.

---

### Post by darkod on 2012-02-25
Are we talking about ubuntu or mint?

Not sure how grub.cfg looks in mint, but if it's similar with ubuntu, for a quick one time fix you can add it in the section:
# BEGIN /etc/grub.d/10_linux

The very first menuentry is usually the one you use, so in this menuentry in the line starting with 'linux' add it before 'quiet splash'.

It should allow you your first boot.

After that you can make it properly with editing in /etc/default/grub and run update-grub which will "delete" you manual nomodeset and again add it because of your edit in the config file.

EDIT: In case you don't know where you make permanent parameters in /etc/default/grub, you need to add them in GRUB_CMDLINE_LINUX="". Add any parameter you want inside the "" and by running update-grub it will set it up in grub.cfg.

---

