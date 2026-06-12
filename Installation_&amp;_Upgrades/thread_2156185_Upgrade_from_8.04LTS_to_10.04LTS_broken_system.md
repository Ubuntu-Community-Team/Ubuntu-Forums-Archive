---
title: "Upgrade from 8.04LTS to 10.04LTS broken system"
date: 2013-06-20
forum: Installation &amp; Upgrades
---

### Post by borahshadow on 2013-06-20
Hi everyone. So I've got a server that was running 8.04LTS and since that has reached EOL I decided I needed to upgrade to 10.04.

Here's where I'm in trouble. I don't have physical access to the machine. I have access to the people who do have physical access though but they know nothing about linux so all they can do is type commands and I tell them so I need a bit of help here.

I can't recite the hardware to you off the top of my head anymore but it is an older system built around an athlon XP processor. It's got less than 1GB of ram and it's got a SATA PCI card. There is currently nothing connected to the SATA card (disconnected the drives during the update)

I used do-release-upgrade and everything worked like it should but then when I went to boot it just hangs at "Starting up" after the grub menu. That is with the default kernel the 2.6.24-38-generic-pae and the 2.6.24-38-generic-pae (recovery mode)

When I try with the -server kernel it hangs and drops into a busy box shell.


Below is the GRUB Screen

[ATTACH=CONFIG]243988[/ATTACH]

And here is the result of the 2.6.24-32-server kernel

[ATTACH=CONFIG]243989[/ATTACH]

I think it might be a problem with the IDE drive that the OS is installed on.

ANy help is appreciated

---

### Post by ahallubuntu on 2013-06-20
~

---

### Post by mörgæs on 2013-06-21
10.04 is supported until 2015 for the server packages.

---

### Post by grahammechanical on 2013-06-21
At the Grub menu when we press any key the count down timer is stopped. This is useful. Also if we press e we enter Grub edit mode.

If you select the first option at the top of the menu and press e you will see all the boot parameters. Look through them to see if the boot process is looking in the right places for its files. You might see something like

> recordfail
load_video
gfxmode $linux_gfx_mode
insmod gzio
insmod part_msdos
insmod ext3
set root=(hdo,msdos1)
linux  /boot/vmlinux-2.6.24-38-generic  blah blah
initrd /boot/initrd.img-2.6.24.38-generic


hd0 = first hard disk. msdos1 = first parttition. See if your settings look correct.

After vmlinuz-2.6.24.38-generic there will be other parameters. See if the UUID of the disk is accurate. And where you see

> initrd.lz quiet splash

remove the quiet splash and boot (press F10) and watch for error messages when the loading process stops. They might help.

Regards.

---

### Post by borahshadow on 2013-06-21
> **ahallubuntu said:**
> Do you realize that 10.04 is EOL also?
For the desktop yes. This is a (typically) headless server that doesn't have a GUI. Just like Mörgæs said > **mörgæs said:**
> 10.04 is supported until 2015 for the server packages. I want to update it all the way to 12.04 but I'd have to get 10.04 working first and secondly I'll probably wait until next spring to jump to 12.04 when I'll have physical access to the box so that this doesn't happen again. 

> **grahammechanical said:**
> At the Grub menu when we press any key the count down timer is stopped. This is useful. Also if we press e we enter Grub edit mode.

If you select the first option at the top of the menu and press e you will see all the boot parameters. Look through them to see if the boot process is looking in the right places for its files. You might see something like



hd0 = first hard disk. msdos1 = first parttition. See if your settings look correct.

After vmlinuz-2.6.24.38-generic there will be other parameters. See if the UUID of the disk is accurate. And where you see



remove the quiet splash and boot (press F10) and watch for error messages when the loading process stops. They might help.

Regards.

Ok thanks. I've sent those instructions to my mom (the one with physical access to the machine) and instructed her to take photos of the screen output at each step. Hopefully she can work through them ok. 

what is the easiest way to check the UUID of the disk? Normally I'd boot into a live system and check that way but that might be hard to have my mom do where I don't have access to the box. The UUID wouldn't have changed right? I thought I recall that those aren't supposed to change.

Here's what I'm wondering if this is what's going on. So I have the OS on a small IDE hard drive connected to the main board. I used to have two SATA disks connected to the PCI card which were running in a RAID 1 array. The RAID disks were recognized as sda and sdb and the main hard disk was sdc IIRC well once I removed the RAID disks the IDE os disk was being recognized as sda. This didn't have any problem while I was still running Hardy though because I rebooted many times with the RAID disks disconnected and it didn't hang. Probably because the system is looking for the UUID right? So if it was working fine because it was using the UUID under Hardy (The fstab was using UUID) why would it not be working now even if the boot disk is sda now instead of sdc

I'll get back to you with the pictures of the result of booting without quiet splash as soon as I get the pictures.

---

### Post by borahshadow on 2013-07-04
Ok well booting the generic-pae kernel without quiet splash didn't make and difference it still just hung at starting up.

I've determined that the UUID is incorrect. I still don't know why but I know that it is. So by using the grub command line I was able to confirm that the correct root partition is hd 0,1 or /dev/sda1. Attempting to boot from the grub command line like in this article [http://answers.oreilly.com/topic/44-how-to-discover-boot-parameters-from-the-grub-command-shell/]("http://answers.oreilly.com/topic/44-how-to-discover-boot-parameters-from-the-grub-command-shell/")

Result. I was able to find the correct kernel and initrd.img but this is the result of trying to boot that.

[ATTACH=CONFIG]244394[/ATTACH]

This seems to be the farthest that It's gotten. It still seems to be having a problem with the root partition. I see stuff from Mdadm there but I don't think that's the error that it's chocking on. (the raid drives are disconnected) Also my swap partition was on the raid but I don't know if the lack of swap would be causing all of this.

---

