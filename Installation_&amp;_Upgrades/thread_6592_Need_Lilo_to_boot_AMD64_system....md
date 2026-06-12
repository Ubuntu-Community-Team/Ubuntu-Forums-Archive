---
title: "Need Lilo to boot AMD64 system..."
date: 2004-11-29
forum: Installation &amp; Upgrades
---

### Post by tjwhaynes on 2004-11-29
I'm a long time Mandrake user who has decided (for various reasons) to jump ship and try a Debian-based distro.

I have an Athlon64 system running on an K8T800 Pro motherboard with 1Gb RAM. I know this system works because I've been running Mandrake 10.1 RC2 on it for a few weeks. When I did the Mandrake install, I had problems with the version of Grub that shipped on that disk and I ended up having to use Lilo instead.

Now I have downloaded and installed the Warty AMD64 iso without problems. I get to the reboot and I get the "GRUB Loading stage1.5" message on the screen and nothing else happens. The disk drive is 120GB SATA and is partitioned with a small 40MB /boot partition as the first partition followed with 2GB swap and then 21GB /home, 60GB / and 35GB /extra.

So now I have a stuck box. I think that the easiest way to complete this install is to get LILO installed during the install process. However, I'm a Ubuntu and Debian newbie and I really don't have a good handle on what I need to do to get LILO installed on the system during the install. So .... HELP!
PLEASE!

Otherwise it'll be another round of CD burning and a Gentoo or FC3 CD set... (ooooo, threats!)

Any help is gratefully received. 

Thanks,
Toby Haynes

---

### Post by jmarc on 2004-11-30
In more or less the same situation (Ubuntu's grub installed on HD or on floppy
clear the screen and then seems to freeze-- it was with an AMD but not an AMD-64),
I've been able to boot on Ubuntu's live CD and use it as a rescue disk.

Yours,

-- 
Jean-Marc

---

### Post by tjwhaynes on 2004-12-01
[QUOTE=jmarc]In more or less the same situation (Ubuntu's grub installed on HD or on floppy
clear the screen and then seems to freeze-- it was with an AMD but not an AMD-64),
I've been able to boot on Ubuntu's live CD and use it as a rescue disk.

Yours,

-- 
Jean-Marc[/QUOTE]
 Interestingly, the Gnoppix 0.8.2.2 live CD (i386, based on warty) won't boot on my machine, failing with the same hang.

Using the ubuntu install CD, I spent a couple of hours hacking around with the provided shell seeing if I could get lilo installed on the machine. In the end I got the network up via the installer, manually mounted up the partitions and chroot'd myself into the drive, copied a 32bit version of LILO over to my AMD64 box from my FC2 laptop and installed LILO on the MBR. Now the machine boots but can't load any modules once the kernel comes up (QM_MODULES function not implemented) which might be a problem with module-init-tools or might just be borkage due to the amount of mucking around I did.

I also tried to get apt up and running - I added universe into /etc/apt/sources.list and ran apt-get update, thinking I might be able to get a "real" ubuntu copy of lilo installed rather than the hacked mess I moved over. apt-get replies that lilo is referenced by another package but is not available. That makes me wonder where it is available from? I browsed through a couple of ubuntu repositories but couldn't find an AMD64 version. Is Lilo available for amd64 with Ubuntu at all?

Oh well, it's day 3 of the boot loader fight now. I have some leads on options to pass to GRUB to try and get passed the hang. There are bug reports on the Redhat fedora bugzilla for GRUB hangs too. I'm wondering whether I have a buggy BIOS which is messing up the LBA support so I'm going to try --force-lba=on and --force-lba=off in the GRUB configuration tonight and see whether that gets me any further.

Thanks,
Toby Haynes

---

### Post by tjwhaynes on 2004-12-02
FINALLY!

I have now successfully located a lilo amd64 deb, installed it, built a lilo.conf and installed lilo into the MBR and successfully booted the kernel. It now hangs on "Starting hotplug subsystem" but that is another mystery to solve.

For those of you who wish to perform this act of prestidigitation, here's how I did it. This also serves as a reminder to me in case I have to do this again!

Do the install as normal. Let it install the grub bootloaded but DO NOT FINISH THE INSTALL.

Switch to the one extra terminal available (Alt-RightCursor) and press Enter to start it up.

Now the filesystem in / is a ram filing system and we need to install stuff to disk. My disk system is a SATA drive with partitions which map as 

/dev/scsi/host0/bus0/target0/lun0/part1  - /boot
/dev/scsi/..../part6  - /home
/dev/scsi/..../part7  - /
/dev/scsi/..../part8  - /extra

To mount these, use

mkdir /mnt
mkdir /mnt/harddrive
mount /dev/scsi/host0/bus0/target0/lun0/part7 /mnt/harddrive
mount /dev/scsi/host0/bus0/target0/lun0/part1 /mnt/harddrive/boot
mount /dev/scsi/host0/bus0/target0/lun0/part6 /mnt/harddrive/home
mount /dev/scsi/host0/bus0/target0/lun0/part8 /mnt/harddrive/extra

Now you need to link up the /proc filesystem as well. This is a little more tricky as you need to use a version of mount which supports --bind. Thankfully the version that is installed on the harddrive does but alas the version on the ramfs does not.

/mnt/harddrive/bin/mount --bind proc /mnt/harddrive/proc -t proc

Now we dive into the harddrive and make the filesystem look "normal"

chroot /mnt/harddrive

At this point, you are in the freshly install Ubuntu box via the backdoor. If you are chasing the lilo amd64 binary, you need to add a debian repository which supports it - I used the ones off the debian-amd64 port.

Add the following line (or similar) to the /etc/apt/sources.list file

deb [http://debian-amd64.alioth.debian.org/pure64](http://debian-amd64.alioth.debian.org/pure64) unstable main contrib non-free

apt-get update
apt-get install lilo

Now configure lilo:

liloconfig

I had to edit the /etc/lilo.conf file to sort out various problems, such as switch to text start up, add initrd lines to each image (if you have a SCSI or SATA-drive you are booting from, you NEED this). boot=/dev/sda, root=/dev/sda7 for my case (see above).

Check your config with 

lilo -v -t

and update the MBR on the drive with 

lilo -v

Assuming that all of this has worked, unpick yourself from the chroot jail and unmount the harddrive.

exit
umount /mnt/harddrive/boot
umount /mnt/harddrive/home
umount /mnt/harddrive/extra
cd /
umount /mnt/harddrive/proc
umount /mnt/harddrive

At this point, you can switch back to the installer and let it reboot the machine, or you can drive it yourself with 

shutdown -r now


I have no idea if all this is useful to anyone but it involved a lot of head scratching to get this far so if even one person saves a few minutes of pain, I'll consider this worth it. If the developers of the Warty AMD64 CD could PLEASE put LILO onto the install disk and make it an option, that would be much appreciated.

Thanks,
Toby Haynes

---

### Post by ssam on 2004-12-08
I am getting the hang at "Starting hotplug subsystem", but have a completely different set up.

i have a lovely via epia MII 6000 fanless 600Mhz, 512 ram, 120gb ide hd.

i did a fairly standard install, grub as my bootloader. installed all the updates over my cisco aironet 340 wifi card. and then it asked me to login and i get a nice woring desktop.

reboot and it hangs at "Starting hotplug subsystem"

seems that if i start from cold then it boots ok (well it waits there for a while, but moves on) , but if a reboot it hangs longer than my patience.

dont quite know what it means, but i guess the fault is not with lilo, sata or amd 64s

sam

---

### Post by ssam on 2004-12-08
played some more, and it seems to help not having my usb keyboard plugged in during booting

---

