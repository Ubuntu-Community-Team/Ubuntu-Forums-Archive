---
title: "[SOLVED] Missing Ubuntu in dual boot"
date: 2007-08-15
forum: Installation &amp; Upgrades
---

### Post by notbitmonk on 2007-08-15
I had XP and Kubuntu installed but decided to make a fresh installation of Ubuntu.  It didn't went good and had to do a complete installation of XP.  I have a 120 Gb SATA drive for my OSs and a 80 Gb ATA for my documents (music, work, etc.).  Of the 120 Gb drive 115 gb are available.  Since I use my XP for gaming, i set 100 Gb for XP, 13 GB fo Ubuntu (ext3) and 2 gb for swap.  Did the windows install first.  Of the free space, I had Windows create a new partition as specified above.  Did my installation with no problems and could load into Windows.  From Ubuntu Live CD I selected the manual partition and created the partitions mentioned above.  Installation completed and when I restarted the machine, it didn't ask me which OS I wanted to load and went directly to Windows.  I could go into Windows and select the ext3 and swap partition and delete them to try to install Ubuntu again but I'm afraid that will also mess up my XP installation and I just spent a whole day installing it.  I was not using Guided option to use the biggest free space because I was afraid it would use my ATA drive.  Now that I think of it, the installation it should not use my ATA drive because its already partitioned and I could use that option without fear of messing my drives.  Am I correct in my assumptions?  If I delete the ext3 and swap partitions from within Windows, will that mess things up?

---

### Post by jnorthr on 2007-08-15
think there is a utility you can burn to cd called supergrub. It's the same as used in the ubuntu install. That may allow you to play with the partitions for ubuntu without blitzing the xp. Did you install ubuntu on the 2nd drive ? The install may have placed the supergrub loader there rather than over the xp loader on the sata drive. This means that when you boot, the sata drive is still 'seen' first by the bios rather than the supergrub of your 2nd drive. You thereby miss the chance to pick which o/s u want to boot.  Can you change your bios to boot from the second drive first just to test this ?

If you try to use fdisk from xp it may not do it correctly and/or may blitz the partition type so that it does not have a recognisible type, though this is no big deal as you can use the ubuntu install again to do a manual config. of your partitions. Look here: [http://supergrub.forjamari.linex.org/?section=features](http://supergrub.forjamari.linex.org/?section=features)

---

### Post by viking777 on 2007-08-15
Another thing to try is Puppy linux it is only 82Mb, runs from disc and allows you to do just about anything with an OS that it is possible to do, including rewriting or installing MBR's and boot managers as well as partitioning. Supergrub disk does this as well, but I find it much more complicated than Puppy and I like things to be easy!

---

### Post by notbitmonk on 2007-08-15
jnorthr: The installation was performed in the SATA drive.  From XP I want to delete the ext3 and swap partitions so I can do a fresh install of Ubuntu.  Think I may run in any trouble by deleting the partitions?

---

### Post by notbitmonk on 2007-08-16
I was able to delete the partitions without any problem.  After I deleted the partition I shut down the machine and booted it into Windows without any trouble.  The installation went OK (I selected to use the largest free space) and apparently all was good.  Upon restarting now I receive: ERROR loading operating system.  If I boot using LiveCD, I can see all the partition with their corresponding data.  Yesterday, while I was searching for this problem I found some information related to /boot/grub/menu.lst but I'm not sure if that's where I need to change things.  Any Help?

---

### Post by notbitmonk on 2007-08-16
Here is what is in my Menu.lst
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=7c5c40c3-1152-4d13-9502-b068c7f0944c ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=7c5c40c3-1152-4d13-9502-b068c7f0944c ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

I don't know a lot about this but I know that the first Windows entry is wrong, there shouldn't be any OS in the hda1.

---

### Post by notbitmonk on 2007-08-16
I went in to a terminal typed sudo gedit /boot/media/grub/menu.lst and deleted the first Windows entry.  It didn't work.  I still receive the Error Loading Operating System.

---

### Post by notbitmonk on 2007-08-16
I tried using fixboot and fixmbr from the XP CD recovery console to no avail.  Looking through the web I found a post that might help ([http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/906009711831]("http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/906009711831")):

"When this happens, I like to boot with a live cd (knoppix,ubuntu,whatever), mount the partition that has /boot (in your case, Im assuming / or /dev/hda2), chroot to that mounted directory, mount proc (mount -t proc /proc) then call grub-install (in your case "grub-install /dev/hda")

Set the first partiton (XP) as the active partition (or bootable flag- whatever)

See if that doesnt get you somewhere." 

"I agree with livecd, but you don't need to go to the trouble of chrooting to grub install.

Just boot from a livecd, run grub at a prompt then set it up:

root (hd0,1)
setup (hd0)

This will write grub to the MBR of hda, and load stage 1.5/2 from hda2. This will let you boot in the existing configurations you had, you'll have to edit /boot/menu.lst to add your Vista boot, though."

I think the commands offered above might help but I don't know what they mean or how I'm supposd to get to them.

---

### Post by notbitmonk on 2007-08-16
I figured out what my problem was.  For some reason, during installation, the instructions on where to look the OSs were pointing to my IDE drive not my SATA.  Although I wasn't able to fix it during reinstall Windows also copied its installation files to this drive instead of the SATA drive.  What I did was disconnect the power supply to my IDE drive so it won't be recognized and I was able to install both OSs.  Upon finishing installation, I shut down the machine and reconnected the drive.

---

