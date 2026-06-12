---
title: "Ok, I need help.... installing to a SATA drive. Lof of my attempts is inside."
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by whistlingtony on 2007-01-17
Intel gives us free chips. They gave us a loaner Core2Duo to play with. I got a Shuttle SD32G2 to throw mine in. I’m a linux nut, and wanted to run only linux. I’m having a devil of a time getting the BEEPing thing to boot. I install it fine using the Ubuntu 6.10 install disk, and then on the first boot it would hang at “Begin: Waiting for root file system... Alert! Not found.” It was annoying, especially as it managed to boot the LiveCD version just fine. FYI, the SD32G2 uses an Intel 945g chipset. Here’s what I’ve attempted so far.

In the BIOS, set the SATA to enhanced mode. This isn’t all that enhanced, it just allows the chip to read PATA drives (which is the fancy term for Parallel ATA, IE: old parallel cable). FYI, I disabled it thinking I was helping, then wondered why it wasn’t booting from my CDROM... Because it couldn’t find it any more. Sigh.

Do an install, you’ll have this problem. This is with Edgy Eft, I wonder how the next version would do?

Boot from the LiveCD again.

Download the latest kernel from Kernel.org and stick it somewhere. I always make a spare partition on drives for moving or storing files in case of Voodoo. I put mine there.

make a temp directory (mkdir blah), move into it (cd blah), and then chroot into it (sudo chroot .). You are now inside your installed system. I mounted my spare partition, then copied the linux source to the /usr/src directory. I understand that is bad form these days. Tough. I then created a symlink to it (ln -s linux-2.6.19.2 linux).

Now, my newly installed system does not have GCC, MAKE, or Libncurses5-dev, all of which I need to configure and compile my new kernel. Sigh.... Gettum. (apt-get install gcc make libncurses5-dev)

Configure a new kernel:

    *
      (make mrproper)
    *
      (make menuconfig)
          o
            I selected the Pentium M as my chip. It seemed to work. There was no option for C2D.
          o
            compile the drivers for file systems and SATA/IDE, etc directly into the kernel. It’s just easier
          o
            Put in all the other good stuff too. Automatic kernel loading, network packet filtering, 802.11 options, your network cards, etc, etc, etc...
          o
            They choose the oddest defaults sometimes, don’t they?
    *
      (make bzImage)
    *
      (make modules && make modules_install)

Copy your new kernel to /boot (cp arch/i386/boot/bzImage /boot/whatevername-2.6.whateverrelease).

Now edit your Grub file and add in your new kernel as a bootable choice. (nano /boot/grub/menu.lst) Make a backup before you change anything!!!!!!!!!!!

Right... Now, notice I didn’t make an initrd image. As I understand it, we don’t need one because all of our file system and important hardware drivers are compiled right into the kernel.... Gulp. I hope.

Reboot and give her a whirl.

Curses! VFS: Cannot open root device “<NULL>” or unknown-block(8,1) Please append a correct “root=” boot option kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(8,1)

Son of a Glitch! So, if I understand that correctly, the bloody thing can’t find my root partition? Hmm..... Lets take a gander at /etc/fstab.

Well... in my /etc/fstab file my / is commented out and there is a UUID=manymanyhexnumbers in it’s place. Err... I’m a bit behind, what is that crud? Right... Lets fiddle with this then.... MAKE BACKUPS!!!!

I deleted all that UUID stuff and made it look like I remember a fstab file looking like. Holy Beep, it worked!

reboot. Naturally, it doesn’t work again. WTH?

Ok, so lets embrace this whole UUID thing. It looks like it is a good idea once I read up on it. Instead of using device codes to mount things, IE: /dev/sda4 should mount on /myusbstick, we use a unique identifier. It used to be when I plug my usb stick into a different USB port and it shows up as /dev/sda5 instead of /dev/sda4, it wouldn’t mount properly with the old /etc/fstab rules. By using a unique identifier(why the hell does it have to be so long!) it gets properly mounted no matter what port I plug it into. Cool...

Ok, so I put the UUID back into /etc/fstab and I put a root=UUID=lotsahexnumbers into /boot/grub/menu.lst.

Should work now right? Reboot... No!

VFS: Cannot open root device “<NULL>” or unknown-block(8,1) Please append a correct “root=” boot option kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(8,1)

All my device drivers are compiled directly into the kernel. I was under the impression it wouldn’t need an initrd.img to boot. Huh...

