---
title: "PPC Boot error"
date: 2005-04-27
forum: Installation &amp; Upgrades
---

### Post by mattweidner on 2005-04-27
Hello all!

I have read so many good things about Ubuntu I decided to give it a whirl.  I have been using Linux since 1994 mostly on intel platforms, mainly Red Hat up until they released Fedora Core, now I'm a Slackware geek.

I had an old iMac sitting here doing nothing and saw Ubuntu had a PowerPC version of Hoary.  The install went fine, however, being a Debian and PowerPC newbie, I ended up installing several times.  I've got what I think is a good install now, that is, no errors reported during the installation, but the machine fails to boot Linux.

When booting from the hard drive, the bootstrap program appears to locate the kernel and initrd, the screen clears and I receive:

audit(1114629007.086:0): initialized
hda: MDMA, cycleTime: 120, accessTime: 75, recTime: 45
hda: Set MDMA timing for mode 2, reg: 0x00211526
request_module: runaway loop modprobe binfmt-0000
request_module: runaway loop modprobe binfmt-0000
request_module: runaway loop modprobe binfmt-0000
request_module: runaway loop modprobe binfmt-0000
request_module: runaway loop modprobe binfmt-0000

I have done a bit of research on the binfmt error message and find it maybe related to initrd not being read correctly due to corruption or not being created correctly:

[http://ds9a.nl/klogbot/?year=2004&month=11&day=2&hour=21.5](http://ds9a.nl/klogbot/?year=2004&month=11&day=2&hour=21.5) 

or a problem with the linux-scsi subsystem:

[http://www.ussg.iu.edu/hypermail/linux/kernel/0406.1/1168.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0406.1/1168.html) 

or, just as a guess, the kernel is unable to identify the type of binary file it's trying to execute.

The kernel used to boot the installation CD runs perfectly on this iMac, so I'm puzzled as to why the stock kernel installed for Ubuntu won't!!  Are the kernels THAT different?

 ](*,) 

Thanks!

matt

---

### Post by mattweidner on 2005-04-28
BUMP!!


No one else has seen this on an iMac???  it's quite a show stopper.

Still  ](*,)

---

### Post by mattweidner on 2005-05-07
OK!!  Having taken a break from this problem for a week or so, I decided to attack it again.

After performing a fresh install of Hoary, I booted the install CD in rescue mode and mounted my root partition.  I downloaded and installed a precompiled 2.6.11.8 kernel from ppckernel.org:

[linux-official-stable-pmac-2.6.11.8.tar.bz2](http://www.ppckernel.org/download/official-stable-pmac/linux-official-stable-pmac-2.6.11.8.tar.bz2)

copied the kernel and modules into the appropriate location, created a symlink for vmlinux to point to the new kernel, then rebooted.

My iMac now boots ubuntu just fine!!    :grin: 

I don't know if this is specific to linux-2.6.10 or if it is an ubuntu kernel configuration issue.

I hope this solution will be useful for someone else.

---

### Post by Roberto FURLAN on 2005-06-28
Hello!
I'd like to install Ubuntu in an old PowerPC 6500/275 with SCSI HardDisk, 64M RAM, but I can't boot from CD. Neither if I press "C" at the starup nor if I select the CD as startup disk. The smiling Mac appears, but nothing happens from here onwards.

What can I do?

Thak you for help!

Roberto FURLAN

---

### Post by marion on 2005-09-04
[QUOTE=mattweidner]...copied the kernel and modules into the appropriate location, created a symlink for vmlinux to point to the new kernel, then rebooted...[/QUOTE]

And what would the appropriate locations be?

I'm having the exact same issue, and I understood how you fixed it, I just don't know where to dump the files and where to link them back to.

If there a conf file I should look in for the locations?

---

### Post by mattweidner on 2005-09-05
[QUOTE=marion]And what would the appropriate locations be?[/QUOTE]

Untar the archive you downloaded from ppckernel.org (i.e. tar -jxvf linux-official-stable-pmac-2.6.13.tar.bz2) and just use their directory structure.  There is a "boot" directory and a "lib" directory, these correspond with /boot and /lib respectively.

Good Luck!

---

### Post by marion on 2005-09-06
I can get to the shell, but when I mount the CD ROM, all I get is a bunch of gibberish, and can't copy the file over to the harddrive.

I've tried using sudo and not using sudo, but the same result.  I've tried:

sudo mount /dev/hdc
sudo mount /media/cdrom
sudo mount /media/cdrom0
sudo mount /cdrom

... and may be a few others each with sudo and without.  I'm obiously missing something, but I don't know what it is.

Any help would be appreciated.

---

