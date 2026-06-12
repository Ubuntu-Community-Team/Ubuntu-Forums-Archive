---
title: "[ubuntu] live iso on exfat, grub ok, full boot ng?"
date: 2022-02-19
forum: Installation &amp; Upgrades
---

### Post by breakdaze on 2022-02-19
Quick question. I tried to put an Ubuntu iso on a removable exfat formatted drive, and then do the loop trick to boot a live session from the iso. I figured out that grub has the exfat module, so I loaded that, but it only gets so far in the boot until it halts. Is there an issue with a driver missing in this case? Same grub menu setup works fine on fat32, and ntfs. I noticed once booted into a live session, exfat is supported. To be clear, this sort of thing: [https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)

---

### Post by MAFoElffen on 2022-02-19
IDK. I'm not there looking at it to see what is happening, so I cannot say for sure...

I have setup USB Flash drives to use as Utilities to take with me out on service calls. These USB disks were formatted as FAT23, installed Grub2 to them... Copied ISO files on to them... and setup Grub2 menus to boot those ISO files. 

Here is a sample menu from one to boot an Ubuntu ISO from one of them:
```

menuentry "Ubuntu Desktop ISO" {
 loopback loop /ubuntu.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu.iso noeject noprompt splash --
 initrd (loop)/casper/initrd.lz
}

```

---

### Post by C.S.Cameron on 2022-02-19
Older versions of Ubuntu do not work with exFAT.
Try mkusb to make a Persistent USB.

---

### Post by breakdaze on 2022-02-19
@MAFoElffen Totally understand that one, and I've done it for years. FAT32 works great for that. At a particular cluster size FAT32 is limited to 32Gb, I believe. My exFat drive is 1 terabyte. It's fast too, so I thought it would be cool to do that trick. No matter, a newer faster FAT32 formatted 32Gb USB thumb should be fine for my purposes. I just have older ones at the moment and certain things take a little bit... blink blink blink goes the USB...ah there we go, LOL.

@C.S.Cameron It was the latest Ubuntu iso - version 21.something. As it is, it took me hours to get the data I have onto this drive, so I don't think I will use mkusb, which dd the drive. It's 1 terabyte. I could probably make another partition or just use a different drive FAT32.

For the sake of my question, I will try to post the output of what happens. My grub is on a FAT32 device, and then I point those menu entries to isos on other FAT32 or ntfs drives. Only the exFat hangs at boot when I have the isos there. Is there a way to capture the part of the dmesg that makes it to the console before I get to busybox?

Thanks,

---

### Post by TheFu on 2022-02-19
You can try **Ventoy** if you seek a multi-boot, ISO dropped into a directory solution. The tool makes a few partitions, one for the base ventoy boot stuff, that knows to read the 1st partition for all img/iso files and creates a menu and another that I suppose would be used for data.  I think that ISO/IMG partition can be exfat, NTFS or most of the ext2/3/4 native Linux file systems, but I don't recall the specifics now. Sorry.

Their website says this: FAT32/exFAT/NTFS/UDF/XFS/Ext2(3)(4) supported for main partition

---

### Post by breakdaze on 2022-02-20
@TheFu Thanks, I may try it.

So, the problem must lie in the initramfs not being able to mount the exfat drive, perhaps. Not sure how with busybox, and I did find a reference to a bug with busybox and mounting exfat.

Here is what I see when it drops to busybox:
```
(initramfs)/scripts/casper-premount/20iso_scan: line 49
can't open /dev/sr0: no medium found
```

Usually this menu entry would work (drive label is T7):
```
menuentry "Test Lubuntu iso exfat" {
	insmod exfat
	search -n -l T7 -s
	set isolabel="Lubuntu 20.04.3"
	set isofile=/lubuntu-20.04.3-desktop-amd64.iso
	loopback loop $isofile
	linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile root=live:LABEL=$isolabel ro rd.live.image noeject noprompt
	initrd (loop)/casper/initrd
}
```

$isolabel is the label of the iso as seen when mounted
$isofile is the path and file name of the iso on the drive
search -n -l T7 -s   (means -n (no floppy), -l (label), -s (set found label to root))
It gets through a lot of the dmesg before crashing to busybox.
I will need to look at the (initramfs)/scripts/casper-premount/20iso_scan script, I suppose...

