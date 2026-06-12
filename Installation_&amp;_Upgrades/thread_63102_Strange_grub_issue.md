---
title: "Strange grub issue"
date: 2005-09-06
forum: Installation &amp; Upgrades
---

### Post by casperlingus on 2005-09-06
So I just installed Ubuntu 5.04 (HH), x86-64 on my desktop (AMD 3000+ 64-bit, 1GB RAM).  During the installation it probed my system for other operating systems and found my Windows partition on the same harddrive.  It installed grub and things seemed to work fine until I screwed up something.

I'm not sure what I did to mess it up, but now I can't boot.  On boot, the grub menu shows up with all the appropriate boot options, but when I select any Ubuntu boot option it says:
[B]
root=(hd2,4)
Filesystem type unknown, partition type 0x7
kernel=/boot/vmlinuz-2.6.10-5-amd64 root=sda5 ro quiet splash (this line not exact, but close)
Error 17: Cannot mount selected partition[/B]

Trying to boot the Windows partition from the grub boot menu gave me a similar error, saying "Filesystem type unknown, partition type 0xf" but then gave an "Error 12: Invalid device requested".

I checked the /boot/grub/menu.lst file and everything appeared as it should.  I put in my windows CD and did a "fixmbr" so I could at least boot into Windows and use my computer.  Well on first reboot, grub showed up (not expected) and when I selected Ubuntu, it worked... ?!?!  

I continued using ubuntu for a while not caring what actually happened (booted several times), until I tried booting windows the first time.  I selected Windows from the grub menu... grub froze and then I rebooted and the comp booted straight into windows.  No more grub.

Reinstalling grub using the live CD causes this problem to start over again.

What in the hell is going on?  My theory is that grub is incorrectly writing the partition table, but creating the bootloader correctly.  When I "fixmbr" with the Windows CD, it corrects the partition table but doesn't overwrite the (correct) grub bootloader until first reboot. 

Any suggestions?

Casper...

---

### Post by amohanty on 2005-09-07
> (hd2,4)

How many drives do you have? Per grub spec this tells me that you are asking the bootloader to boot off of the 4th partition on the 2nd drive, where 2nd drive could simply mean that your hdd is the secondary master.

Is that the configuration, if not, could you possibly post your menu.lst and your hw configuration?

AM

---

### Post by casperlingus on 2005-09-07
I suppose it would've been a good idea to post all that... 

I have 3 hard drives:  my system is set up like this:

hda:  cdrom
hdb:  dvd-rw
hdc:  40 GB IDE HD
hdd:  120 GB IDE HD
sda:  120 GB IDE HD (both OSs on here)

sudo fdisk -l produces the following for sda

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2089    16779861    7  HPFS/NTFS
/dev/sda2            2090        4178    16779892+   7  HPFS/NTFS
/dev/sda3            4179        8566    35241546+   7  HPFS/NTFS
/dev/sda4            8567       14596    48435975    5  Extended
/dev/sda5   *        8567       14347    46435851   83  Linux
/dev/sda6           14348       14596     2000061   82  Linux swap / Solaris

/boot/grub/device.map:

(hd0)   /dev/hdc
(hd1)   /dev/hdd
(hd2)   /dev/sda

Here is all the uncommented parts of my /boot/grub/menu.lst file:
[I]
default         0
timeout        10

title           Ubuntu, kernel 2.6.10-5-amd64-generic Default
root            (hd2,4)
kernel          /boot/vmlinuz root=/dev/sda5 ro console=tty0 quiet splash
initrd          /boot/initrd.img
savedefault
boot

title           Ubuntu, kernel 2.6.10-5-amd64-generic Default (recovery mode)
root            (hd2,4)
kernel          /boot/vmlinuz root=/dev/sda5 ro console=tty0 single
initrd          /boot/initrd.img
savedefault
boot

title           Ubuntu, kernel 2.6.10-5-amd64-generic
root            (hd2,4)
kernel          /boot/vmlinuz-2.6.10-5-amd64-generic root=/dev/sda5 ro console=tty0 quiet splash
initrd          /boot/initrd.img-2.6.10-5-amd64-generic
savedefault
boot

title           Ubuntu, kernel 2.6.10-5-amd64-generic (recovery mode)
root            (hd2,4)
kernel          /boot/vmlinuz-2.6.10-5-amd64-generic root=/dev/sda5 ro console=tty0 single
initrd          /boot/initrd.img-2.6.10-5-amd64-generic
savedefault
boot

title           Ubuntu, kernel memtest86+
root            (hd2,4)
kernel          /boot/memtest86+.bin
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd2,0)
savedefault
makeactive
chainloader     +1
[/I]

I can run grub after I've chroot'ed to sda after booting from the live CD.  Typing 
"root (hd2,4)" results in "Filesystem type is ext2fs, partition type 0x83"
"root (hd2,0)" gives me "Filesystem type unknown, partition type 0x7"

I feel like there's a simple solution... a setting somewhere I'm missing, or a messed up line in my partition table... 

-Casper

---

### Post by amohanty on 2005-09-07
Well your menu.last looks right based on you configuration. Heres what I would suggest:

1. In your CMOS setup make sure all your drives are setup as auto.
2. Make sure your boot device is setup to be the SATA device. keep in mind that some bios' treat SATA drives as removable devices.

Finally fixmbr resets the MBR to be point to the ntloader. So you might want to reinstall GRUB once you login to Ubuntu. Instructions are floating around the fora by the dozen.

HTH
AM

---

### Post by casperlingus on 2005-09-08
Okay so I fixed the problem.

Theoretically, my /boot/grub/menu.lst was setup correctly.   However, grub **rearranges** all of your hard drives based on boot order in the bios.  Even though /boot/grub/device.map indicated that my /dev/sda = hd2,  it become hd0 since my bios used it as the first boot device.  

Everything works great now!

Casper...

---

