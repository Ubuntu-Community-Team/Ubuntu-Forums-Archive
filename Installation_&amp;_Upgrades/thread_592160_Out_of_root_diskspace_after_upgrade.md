---
title: "Out of root diskspace after upgrade"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by BroadArrow on 2007-10-26
After attempting to upgrade from Xubuntu Feisty to Gutsy I am unable to log in and get the message "GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator." after entering log in details. Pressing OK returns me to the log in screen.

I have managed to get to a prompt by rebooting in recovery mode (selected via Grub). A "df" shows me the 6GB root partition has 0GB available. (Other partitions where I keep all my non-operating system related stuff have plenty of room.) So it might be that I am in fact out of space where it counts?

I would simply resize partitions but I can't boot into my gparted CD-ROM because this server doesn't have an optical drive. So I have to find a solution that uses the network or the prompt.

Perhaps a solution would be to delete files to create space -- but what can I safely delete? What would give me the most gain in GB? If I'm lucky I only need enough space to log in under X, start gparted and resize my partitions.

Thanks in advance for any help!

PS: I'm a little annoyed that the upgrade utility didn't see this coming and warn me...

---

### Post by thelocust on 2007-10-26
[COLOR=#666666]I know that there is a way to use gparted off of a usb thumb drive and there is always cannibalization. The usb thing is on the gparted live cd website.[/COLOR]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]

---

### Post by paul.matthijsse on 2007-10-26
> **BroadArrow said:**
> A "df" shows me the 6GB root partition has 0GB available. Hello, 6 GB in /root is way too much for Xubuntu, which is a lightweight distro! Even on my Gnome pc that runs for more than a year /root is only 11 MB, so something is wrong with your system. Type:
# sudo du -H /root 
to see what occupies all that space...

Edit: I've installed xubuntu 7.10 release candidate in a VM (without installing extra software, so just the base install) and /root contains only 82 KB! Definitely something wrong with your machine!

Cheers, Paul.

---

### Post by BroadArrow on 2007-10-26
> **paul.matthijsse said:**
> Hello, 6 GB in /root is way too much for Xubuntu
Sorry, I should have been clearer: I have a 6GB root partition ("/"), not a 6BG root user partition ("/root"). So this partition houses the entire operating system and home directories. (BTW, I've gone through the home directories to ensure they're not using too much space.)

Could it be that old packages from before the upgrade are still stored on my computer somewhere and can now  be removed? If so, does anyone know where they are and how to remove them?

---

### Post by BroadArrow on 2007-10-26
> **thelocust said:**
> [COLOR=#666666]I know that there is a way to use gparted off of a usb thumb drive and there is always cannibalization. The usb thing is on the gparted live cd website.[/COLOR]
[FONT=Times New Roman][/FONT]
That's a good idea. I'll try creating a bootable gparted USB drive to boot into. I might still have to find some files to delete or move to another partition to create extra room though. :-(

---

### Post by BroadArrow on 2007-10-26
> **BroadArrow said:**
> That's a good idea. I'll try creating a bootable gparted USB drive to boot into. I might still have to find some files to delete or move to another partition to create extra room though. :-(
Didn't work. The server BIOS is unable to boot from the USB drive. For some reason it can't find an OS to boot. I've tried both "syslinux" and "syslinux -s" on the gparted USB drive. Might be an old or finicky BIOS. Back to trying to create space on the root partition to be able to login to X and run gparted from there... :-(

---

### Post by BroadArrow on 2007-10-27
I've resorted to canibalising another box to put a CDROM on this one. Even the Xubuntu live CDs are having trouble starting. Both the 7.06 and 7.10 CDs pause a long time while displaying messages like:

> [131.080000] Buffer I/O error on device fd0, logical block 0.

Would that occur simply if the root partition was full?

---

### Post by BroadArrow on 2007-10-27
I have managed to create enough space in my root partition to log in to X by clearing the apt package cache with:

> sudo apt-get clean

I'm now continuing the upgrade with fingers crossed that I don't run out of diskspace again...

---

