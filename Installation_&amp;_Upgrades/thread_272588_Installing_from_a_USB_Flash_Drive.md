---
title: "Installing from a USB Flash Drive"
date: 2006-10-06
forum: Installation &amp; Upgrades
---

### Post by ofanite on 2006-10-06
Well, I went through a frustrating few hours today, and thought I might save some folks the trouble.  I have a machine which effectively has no optical drive, but it *can* boot from a USB device, so I thought I would install from a little key drive I had.  The problem was I couldn't find a good set of directions for doing this, and even when I did they seemed to make assumptions about how big the key drive was, and the one I had was very small (64MB). Even more fun, they didn't seem to work very well.  ](*,)

Here's what I did to overcome the problem.  I was working with a dapper workstation at the time, trying to make an edgy installer, but you can easily tailor the distro specific bits to your liking.

First, prepare your system:

```
sudo apt-get install lilo dosfstools util-linux syslinux
```

That should give us all the utilities we need.  Note: do **not** follow the instructions lilo gives you.  We aren't using it for a bootloader, and we don't want it to install in the boot record.  Next, put in your keydrive.  My drive recognized as sdb, but your mileage may vary.  Check for your device like this:

```
abell@argus:~$ dmesg | grep -C6 "USB Mass Storage"
[17179607.352000] Bluetooth: L2CAP socket layer initialized
[17179607.448000] eth0: no IPv6 routers present
[17179607.476000] Bluetooth: RFCOMM socket layer initialized
[17179607.476000] Bluetooth: RFCOMM TTY layer initialized
[17179607.476000] Bluetooth: RFCOMM ver 1.7
[17182459.364000] usb 5-7: new high speed USB device using ehci_hcd and address 5
[17182459.576000] Initializing USB Mass Storage driver...
[17182459.576000] scsi4 : SCSI emulation for USB Mass Storage devices
[17182459.576000] usb-storage: device found at 5
[17182459.576000] usb-storage: waiting for device to settle before scanning
[17182459.576000] usbcore: registered new driver usb-storage
[17182459.576000] USB Mass Storage support registered.
[17182464.580000]   Vendor: Flash     Model: Drive UT_USB20    Rev: 0.00
[17182464.580000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17182464.580000] SCSI device sdb: 128000 512-byte hdwr sectors (66 MB)
[17182464.580000] sdb: Write Protect is off
[17182464.580000] sdb: Mode Sense: 00 00 00 00
[17182464.580000] sdb: assuming drive cache: write through
abell@argus:~$
```Make sure to replace all my references to sdb with your real disk.  I can't emphasize this enough.  I've replaced all my references to it with $TARGETDISK, so if you want to export an environment variable, you can cut and paste away.

Now make sure it's not mounted so we can work on it:

```
sudo umount `df | grep $TARGETDISK | awk '{ print $1 }'`
```

Now we need to partition it:

```
sudo cfdisk $TARGETDISK
```

Make one primary partition at the beginning of the disk which is the size of the whole drive (or 2GB, whichever is smaller), and make it **bootable** and of type 06 (FAT16).  Then make sure to remember to write the changes to the disk!

Now we need a filesystem on there:

```
sudo mkdosfs -n"Edgy" ${TARGETDISK}1
```

Now pop out that drive and pop it back in.  You should get a volume named Edgy automounted for you in /media/Edgy.  Time to get some files.

```
wget http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/boot.img.gz
gunzip boot.img.gz
sudo mount -o loop boot.img /mnt
sudo cp -r /mnt/* /media/Edgy/
sudo umount ${TARGETDISK}1
sudo syslinux ${TARGETDISK}1
sudo lilo -M $TARGETDISK mbr
```

All set!  Boot up from the drive, test that the installer comes up and looks normal, then install away wherever you need an installer.  This method gives you a super lightweight installer ( <10MB ) so you should be able to fit it on any freebie USB drive you come across.

---

### Post by antidrugue on 2006-10-27
Very nice, it does work beautifully. 

Your forgot one step though... After partitionning the USB key, one must mount it in order to copy files on it. Just adding this step would do it :

```
wget http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/boot.img.gz
gunzip boot.img.gz
sudo mount -o loop boot.img /mnt
**sudo mount ${TARGETDISK}1 /media/Edgy**
sudo cp -r /mnt/* /media/Edgy/
sudo umount ${TARGETDISK}1
sudo syslinux ${TARGETDISK}1
sudo lilo -M $TARGETDISK mbr

```

---

### Post by bean1975 on 2006-10-31
Perfect. Do not forget to apt-get install mtools though otherwise syslinux will complain.

Also. Install failed to create initrd, and because of this the machine did not boot. I wanted to run dpkg-reconfigure linux-image-2.6.17-10-386 but to do that, I needed to mount the target drive. This posed a problem because the network connection I used with the laptop is very slow, and I wanted the USB stick used for the install to be able mount the install. For this, I needed to add generic-ide and ext2fs module. So I plugged the USB stick into my desktop (which also runs Edgy) and:

> 
cp /media/usbdisk/initrd.gz /tmp
cd /tmp
gunzip initrd.gz
mkdir 1
cd 1
cat ../initrd | cpio -i
cp -r /lib/modules/2.6.17-10-386/kernel/fs/ext2 lib/modules/2.6.17-10-386/kernel/fs/
cp -r /lib/modules/2.6.17-10-386/kernel/drivers/ide lib/modules/2.6.17-10-386/kernel/drivers
depmod -ab /tmp/1
cd ..
mkfs.cramfs 1 initrd.gz
cp initrd.gz /media/usbdisk
umount /media/usbdisk


Plug back to the notebook, boot, modprobe ide-generic, modprobe ext2 (if not found, run depmod -a again) mounted partitions, removed a failed /initrd.img , ran dpkg-reconfigure as said above, reboot, works.

---

### Post by UBfusion on 2006-11-25
This is a wonderful thread that finally made register into The Forums.

In an unfortunate sequence of events (TM) I am struggling to install Edgy on an Asus P5B-VM with Intel E6300, just to check whether Edgy is HD-Audio aware (specifically whether SPDIF passthrough works or not...).

I am stuck like other Intel 775 chipset users. CDROM is not recognised, and there is no official Ubuntu network boot floppy/CD. So booting from USB is my only option.

I just finished following your instructions, and made the bootable USB stick within an Ubuntu VM client and I have such a terrific feeling of achievement! Thanks so much! I'll let you know if it works....

If this thread had been revised a bit more (e.g. it could mention on top 'first install mtools' and use '/dev/sdb' instead of plain 'sdb', it would become a very nice How-To for newbies like me wanting to install Ubuntu on problematic hardware.

---

### Post by Arekin on 2006-11-30
um it looks nice and all, but how do i do it if im switching over from windows...

---

### Post by mydnight on 2008-01-17
Does this create some sort of GUI net installer, or does this just give me a shell from which I have to use apt to install the rest of the linux system?

---

### Post by Hasmarth on 2008-07-22
> **Arekin said:**
> um it looks nice and all, but how do i do it if im switching over from windows...

Yeah i'm in this same situation. Both my computer are windows, and one doesn't have a CD drive, and that's the one i want Ubuntu on. Any help would be great.

---

