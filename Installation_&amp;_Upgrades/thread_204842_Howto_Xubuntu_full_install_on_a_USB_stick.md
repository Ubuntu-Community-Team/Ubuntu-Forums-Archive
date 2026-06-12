---
title: "Howto: Xubuntu full install on a USB stick"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by MatBi on 2006-06-27
I just succeeded in installing Xubuntu on a 2 gigs USB stick.
To avoid confusion, i'm not talking about a live CD image, but a full installed system, with root and swap (peooow) on the USB key.
This is not a proper howto, it's just a collection of descriptive steps; newbies be aware, it's cryptic and there's no guarantee it works.

**1. Xubuntu install**
Install Xubuntu on a spare IDE hdd, since the normal installer refuses any disk smaller than 2 gigs. Alternatively, you could try to install directly to the USB device with the server install cd or the alternate install cd. 

**2. Partition and format**
Partition the USB stick with cfdisk, the first partition (to be mounted as root) as big as possible, the second as swap (i've got 128 megs for it). Format both (mke2fs -j and mkswap), and make bootable the first one.

**3. Copy to the USB**
The good point of linux is that you don't need expensive backup tools. 
Mount the disk readonly under /mnt/hda and the USB stick (rw) under /mnt/usb, then:
*copy -a /mnt/hda/* /mnt/usb/*

**4. Chroot to the USB stick**
We need to fix the boot loader and create the initrd image, we'll chroot to the USB stick.
[I]mount -o bind /dev /mnt/usb/dev
mount -o bind /proc /mnt/usb/proc
chroot /mnt/usb[/I]

**5. Create a new initrd image**
Edit /etc/fstab so that the root entry points to the USB key; it's /dev/sda1 on my system.
As explained in [this]("http://ubuntuforums.org/showthread.php?t=80811") and other posts, fix the USB kernel modules to be loaded into the image.

**6. Install Lilo**
For some reason, grub refuses to install to a device which is not (at the moment) mapped by the bios, so we'll use good'ol lilo. Not sure if it's specific to my system, an EPIA ME6000, YMMV.
[I]apt-get remove grub
apt-get install lilo[/I]
My /etc/lilo.conf looks like this:
boot=/dev/sda
prompt
timeout=100
lba32
compact
vga=normal
root=/dev/sda1
read-only
menu-title="Apu"
image=/vmlinuz
        label=apu
        initrd=/initrd.img

Now you can install lilo:
*lilo*

**7. Cross your finger and boot**
Looks like we're done, shutdown the machine, unplug the IDE hdd, and reboot.
If you're lucky enough, you'll get no kernel panic or other problems. 
After the lilo screen, my system takes around 30 seconds probing the BIOS, don't be impatient if it takes a little to load the kernel.

**8. Troubleshooting**
I successfully tried this on 2 USB devices: an external hdd and a USB stick (a Corsair Flash Voyager). The USB stick did require some fine tuning in order to boot; in fact, when mounting the root, i was kicked to busybox with the error that the root fs was not (yet) mounted. Here's how i fixed it: i added some "/bin/sleep 5" to the /usr/share/initramfs-tools/scripts/local before the root mount; recreate the initrd image, reinstalled lilo. 

**9. Final considerations**
Mounting swap and root(rw) onto a USB keys may look like a bad idea, because the flash memory lifespan is not infinite. It's the tradeoff you have to accept if you want to have a complete solid state system with no moving part. OTOH, flash memory has improved, and so have anti-wearing algorithms. I've choosed this specific USB stick according to good performance and the 10 years warranty, and i take backups every 2 weeks or so.
I wrote this loosy recipe in hope to be helpful to the community; if you've found this post useful, please drop me a comment.

My longest post so far,
MatBi

---