Perhaps if I slather on that initrd.img? Son of a biscuit...... Perhaps I should go in and enable every stinking SATA driver too. Alternatively, I could try a Dapper Drake install. As I read it, this whole UUID thing is new to Edgy. Hrm.... I can spare some Hard Drive space for that.

Ok, trying an initrd.img. I enabled every SATA option as a module that was not previously configured into the kernel. I made an initrd.img with (update-initramfs -k 2.6.19.2 -c) afterwards. Here goes everything... I updated my /boot/grub/menu.lst to include the initrd.img for my 2.6.19.2 kernel....

I get no more message about not having a root device. Now it just waits at Begin: waiting for root file system... Lame.

Hmm... OK, so lets install Dapper(version 6.06) Ubuntu. Installs fine from the Live CD. Boot into it... and... Begin: Waiting for root file system... Done. Alert! does not exist. Dropping to a shell!

Huh... So, they have no UUID’s in their /etc/fstab or /boot/grub/menu.lst. it’s all by /dev/sdX. Why the BEEP can’t it find the BEEPing root? Lame... When I drop into a shell, I can mount the hard drive just fine. It reads just fine. So, what the heck is this waiting for root crud all about? Time to read more I guess....

Ok, so since Dapper doesn’t work I’m going back to Edgy. Edgy installed. I have a list of modules needed to read the SATA hard drive from the Dapper live CD. I’m making sure they are present as modules in a new 2.6.19.2 kernel. Specifically I’m using sg, libata, ide_generic, sd_mod, ata_piix, scsi_mod, usb_storage, ide_cd, cdrom, piix, and generic. That should cover all my SATA and PATA needs. This is NOT including the intel and JMicron selections in the SATA category. Kernel Made. both /etc/fstab and /boot/grub/menu.lst are using UUIDs. They match what I get when I use the live CD. an initramfs is made and in place. a System.map is made and in place....

Almost everything is compiled as a module... even the stuff they said not to. :D I have to see..... And isn’t that the job of the initramfs anyway?

For the record, I am using (dumpe2fs -ob /dev/sda1|grep UUID) to find the UUIDs that I need.

ARGH!!! same thing. Begin: Waiting for root file system...

Think.. Think.... the initramfs is working. The system has the modules to load for the USB, network, etc. What’s it doing wrong? might the UUIDs be wrong? Those are supposed to be set when you create the partitions right? They’re not supposed to change. What’s wrong here?

the CDrom is on PATA, module for that is piix. The SATA hard drive is on SATA, module for that is ata_piix. double check that I have those.... and I’m going to bed. Frell This.

---

### Post by Theimon on 2007-01-18
Double post? --> [http://ubuntuforums.org/showthread.php?t=339775](http://ubuntuforums.org/showthread.php?t=339775)

You can always bump your own thread after a day or two. It keeps the forums from becoming a mess :)

For your problem, I thought I had a solution but I see you already tried that one.
Perhaps following this guide will help you sort it out: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)[]("http://ubuntuforums.org/showthread.php?t=339775")

---

### Post by nem75 on 2007-01-25
FWIW, I do have the exact same problems trying to install Ubuntu on a Shuttle SD32G2 with Intel 945G chipset. All live CDs boot just fine, but trying to boot an installed Ubuntu results in the system seemingly trying to find the root partition and failing, throwing me into a busybox shell. From where the root partition can be mounted manually without problems, i.e. all necessary modules etc. are obviously there. What gives?

It should be noted that not even the graphical load screen with the progress bar is shown, it drops right into text mode, whatever this may indicate. It's probably also noteworthy that this happens with Dapper, Edgy and Feisty, and no matter if fstab goes by /dev/sdX or UUIDs (which seems logical since it would need to find the root partition before even being able to access fstab).

I'll try to put the UUID in Grub boot options, and if this fails try a Suse install just for kicks. if anyone else has any bright ideas (or actually ANY ideas at all ;)), please post.

EDIT: booting via UUID or dev/sdX didn't make any difference at all. Trying the Suse install next.

---

### Post by nem75 on 2007-01-26
Ok, found a workaround with the help of Tony's adventures in this case (find his description here: [http://whistlingtony.homelinux.net/doku.php?id=desktop](http://whistlingtony.homelinux.net/doku.php?id=desktop) ).

