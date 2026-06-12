---
title: "I plan to restore Gutsy - please check out my plan"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by DrMega on 2008-06-17
Hi all

I've given Hardy a chance, and from what I gather it is working well for most, but not me. Gutsy worked ace, so I'm planning to restore my old Gutsy setup. Before I do though, I'd be grateful if someone with more in depth knowledge could double check what I plan to do.

Basically, I have two hard disks. Gutsy is on my secondary disk, which used to be my primary until I replaced it because I thought it had failed (the plug came off and I have to confess I didn't check until I went to install the replacement). So I can access all the files from my old hard disk, but can't boot from it. Hardy is on my new primary disk.

Here's my plan.

1. Delete my entire file system using a well published command that blows everything away (if I do that will bash still work?)

2. Copy everything exactly as is from the root of the secondary disk to the root of the primary.

Will that work? Will all attributes (permissions etc) come across OK?

---

### Post by logos34 on 2008-06-17
> **DrMega said:**
> Basically, I have two hard disks. Gutsy is on my secondary disk, which used to be my primary until I replaced it because I thought it had failed (the plug came off and I have to confess I didn't check until I went to install the replacement). So I can access all the files from my old hard disk, but can't boot from it. Hardy is on my new primary disk.


wait...are you sure you can't boot from gutsy?  Can't you switch the boot order in the Bios?  Or change the 'root' line (press 'e' on grub screen) to '(hd1,?)' (if booting from hardy grub on new drive)?

You can wipe the new hard disk with hardy using gparted (delete partitions).

If you want to copy gutsy root to new drive, it can be done.  Use [Gparted]("http://gparted.sourceforge.net/larry/move/move.htm") move option or [dd command]("http://www.brunolinux.com/02-The_Terminal/The_dd_command.html").  Then [reinstall gutsy grub]("http://ubuntuforums.org/showthread.php?t=224351") to the MBR of the new drive.

OR use '**cp -dpR**' (aka **cp -a**) like they do [here]("http://ubuntuforums.org/showthread.php?t=431645").

---

### Post by DrMega on 2008-06-17
> **logos34 said:**
> wait...are you sure you can't boot from gutsy?  Can't you switch the boot order in the Bios?  Or change the 'root' line (press 'e' on grub screen) to '(hd1,?)' (if booting from hardy grub on new drive)?

Thanks for that. I tried but unfortunately it didn't work. Oddly enough when I installed Hardy it recognised that Gutsy was on the other disk and created it a grub menu entry, but that doesn't work either, yet I can access the other disk once I've booted.

I reckon what I'll do to be on the safe side is just blow away Hardy and reinstall Gutsy from scratch, thus ensuring that the MBR is in order, then just overwrite everything from the the setup on the other disk.

---

### Post by logos34 on 2008-06-17
> **DrMega said:**
> I reckon what I'll do to be on the safe side is just blow away Hardy and reinstall Gutsy from scratch, thus ensuring that the MBR is in order, then just overwrite everything from the the setup on the other disk.

ok, whatever.  

You might copy over the deb pkgs in /var/cache/apt/archives to new gutsy install before you overwrite the old disk--at least you won't have to download everything a second time.  (same for /opt and /usr/share).

good luck

---

### Post by DrMega on 2008-06-18
> **logos34 said:**
> ok, whatever.  

You might copy over the deb pkgs in /var/cache/apt/archives to new gutsy install before you overwrite the old disk--at least you won't have to download everything a second time.  (same for /opt and /usr/share).

good luck

Thanks. In theory, once I've installed Gutsy on what is now the primary disk, if I then reboot from the LiveCD I should be able to overwrite that setup with the files at the root of the secondary disk (which used to be the primary). That way, in theory at least, I should have two identical copies of the setup, one on the primary disk and one on the secondary, and the MBR and grub and everything should be all set up nicely.

---

