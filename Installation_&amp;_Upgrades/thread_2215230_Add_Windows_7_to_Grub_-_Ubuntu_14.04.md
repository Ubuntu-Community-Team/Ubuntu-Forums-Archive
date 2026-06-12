---
title: "Add Windows 7 to Grub - Ubuntu 14.04"
date: 2014-04-05
forum: Installation &amp; Upgrades
---

### Post by mark2741 on 2014-04-05
I installed an SSD yesterday and decided to do a clean install of dual-boot Win 7 and Ubuntu 14.04.

Unfortunately, I screwed up! I installed Windows 7 and updated it (took ~3 hours to run all the updates!). I then started the Ubuntu 14.04 install process and chose the "something else" partition option and partitioned the SSD into separate partitions for Windows 7, Ubuntu, and another ext4 partition (for an eventual extra linux distro) during the Ubuntu install.

Everything was going great but then, in my rush, I mistakenly had the root of sda selected, instead of the partition I had created specifically for Ubuntu, and hit next on the partitioner. Fortunately, it looks like my Win 7 install is still there (see below) but grub doesn't appear when I start the computer.

Here is output of sudo parted -l:

mark@mark-ubuntu:~$ sudo parted -l
Model: ATA INTEL SSDSC2CT24 (scsi)
Disk /dev/sda: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  100GB  100GB   primary   ntfs            boot
 2      100GB   240GB  140GB   extended
 5      100GB   180GB  80.0GB  logical   ext4
 7      180GB   230GB  50.0GB  logical
 6      230GB   240GB  10.1GB  logical   linux-swap(v1)


Model: ATA WDC WD1002FAEX-0 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags


mark@mark-ubuntu:~$ 

(I have a second HD that I haven't formatted yet, but will once the SSD is sorted out). 

I tried installing boot-repair but it isn't available yet for 14.04. How do I get the Win 7 in grub?

---

### Post by sikander3786 on 2014-04-05
Just run this command:

```
sudo update-grub
```

Hopefully it would list Windows in the output there. If it does, it will automatically add it to the Grub menu and will automatically set Grub to show up on power up.

If it doesn't, please post the output of the above command in addition to this one:

```
cat /etc/default/grub
```

---

### Post by mark2741 on 2014-04-06
Thanks for helping me.

Here is output of the above commands:

mark@mark-ubuntu:~$ sudo update-grub
[sudo] password for mark: 
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-14-generic
Found initrd image: /boot/initrd.img-3.13.0-14-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
mark@mark-ubuntu:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
mark@mark-ubuntu:~$ 

It's not listing Windows anywhere, but I know the partition and files are still there.

---

### Post by Mark Phelps on 2014-04-06
I  know that 14.04 will be out in final form in a few days, but even folks seasoned with Ubuntu tend to wait a while installing a new release as there are always bugs that the testing did not find and fix in advance.  Installing a Beta version prior to release is asking for even more trouble.

It's apparent that os_prober (the program that actually looks for the presence of OSs on your drive) did not find an MS Windows instance.  When it does, it generates a line something like "Windows 7 (Loader) found on sda1".

In your case, what might have happened to confuse Win7 is that the GRUB loader files got written to sda1 as well as the first Linux filesystem partition.  Since Windows loader files are stored in "Boot" and Linux loader files are stored in "boot", this confuses Windows which doesn't pay attention to the two different folders.  It might also confuse the os_prober (don't know).

So, the first thing I would do is look inside your Win7 OS partition to see if you have BOTH the directories I mentioned above.  You can do that by booting from the Ubuntu install media and, once at a desktop, you should be able to open Nautilus to point to the Windows OS partition and see what directories are present.  If both are there, remove the one named "boot" -- and reboot.

When you're back in Ubuntu, do the "sudo update-grub" again and see if, this time, it finds the Windows loader files.

An alternative is that the Windows loader files got clobbered and are not in "Boot" in the Win 7 OS partition.  IF that is the case, you'll need to restore them.

If you have Win7 install media, you can do that by booting from that media and running Startup Repair three times -- that's right, three times.

If you don't have Win 7 install media, you will need to go online and PURCHASE the Win7 repair CD ISO image from the link, download that to a PC and burn a CD from it:  [http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/") You then boot from that, and run Startup Repair three times.

---

### Post by mark2741 on 2014-04-06
Thanks Mark. Running the Win7 Startup Repair 3 times did the trick. Thanks so much!

I was running 14.04 for the past month without issue and know of the risks but it had been very stable for me, and with a new hard drive (SSD, actually) I wanted to do a clean install and I don't trust doing in-place upgrades on OSes, so 14.04 made the most sense for my situation.

Thanks again!

---

### Post by Mark Phelps on 2014-04-07
Good to see you got it fixed.  Please mark this thread as Solved.

---