---

### Post by breakdaze on 2022-02-22
Well, I tested the above menuentry and an iso from a FAT32 device, and it works fine from that. I used the search because my grub is on a different drive than the iso. I'm not sure if the root=live:LABEL= pertains to Ubuntu, or just to other distros, does anyone know?

Also, on the Ubuntu man pages, there is a bit about casper, but also a man page about "live-boot." Is this the same thing, and is there a case where the live directory exists on a flavor of Ubuntu?

[http://manpages.ubuntu.com/manpages/focal/man7/casper.7.html](http://manpages.ubuntu.com/manpages/focal/man7/casper.7.html)
Is that all there is as far as casper boot options? Anything for debug, as described for "live-boot" in the below man page?

So, is the below a custom live directory you just set up, then do boot=live?
[http://manpages.ubuntu.com/manpages/focal/en/man7/live-boot.7.html](http://manpages.ubuntu.com/manpages/focal/en/man7/live-boot.7.html)

---

### Post by breakdaze on 2022-02-22
OK, I was playing around some more with trying to boot from an iso from an exfat drive, and once in busybox, I took a look at /proc/filesystems and exfat isn't there, so I guess it's not supported, but maybe there is a way to add the driver to busybox:
```
odev	sysfs
nodev	tmpfs
nodev	bdev
nodev	proc
nodev	cgroup
nodev	cgroup2
nodev	cpuset
nodev	devtmpfs
nodev	configfs
nodev	debugfs
nodev	tracefs
nodev	securityfs
nodev	sockfs
nodev	bpf
nodev	pipefs
nodev	ramfs
nodev	hugetlbfs
nodev	devpts
	ext3
	ext2
	ext4
	squashfs
	vfat
nodev	ecryptfs
	fuseblk
nodev	fuse
nodev	fusectl
nodev	efivarfs
nodev	mqueue
nodev	pstore
	reiserfs
	xfs
	jfs

```

I copied the casper.log to a drive, and uploaded to Ubuntu Pastebin: [https://pastebin.ubuntu.com/p/P5BZSsncKq/](https://pastebin.ubuntu.com/p/P5BZSsncKq/)

I also grabbed to scripts. Unsure why the error is found on line 49 of 20iso_scan script, when it doesn't have that many lines?
```
#!/bin/sh

PREREQ=""

prereqs()
{
       echo "$PREREQ"
}

case $1 in
# get pre-requisites
    prereqs)
           prereqs
           exit 0
           ;;
esac

. /scripts/casper-functions
. /scripts/lupin-helpers

iso_path=
for x in $(cat /proc/cmdline); do
    case ${x} in
        iso-scan/filename=*)
            iso_path=${x#iso-scan/filename=}
            ;;
    esac
done
if [ "$iso_path" ]; then
    if find_path "${iso_path}" /isodevice rw; then
        echo "LIVEMEDIA=${FOUNDPATH}" >> /conf/param.conf
        if [ -f "${FOUNDPATH}" ]; then
            echo "LIVEMEDIA_OFFSET=0" >> /conf/param.conf
        fi
    else
        panic "
Could not find the ISO $iso_path
This could also happen if the file system is not clean because of an operating
system crash, an interrupted boot process, an improper shutdown, or unplugging
of a removable device without first unmounting or ejecting it.  To fix this,
simply reboot into Windows, let it fully start, log in, run 'chkdsk /r', then
gracefully shut down and reboot back into Windows. After this you should be
able to reboot again and resume the installation.
"
    fird
fi

```

Also grabbed the kmsg: [https://pastebin.ubuntu.com/p/CyytbDyVmY/](https://pastebin.ubuntu.com/p/CyytbDyVmY/)

I'm interested in rebuilding the initramfs to include exfat. I found example about how to extract the contents of initrd. Any clues about adding the exfat driver once I do? Once long ago a Linux Mint iso wouldn't load live, so I managed to make a script that rebuilt it, but it was just a matter of copying a couple files. The script was handy for extracting and remastering the iso though. Wonder if I can track it down... probably not after 12 years or whatever, lol.

---

### Post by oldfred on 2022-02-22
You may need to rebuild kernel.
It looks like it has been added to kernel, but whoever builds kernel has to add a flag.
From 2 years ago.
[https://www.phoronix.com/scan.php?page=news_item&px=New-exFAT-For-Linux-5.7](https://www.phoronix.com/scan.php?page=news_item&px=New-exFAT-For-Linux-5.7)

---

### Post by breakdaze on 2022-02-23
It seems to exist as an external module for the kernel packed with 20.04 LTS (5.11.0-27-generic).
```
lubuntu@lubuntu:~$ l -o /lib/modules/5.11.0-27-generic/kernel/fs/exfat
total 115
-rw-r--r-- 1 root 117617 Aug 11  2021 exfat.ko

```

And in the source tree for 5.11

However, after unpacking the /casper/initrd I found it isn't in that file. So, I guess the casper stuff is built differently - the initramfs and/or kernel.

I found a source about how to unpack the /casper/initrd, but not how to recompress it yet. Apparently it is in 3 parts:
[https://askubuntu.com/questions/1260675/why-cant-i-extract-all-of-the-ubuntu-20-04-live-server-amd64-iso-initrd](https://askubuntu.com/questions/1260675/why-cant-i-extract-all-of-the-ubuntu-20-04-live-server-amd64-iso-initrd)

This did work:
```
apt-get install dracut liblz4-tool
/usr/lib/dracut/skipcpio initrd > i1
/usr/lib/dracut/skipcpio i1 > i2
lz4cat i2 | cpio --extract --no-absolute-filenames --verbose
```

Here's the entire /casper/initrd file list from the above commands: [https://pastebin.ubuntu.com/p/9n4tKpvHM3/](https://pastebin.ubuntu.com/p/9n4tKpvHM3/)

From what I understand, the kernel is built with headers that can use the external modules in /lib/modules/5.11.0-27-generic/kernel/fs/

Extracting the iso to a drive and running the live system from the flat on the exfat device yielded a repeated
> /init:  line 49:  can't open /dev/sr0: No medium found

So, yeah, I would need to rebuld the /casper/initrd and possibly the kernel (/casper/vmlinuz) if different than the one loaded in the final boot stage. A uname -a shows it is the same version from busybox though.

I even tried copying the module once in busybox, but I couldn't load the module with kmod nor mount the exfat drive, getting an unknown filesystem type.

---

### Post by breakdaze on 2022-02-23
Ouch, I cut my dominant hand pretty bad, so that sure slows the typing down!

Anyway, I pretty much figured out I need to build a new initramfs for /casper to include the exfat.ko module for loop iso booting from exfat to work.

In the troubleshooting process I learned more about debugging the initramfs.

[LIST=1]
[*]add debug to kernel boot parameter string, fing log in /run/initramfs/initramfs.debug
[*]ensure root device exists: ls -l /dev/[hs]da*
[*]check root= is same device: cat /proc/cmdline
[*]compare: blkid /dev/sda1 with: fstype /dev/sda1 if not same, suspect missing driver or bad format / corrupt volume
[*]mount a drive to copy /casper.log and /run/initramfs/initramfs.debug
[*]must create a dir and manually mount. a usb stick with ext3 is a good option
[/LIST]

Oh, and the message I got about can't mount /dev/sr0 was becuase there was no CD in the drive! not really an error.

Which tool builds the casper initramfs for lubuntu 20.04? dracut or initramfs-tools/mkinitramfs?

---

### Post by C.S.Cameron on 2022-02-24
Try adding exFAT drivers:
```
sudo apt update && sudo apt install exfat-utils -y
sudo mkfs -t exfat /dev/sd[x]1
```
It worked for me.

Ref:[https://blog.programster.org/ubuntu-20-add-exfat-support](https://blog.programster.org/ubuntu-20-add-exfat-support)

---

### Post by breakdaze on 2022-02-24
@C.S.Cameron exfat always worked for me once the live system or full install was up and running. Just can't boot an ISO found on exfat device. The driver isn't part of /casper/initrd

So, since initrd is already an image and part of the ISO, we need to rebuild the initramfs and ISO to make it work.

---