The long and short of it: it works if you compile all SATA and file system drivers statically into the kernel and boot without initrd. A short step by step instruction:

Boot from the live CD.
Setup your internet connection.
Install Ubuntu.
Don't restart.
Open a terminal window.
```
sudo mount /dev/sdX /mnt
sudo mount /dev/sdY /mnt/boot
sudo chroot /mnt
```
Replace X and Y with the numbers to your root and boot partitions respectively. The second command isn't necessary if you don't have a separate boot partition.

```
apt-get install build-essential kernel-package xmlto libncurses5-dev linux-source linux-headers-generic
cd /usr/src
tar xvjf linux-source-`uname -r`.tar.bz2
ln -s linux-source-`uname -r` linux
cd linux
cp /boot/config-<kernel_version> .config
make oldconfig
make defconfig
make menuconfig
```
<kernel_version> has to be replaced with the version of the live CD's kernel, if in doubt just type "/boot/config-" and then press TAB.

Now configure your kernel according to your hardware. Be sure to select support for SATA (see [http://gentoo-wiki.com/HARDWARE_SATA](http://gentoo-wiki.com/HARDWARE_SATA) plus SATA AHCI driver in the SATA driver section plus intel ICH SATA driver) and the file systems you use (probably ext3 and maybe ext2) and select them to be compiled into the kernel, NOT as modules. Also be sure to select the Inotify support in the File Systems section.

```
make-kpkg binary
cd ..
dpkg -i linux-image<TAB>
```
Of course <TAB> means to press the key.

On my system this would result in incorrect paths in /boot/grub/menu.lst, so you might want to

```
vi /boot/grub/menu.lst
```

and make sure that the paths to the kernel images are correct (starting with /boot/ if you don't have a separate boot partition, starting with /vmlinuz<etc> if you do).

Also make sure that the menu.lst entries to your new kernel don't contain lines starting with "initrd".

Now exit your chroot and terminal and reboot. If your kernel doesn't miss any essential drivers, booting the Shuttle SD32G2 should now boot from hard disk. I'm still not sure if this is an upstart or initrd issue, any input on how to diagnose this would be very much appreciated.

Hope this helps someone.

---

### Post by rutabegaa on 2007-02-16
sorry to bump an old thread -- I was led here by google, looking for issues related to the Shuttle SD32G2. I have not attempted the no-initrd procedure described above. There is an (at the time of this writing) unreleased bios upgrade which I heard rumor of elsewhere. It can be obtained from shuttle tech support and appears to fix the issue.

Prior to the upgrade, I was able to boot from a cd and install, but then unable to boot from the hard drive (as above). In my frustration, I tried several distrubutions... after the bios upgrade, the system booted without a hitch.

I am now happily running with lvm over sata raid, using an initrd.
Thought I'd post this in case it helps someone.

---

### Post by wackowillem on 2007-02-19
Yes, upgrading the BIOS flash is the solution to get the machine booting from your SATA harddisk: go to the shuttle.com website, look for the latest flash upgrade and chuck it on a bootable dos floppy together with Award flash utility from the CDROMS that came with your system. That is is if you still HAVE a floppy drive + bootable disks, otherwise you need to prepare a bootable CD-rom. 
Boot from floppy, install the flash, and after that bob is your uncle. 

Next step: trying to re-install Ubuntu 6.10 doesn't work, because the installation process gets stuck at the screen where you assign your drives ('/'=/dev/sda5 etc). The reported error is : 'no root' (or 'no root partition/disk or something of this kind). I guess this is the same as the 'no partitionable media found' error when trying to install Debian.

But I do manage to boot now on the old Ubuntu installation (the 6.06 release) that was present on the disk. Only one 'minor' problem, the network card (marvell yukon with skge driver) DOES get recognized (a line shows up in the log), but eth0 does not get setup.
Really funny: booting up from live-cd -> the NIC works fine, booting up from hard-disk -> the NIC does nothing.
I guess I'll have to roll my own kernel now ... (although I doubt that it will help).

---

### Post by Mr.Clark on 2007-04-23
What would happen if we took out the IDE optical drive and replaced it with a SATA optical drive?

Might that solve it?

---

### Post by whistlingtony on 2007-07-12
Heheheheh....

Cool, a BIOS fix. Sigh... I forgot about this and reinstalled my machine, only to face the same problem again. Time to go get a bios upgrade. And a Floppy drive. Grrrr......

---

