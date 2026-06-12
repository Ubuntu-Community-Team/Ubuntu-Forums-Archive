---
title: "GRUB and dual-booting from two different HDs"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by cgeddie on 2006-07-05
Hi Folks,

Thanks in advance for your help on this one :)

I've got an AMD64x2 system (see my signature) with a mirrored software RAID array of 2 250Gb SATA drives.  I first partitioned WinXP SP2 for 200GB of NTFS and installed Windows there.  System ran fine like that.

I want to see what using Ubuntu Linux is like, so I formatted the rest of the 250Gb RAID array with the Dapper Drake Live CD and tried to install using the instructions at [http://ubuntu-in.org/wiki/SATA_RAID_Howto](http://ubuntu-in.org/wiki/SATA_RAID_Howto).  Couldn't get the install to work, so I tried installing on /dev/hdc (GRUB drive hd1, I think), a PATA non-RAID drive also in the system.  Grub is installed on the RAID array (GRUB drive hd0), I think in the MBR.

So now I get a GRUB menu when I boot, and I can boot into WinXP just fine.  However, if I try Ubuntu, I get the first graphical screen, where the boot steps scroll in the bottom half of the screen.  It hangs on the "mounting root file system".

I don't know GRUB very well, so I'm wondering -- should I be able to boot Windows from one drive and Ubuntu Linux from another, and how do I make sure that GRUB on hd0 knows where the Ubuntu root is (on hd1)?  Or am I facing a differnt problem altogether?

Thanks!
cgeddie

---

### Post by linuchsan on 2006-07-05
it is a known kernel "bug". What happens if you disable acpi in the bios?

---

### Post by cgeddie on 2006-07-06
[QUOTE=linuchsan]it is a known kernel "bug". What happens if you disable acpi in the bios?[/QUOTE]

Thanks for the suggestion :)  I haven't had the chance to try it yet, but I will when I get home.  I had another idea after looking at other menu.lst files on the installation forum:change my GRUB menu.lst entry for Dapper to add the code in red:

```
title		hd2,2 Ubuntu 6.06 (Dapper), 2.6.15-25-amd64-generic
root		(hd2,2)
kernel		/boot/vmlinuz-2.6.15-25-amd64-generic root=[COLOR="Red"]/dev/hdd3[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-amd64-generic
boot
```

I don't get why I would have to specify "root (hd2,2)" _and_ root=/dev/hdd3, but I tried it this morning on the Ubuntu recovery mode entry in menu.lst, and I got to the sign in screen for Ubuntu at long last!  Now all I have to do is figure out how to create a user account and I'll be golden.  (Any suggestions?)

Comments are welcome.

Thanks!

---

