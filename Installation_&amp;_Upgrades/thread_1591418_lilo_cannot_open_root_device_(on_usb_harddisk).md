---
title: "lilo: cannot open root device (on usb harddisk)"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by Al_ on 2010-10-09
Hi
I try to install linux (ubuntu lucid) on an external usb harddisk. As the laptop can boot from an USB flash stick, but not from a USB harddisk (500 GB Lacie rikiki), I try to install lilo bootloader and kernel on a USB flash stick, but use the USB harddisk as root. I run lilo to install the bootloader on another machine (desktop with Ubuntu lucid) with the USB flash stick and USB harddisk recognized as /dev/sdf (mounted in /media/LILO) and /dev/sdg, respectively.

The laptop shows the lilo boot menu, then boots, but ends with kernel panic:
```
...
md: autorun DONE.
VFS: Cannot open root device "UUID=7ba4..." or unknown-block(0,0)
Please append a correct "root=" boot option; here are the available partitions:
0b00     1048575 sr0 driver: sr
Kernel panic - not syncing: VFS: Unable to mount root fs on onknown-block(0,0)
Pid: 1, comm: swapper Not tainted 2.6.32.25-generic #44-Ubuntu
...

```The UUID is correct for the first partition of the USB harddisk.
My own thoughts:
- the kernel can not load a usb harddisk?
- the disk inaccessible option in my lilo.conf is wrong (see bold lines in lilo.conf)?

I appreciate any ideas how to solve this, after I have spent already several days on it.

My lilo.conf file:```

# see http://tldp.org/HOWTO/LILO-5.html
#
#  Install Lilo on the Master Boot Record of a bootable usb flash drive, e.g., violet competact
boot = /dev/sdf
install = menu
#  The installer will build the following file. It tells the boot-loader where the blocks of the kernels are.
map = /media/LILO/map
compact
prompt
[COLOR=Black][B]disk=/dev/sdg
   inaccessible[/B][/COLOR]
#timeout = 100
# try to use geometric instead of lba32  addressing. Errors should be reported at boot-config time (not at boot time)
# no, geomteric does not work
#geometric
lba32
#  The kernel is stored where BIOS can see it.
image = /media/LILO/vmlinuz
         append="acpi=off pci=noacpi noapic nolapic pnpbios, pci=usepirqmask, pci=biosirq"
# Lilo tells the kernel to mount the following partition as root. BIOS does not have to be able to see it.
         root="UUID=7ba4b03b-6496-4050-8ce8-7855630337d6"
         read-only
```Hardware info:
laptop =  hp / compaq 6910p
USB harddisk: Lacie rikiki 500 GB, ext4 formatted (plus a few GB swap at the upper end)
USB flash: old, noname 256 MB stick, ext2 formatted

---

### Post by oldfred on 2010-10-09
I am not sure lilo has been updated to see ext4 partitions. If you can boot a USB I would think you can boot a external drive? My system showed USB boots none of which worked for a flash drive but then I found the flash drive was actually listed under hard drives.

You can do the same thing with a dedicated /grub or /boot partition.

