---
title: "Howto do a Ubuntu install from Debian?"
date: 2006-04-24
forum: Installation &amp; Upgrades
---

### Post by kaze on 2006-04-24
What to do? I have a functional Debian system I want to wipe and replace with Ubuntu. Optical boot fails. Network install fails.

Short story long:

Have a known good Ubuntu bootable CDR. Target machine wont boot from it with BIOS correctly set.

I know the CDROM drive mostly works cause once I boot into the currently installed Debian system I can mount and read the CD. There is possibly something wrong with it though as it takes a while to spin up and only mounted after a few ejects and tries.

Did the five floppy netinstall thing from "Curufir" from here: [http://www.ubuntuforums.org/showthread.php?t=75372](http://www.ubuntuforums.org/showthread.php?t=75372). Worked fine except for the Kernel panic and hang I got - maybe due to a lack of RAM (or a PCMCIA network card based 'net connection attempt.) (Seems like a slightly older form of the same thread is here: [http://ubuntuforums.org/showthread.php?t=29555](http://ubuntuforums.org/showthread.php?t=29555))

Found the Smart Boot Manager (SBM) referenced on the Ubuntu forums and got that and got it to work. Then said D'oh when I realized what I knew already - that the laptop only takes the floppy OR the CDROM. There is a single bay for either one or the other...

After that I tried an external USB optical with the SBM - but it didn't recognize it, so couldn't go there.

Somewhere during the above I found a link from the Ubuntu forums to [http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html). This is a okay howto for going from W32 to Ubuntu, but for non-Windows says, "...if you start from something else. You'll just have to "translate" a bit. As a bonus, the "translation" will probably be shorter and easier."

---

### Post by Qrk on 2006-04-24
You can directly upgrade from Debian to Ubuntu by editing /etc/apt/ sources.list. It is probably very risky, though.

I'd recommend first upgrading Debian to testing, etch, if you aren't using etch already.

After that upgrade, you should be able to change /etc/apt/sources.list to point to Breezy by replacing the contents with this:

```
# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://us.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse
```

Now, update, but don't upgrade. ;) 

Then install these:

```
sudo aptitude install ubuntu-desktop ubuntu-standard 
```

Now do an upgrade.

```
sudo apt-get dist-upgrade
```

This might work. No guarentees. I once used the same method to install Warty from Woody, but that was a while ago. (Also, it didn't work too well. I got a functional system, but I had so many left over packages I decided to reinstall anyway)

You may not want to ruin a functioning Debian install just for Ubuntu.

---

### Post by lha on 2006-04-24
Those instructions you looked at do use netinstall, so if it is really netinstall that doesn't work for you, there's not much I can do to help you. But if the problem lies within netinstall floppies, you aren't far from the solution. Download kernel and ramdisk image as instructed (but be sure to get Breezy, not Hoary). Add a menu entry to Debian's boot loader that lets you boot the installer, restart and start the installation. Hopefully installer won't give you kernel panic or render your computer unbootable. Good luck!

---

### Post by kaze on 2006-04-24
Net-install floppies did work. Don't want to upgrade - need to do a fresh install.

What if I pull the drive out and copy the CD onto it. Or onto a partition on it. Is there a way to then return the drive to the target laptop and boot from a floppy and initiate the install?

---

### Post by lha on 2006-04-25
[QUOTE=kaze]Net-install floppies did work. Don't want to upgrade - need to do a fresh install.

What if I pull the drive out and copy the CD onto it. Or onto a partition on it. Is there a way to then return the drive to the target laptop and boot from a floppy and initiate the install?[/QUOTE]

I once copied contents of a Ubuntu live-cd to a hd partition and managed to boot it. While live-cd was booting up, it couldn't find the files it was looking for so I had to manually mount the partition with live-cd files into cdrom's mount point to get it working. Maybe you can use similar trickery to make it work.

SBM can be installed on hard drives. Then you could try to boot installation cd with SBM. (If you install SBM on your hd, be sure to make a backup of your mbr so you can restore it and boot Debian if something goes wrong with SBM.)

---

### Post by lha on 2006-04-25
Wiki has a page with title [Installation/FromHardDriveWithFloppies]("https://wiki.ubuntu.com/Installation/FromHardDriveWithFloppies")

---

### Post by kaze on 2006-04-25
Looks perfect! Gonna try it tonight or tomorrow.

Here's a cleaner earl to the above poster's link: [https://wiki.ubuntu.com/Installation/FromHardDriveWithFloppies](https://wiki.ubuntu.com/Installation/FromHardDriveWithFloppies)

thanks

---

### Post by kaze on 2006-04-30
The GrubHowto/BootFloppy page worked great.

Tom's root boot is still awesome.

Followed Installation/FromHardDriveWithFloppies:

Could not get the target laptop to recognize any external USB harddrive - I figure it's an older USB, I  know it's v1.1. So just like the not booting from CD and only floppy -or- CDROM it's a hardware limitation and I just have to live with it.

Step 2. under "Setting up the Destination Drive" says "use fdisk or cfdisk to partition the harddrive" - tomsrtbt doesn't seem to have cfdisk... Maybe I just have an older version. No matter.

Step 2. under "Setting up the Destination Drive" says NOTHING about formating the root and "ISO" partitions - it's just assumed... Can't really copy the files out of the mounted iso to the to be root partition until after you a mke2fs...

When I got to step 5. I paused as I found the syntax curious, "dd if=/mnt/usb/ubuntu.iso of=/dev/hdaX". I had the ubuntu.iso on a machine at work. Pulled the laptop hard drive and made a large hda1 for /, hda2 for swap, and a >700MB hda3. As I was on a Windows box I figured to make hda3 FAT16, and copied ubuntu.iso onto it. Now when I got to the fourth bullet under "Installation," "In the device prompt, provide the device name for the dummy partition, such as /dev/hdaX." the iso FILE was useless as the installer won’t accept and can't mount and use /dev/hda3/ubuntu.iso... So back to tomsrtbt and
mount /dev/hda3 hda3 -t msdos
cp /mnt/hda3/ubuntu.iso /mnt/hda1
umount /dev/hda3
dd if=/mnt/hda1/ubuntu.iso of=/dev/hda3
Okay, so I'm learning and think it's way cool that you can copy an iso into a partition, and it makes sense that dd would do this. Question: can you even do this on a Windows box?

Under step 6. "mount -t iso9660 -o loop /dev/hdaX iso" tomsrtbt man mount doesn't list of define "-o loop". What is this?

In the "Booting into the Installation" section when I printed this webpage the kernel line wrapped. This stumped me for a few minutes as "root=/dev/rd/0 rw --" doesn't work too well. It does mention above the code kernel...single line...ends with "--", but still...

So, once I got all that way, the installed just went into an infinite loop saying "killed", "killed", "killed", "killed"... I tried the no memory option on the kernel line but that yielded the same results. My install runs in "low memory mode" and suggests creating a swap file ASAP. Can I manually create a swap partition prior to running setup and pass a parameter to the installer to use it? Should I investigate isolinux.cfg to try a non default install?

Thanks in for reading and helping,
kaze

---

### Post by kaze on 2006-04-30
Updated the wiki with some of my findings.

---

### Post by lha on 2006-05-01
[QUOTE=kaze]When I got to step 5. I paused as I found the syntax curious, "dd if=/mnt/usb/ubuntu.iso of=/dev/hdaX". I had the ubuntu.iso on a machine at work. Pulled the laptop hard drive and made a large hda1 for /, hda2 for swap, and a >700MB hda3. As I was on a Windows box I figured to make hda3 FAT16, and copied ubuntu.iso onto it. Now when I got to the fourth bullet under "Installation," "In the device prompt, provide the device name for the dummy partition, such as /dev/hdaX." the iso FILE was useless as the installer won’t accept and can't mount and use /dev/hda3/ubuntu.iso... So back to tomsrtbt and
mount /dev/hda3 hda3 -t msdos
cp /mnt/hda3/ubuntu.iso /mnt/hda1
umount /dev/hda3
dd if=/mnt/hda1/ubuntu.iso of=/dev/hda3
Okay, so I'm learning and think it's way cool that you can copy an iso into a partition, and it makes sense that dd would do this. Question: can you even do this on a Windows box?[/QUOTE]
When I was fooling around with Ubuntu live cd (trying to boot it directly from hd), I copied the contents of a live cd image into a partition and managed to boot from there. Maybe this would work with the installer, too. Some archiver (I mean WinZip, WinRar, 7-Zip) was able to read and unpack isos, so this method would be available for those with WIndows only.

There's also [dd for Windows]("http://uranus.it.swin.edu.au/~jn/linux/rawwrite/dd.htm"). Haven't used it, but it might do the trick.

[QUOTE=kaze]Under step 6. "mount -t iso9660 -o loop /dev/hdaX iso" tomsrtbt man mount doesn't list of define "-o loop". What is this?[/QUOTE]
-o loop tells mount to use a loopback device that allows you to mount a normal disk file as a filesystem.


[QUOTE=kaze]So, once I got all that way, the installed just went into an infinite loop saying "killed", "killed", "killed", "killed"... I tried the no memory option on the kernel line but that yielded the same results. My install runs in "low memory mode" and suggests creating a swap file ASAP. Can I manually create a swap partition prior to running setup and pass a parameter to the installer to use it? Should I investigate isolinux.cfg to try a non default install?[/QUOTE]
After you have started the installer, press <control>-<alt>-<f2> to get a shell. Then use instructions from [http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html]("http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html") to mount your existing swap partition (mkswap /dev/hdb2 && swapon /dev/hdb2) or to create a swapfile and use it.

---

