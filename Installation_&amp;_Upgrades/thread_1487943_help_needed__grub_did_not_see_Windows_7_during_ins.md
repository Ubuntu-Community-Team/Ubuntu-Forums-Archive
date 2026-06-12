---
title: "help needed : grub did not see Windows 7 during install"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by Beowulf.1000 on 2010-05-19
Grub does not see my Windows 7 during Ubuntu (or Xubuntu, tried both) 64 bit install. Thus once ubuntu is installed I do not have the option of booting into my Windows 7 operating system. I need help fixing this!

Hardware:
 1st sata drive is Windows 7 (ntfs) that has two partitions, one for Windows 7, another for some music composition software.
 2nd sata drive is a data drive (ntfs)
 PATA (ide) drive (hda) has Ubuntu on it, and is where I installed grub during install

 I reconfigured BIOS so that boot (first) drive is the PATA drive.


Here is the output from 'fdisk -l'

beowulf@beowulf-desktop:/etc/default$ sudo fdisk -l

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2407c154

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       34103   273926144    7  HPFS/NTFS
/dev/sda2           34103       48642   116782080    7  HPFS/NTFS

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xed0ea986

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953512448    7  HPFS/NTFS

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c3ff9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       37333   299869184   83  Linux
/dev/sdc2           37333       38914    12699649    5  Extended
/dev/sdc5           37333       38914    12699648   82  Linux swap / Solaris
beowulf@beowulf-desktop:/etc/default$ 




How can I get grub modified so that my Windows 7 operating system is visible and is in the grub menu listing?

I am a bit nervous about these errors when I run 'sudo update-grub'

beowulf@beowulf-desktop:/etc/default$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
ERROR: nvidia: wrong # of devices in RAID set "nvidia_eahecbea-0" [1/2] on /dev/sda
ERROR: keeping degraded mirror set "nvidia_eahecbea"
done
beowulf@beowulf-desktop:/etc/default$ 



Here is my /etc/default/grab file contents:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by lindsay7 on 2010-05-19
[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

If this does not work see this,

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Beowulf.1000 on 2010-05-19
> **lindsay7 said:**
> [http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

Well I have grub on my ubuntu system, recovering it is not the problem. It exists (the grub bootloader), it just did not install with Windows as a dual boot option like ubuntu has ALWAYS done in the past for many many  years. Something is really messed up with 10.4, as I have never had this problem, not even as recent as a month or two ago with 9.10.

I manually added Win7 to the grub menu by adding an entry to /etc/grub.d/40_custom but now when I see the menu entry during booting and choose it I get 'no such disk'. I did do a 'sudo update-grub' but I keep getting that weird nvidia error (my motherboard uses the nvidia nforce chipset, but this was working fine before with ubuntu 9.10) and I do not see Windows 7 added during the grub update.

Going to go boot now, play with grub menu entry for windows. Here is what I added to 40_custom

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Adding Win 7 to GRUB Bootloader" >&2
cat << EOF
menuentry "Windows 7" {
set root=(hd0,1)
chainloader (hd0,1) +1
}
EOF

---

### Post by lindsay7 on 2010-05-19
Did you try this, from the second link I gave you?

How to restore the Windows Vista or 7 bootloader

To restore the Windows Vista/7 bootloader, you must first boot off your Windows Vista/7 installation DVD.
If you have one of the many OEM computers that didnt come with a Vista/7 installation disk, you can get the same effect with a Vista recovery disk, which you can download for Vista or Win 7.
When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer."

On the next page, if it finds your Windows Vista/7 installation, make sure it is UNSELECTED before clicking next.
Then click on "Command prompt". From there, type in the folowing:



Code:

bootrec.exe /fixboot

Code:

bootrec.exe /fixmbr

Now close the two windows and click "Restart."

Take out your Vista/7 DVD and hopefully, you will be left with your Windows Vista/7 Bootloader.




Here is the link to get a repair startup disc if you need one.  You can use the vista disc too,


[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
__________________

---

### Post by Beowulf.1000 on 2010-05-19
SOLVED! I played with the grub boot menu when it appeared, using the handy 'e' key to edit an entry and then to <ctrl><x> to try running that entry. For the Windows 7 entry (created by editing /etc/grub.d/40_custom and then running 'sudo update-grub') I just played with the entry until i found this worked for the Windows 7 entry:

[INDENT]set root=(hd1,1)
chainloader +1[/INDENT]

and that is all I had for the entry, and was able to then do a Ctrl-x to execute it and boot into my Windows 7 Ultimate 64 bit on my C: drive (first sata drive). Mind you I have the GRUB bootloader and Ubuntu installed on my PATA ide drive -- I have learned the hard way NOT to install GRUB to the drive that I have windows on, thus never interfering with the Windows MBR bootloader.

So to summarize, I edited /etc/grub.d/40_custom 
 [INDENT] [FONT="Courier New"]$ sudo gedit /etc/grub.d/40_custom [/FONT][/INDENT]
so that I had this in that file:
[INDENT]
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.

echo "Adding Win 7 to GRUB Bootloader" >&2
cat << EOF
menuentry "Windows 7" {
set root=(hd1,1)
chainloader +1
}
EOF[/INDENT]

Save the above edited file, then in a terminal run
 [INDENT][FONT="Courier New"]$ sudo update-grub[/FONT]
[/INDENT]
presto shazam you have a GRUB2 bootloader that shows Windows 7 that can be booted.
 :guitar:

---

### Post by Beowulf.1000 on 2010-05-19
Thank you for your help Lindsay. 
Problem solved, turned out to be pretty easy to fix.
I think the main thing throwing me off was thinking the Win7 boot partition was the first (0) on hd1 but in fact it appears to be on hd1,1 not hd1,0 as I would have thought. Tinkering with the grub boot menu listing using the 'e' option to edit entries and try them out with Ctrl-x let me deduce that I needed hd1,1 to boot Win7.

---