Herman has info on both grub & grub2 partitions
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)
Chainbooting grub2, install to partition & Make CD or floppy - saikee
[http://www.justlinux.com/forum/showthread.php?threadid=152790](http://www.justlinux.com/forum/showthread.php?threadid=152790)
Herman on separate grub partition:
[http://ubuntuforums.org/showthread.php?t=1320270](http://ubuntuforums.org/showthread.php?t=1320270)
Grub partition slakkie
[http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/](http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/)
grub2 partition
[http://rxezlqu.wordpress.com/2010/04/07/separate-boot-partition-vs-dedicated-boot-partition/](http://rxezlqu.wordpress.com/2010/04/07/separate-boot-partition-vs-dedicated-boot-partition/)

Grub2 partition discussion:
[http://ubuntuforums.org/showthread.php?t=1465772](http://ubuntuforums.org/showthread.php?t=1465772)

---

### Post by Al_ on 2010-10-09
@oldfred: Thanks for your reply. I am also surprised that the system boots from USB flash drive (I tried several, all work; including a 16 GB stick on which I could install entire Ubuntu) but not from the USB harddisk. I have no other USB harddisk, so I can not check whether it is something peculiar to this drive or a general 'feature'. Of course I confirmed that the harddisk can be mounted in a running system, Ubuntu Desktop as well as Windows XP. The latter on the same laptop where I want to boot Linux (I can not use the Win XP harddisk as boot device as it is a corporate laptop with a fully encrypted harddisk that is not even seen from a LiveCD).

I had also tried GRUB previously, with no success. I tried to have /boot on the USB stick and / (root) on the USB harddisk. The best I got was a grub rescue> prompt. So, ending up at a lilo boot menu is already a small success ... Nevertheless, I will look up the links you provided and give GRUB another try.

---

### Post by Al_ on 2010-10-10
So, I re-tried GRUB. Thanks to the very clear instructions in the links provided by oldfred (notably [http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")), I created a GRUB2 boot USB flash stick (commandline only) and get a grub prompt. But then I am stuck again, similar to the lilo attempts.
```
grub> ls
(hd0) (hd0,1) (hd1) (hd1,1)
grub> ls (hd0)
Device hd0: Partition table
grub> ls (hd0,1)
        Partition hd0,1: Filesystem type ext2 - Label "GRUB2" - Last modification time 2010-10-10 08:14:20 Sunday, UUID 8d346542-...
grub> ls (hd1)
Device hd1: Partition table
grub> ls hd(1,1)
         Partition hd1,1: Unknown filesystem
```hd0 is the USB flash stick with the grub2 boot installation. hd1 is the internal harddisk, fully encrypted by ProtectDrive, so the partition is not recognizable (it is ntfs); I know it is the internal drive as the laptop LED flashes briefly when entering [FONT=Courier New]ls hd(1)[/FONT] or [FONT=Courier New]ls hd(1,1)[/FONT]. The LED on the USB flash stick flashes with [FONT=Courier New]ls (hd0)[/FONT] and[FONT=Courier New] ls (hd0,1)[/FONT]. The LED on the external USB harddisk is steady on at all times, never flashes. My conclusion: GRUB2 and the BIOS do not see the USB harddisk at all. Possibly I need to load some modules using [FONT=Courier New]insmod[/FONT], but which modules?

---

### Post by Al_ on 2010-10-10
Finally, it works :P. This is how I did it, in case anybody else has the same issues (steps 4 - 12 are not needed, just for me to test; the on-screen messages in step 8 allowed me an estimated guess, which device the root on my USB harddisk is, ie., /dev/sdb1).

[LIST=1]
[*]copied vmlinuz-2.6.32-21-generic and initrd.img-2.6.32-21-generic from the USB harddisk to the top directory of the USB flash stick (renamed for convenience to vmlinuz and initrd.img); for testing purpose, also copied memtest86+.bin to that top directory
[*]connect USB harddisk and USB flash stick to laptop and power on
[*]hit BIOS startup option key to start from USB (in my case F9)
--> a grub prompt appears
[*]to test:
grub> linux16 memtest86+.bin
[*]grub> boot
--> memtest starts
[*]to boot to busy box: reboot, then
grub> linux (hd0,1)/vmlinuz
[*]grub> initrd (hd0,1)/initrd.img
[*]grub> boot
--> (initramfs) busy box prompt appears, as no root for linux was specified
[*](initramfs) mkdir rikiki
[*](initramfs) mount -t ext4 /dev/sdb1 rikiki
[  517.722124] EXT4-fs (sdb1): mounter filesystem with ordered data mode
[*](initramfs) cd rikiki
[*](initramfs) ls
--> files and directories in root of USB harddisk are listed!!
[*]to boot really: reboot, then
grub> linux (hd0,1)/vmlinuz root=/dev/sdb1 ro quiet splash
[*]grub> initrd (hd0,1)/initrd.img
[*]grub> boot
[/LIST]
What is left to do: a small grub.cfg to automate steps 13 - 15.

---

### Post by oldfred on 2010-10-10
Herman has in his link how to create a grub.cfg. When I created a grub.cfg for loop mounting the ISO on a USB, I just created a file and copied into it some stanza.

You will need something like this.

This uses the links from a standard install, but it looks like you renamed your kernels to the same name? Standard installs have a updated link in / (root) to the kernels in /boot so you do not have to have the exact version numbers if you use the link.

Boot most up2date kernel on sda1:

menuentry "Desktop sda1" {
    set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 ro quiet splash
        initrd /initrd.img
}


I like to use spacer (blank menu entry), reboot & Halt as extra options.
menuentry " " {
set root= 
}

menuentry "Reboot" {
    reboot
}

menuentry "Halt" {
    halt
}

---

### Post by Al_ on 2010-10-14
I was out of town for a few days; now back at Linux.

Rename versus symbolic link: good point. I followed your advice (and Ubuntu standard, as I have meanwhile realized), moved kernel and initrd.img to /boot, and use symbolic links with short names in /.

Re grub.cfg, still to be done. Should be fairly straight forward in /etc/grub.d/40_custom.

Thanks again for your help.

Al_

---

