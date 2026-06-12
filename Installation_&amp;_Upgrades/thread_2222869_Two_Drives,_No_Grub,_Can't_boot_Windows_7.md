---
title: "Two Drives, No Grub, Can't boot Windows 7"
date: 2014-05-08
forum: Installation &amp; Upgrades
---

### Post by Maverick Meerkat on 2014-05-08
Hello all,

I put a second hard drive in my computer trying to boot Windows 7 on one, Ubuntu 14.04 on the other.
Now, the computer goes straight to Ubuntu.
I can get to my files on the Win. 7 disk, I just can't boot Windows.

This idea worked great on my older Win XP computer.
It also worked when I put 13.10 on my Win. 7 computer.
I think I went wrong when I tried to do a fresh install of 14.04, and I didn't unplug the Windows drive.
I selected Uninstall Ubuntu 13.10, and install Ubuntu 14.04 ( a 250 Gig drive )

I have read numerous posts but it's all foggy to me as to which approach is for me.
I don't want to make things worse while guessing.
Although I've used Ubuntu for 3 years, I am not very well versed on these things.
Ubuntu always worked good enough for me that I was spoiled.

If I could get Windows to boot, it would save me much trouble at home.
My wife is tolerant of Ubuntu, but this could strain that.

Here's the link for my info: [http://paste.ubuntu.com/7302461/](http://paste.ubuntu.com/7302461/)

Thanks a million for any assistance :-)

Rick

---

### Post by Maverick Meerkat on 2014-05-08
Oh yeah,

What about this idea:
[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

---

### Post by Mark Phelps on 2014-05-08
> I think I went wrong when I tried to do a fresh install of 14.04, and I didn't unplug the Windows drive.

My guess is that you are right -- GRUB was installed by default to the "first" drive in the system, in your case, the Windows drive.

Info on restoring the Windows MBR using Lilo (courtesy of OldFred):  > Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader to boot partition with boot flag (Windows).

---

### Post by oldfred on 2014-05-08
Installing lilo should get Windows booting as it is installed in BIOS mode.
But system looks like it is UEFI as well as BIOS as even the HP recovery partition has efi files.

And then you installed Ubuntu in UEFI boot mode.
That can be done, but you can only dual boot from UEFI/BIOS. You may have to turn on/off UEFI or turn on/off BIOS mode to boot Windows in BIOS and Ubuntu in UEFI. Some auto switch, but you can only dual boot from UEFI menu.

You can use Boot-Repair to convert Ubuntu from UEFI boot to BIOS boot. Or even do that from inside you Ubuntu install. Boot-Repair uninstalls grub-efi(UEFI boot) and installs grub-pc(BIOS boot). 
But before doing that you have to use gparted or gdisk and create a tiny 1 or 2MB unformatted partition with the bios_grub flag if using gparted or as ef02 setting if using gdisk.
Ubuntu will boot fine in BIOS or UEFI boot modes from a drive partitioned with gpt like your sdb.
Windows will only boot in BIOS mode from a MBR(msdos) partitioned drive like your sda.

---

### Post by Maverick Meerkat on 2014-05-09
Thank you Mark and Oldfred!

I couldn't wait to get on the computer and try Lilo after reading your advice.
Lilo worked exactly as you have stated.
Because you warned me in advance, the pop-up message did not scare me.

The process took maybe a minute, probably less.

Upon reboot, the system booted directly into Ubuntu. No menu to choose.
No problem because Oldfred said the OS's were in different boot modes.

Upon restart, again, I hit f-9 for the boot menu, and selected Sata-0 ( Windows 7 drive )
Now, before your help with Lilo, this part did not work.
This time, Windows Recovery showed up, and I selected Startup Repair, then rebooted.
As long as I select Sata-0, Windows 7 boots perfectly, otherwise, I get Ubuntu :-)

This is all I ever wanted, 2 systems, on 2 drives.

It was a big concern when I wrecked it in the first place.
The computer was about 2 months old, and I didn't want my wife to think I killed it, lol.

One of the things that makes Ubuntu great, is the people.
Mark and Oldfred came to the rescue of a guy they've never met, and graciously handed him a rope.
I really read here much more than I post, and it's comforting to know that there is help.

You guys are awesome!
"Humanity towards others"... yep, that is a very fitting definition of Ubuntu.

Peace,

Rick

---

