---
title: "After Upgraded Kernel It's not in the grub menu when I boot"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by mpsz on 2010-02-01
Hi,

I have a problem.
I upgraded my Kernel to the latest version with the upgrade manager but after it finished it doesn't show the new entries with the new Kernel version in the grub boot menu.

How can I make it show the new kernels?

Thanks!

---

### Post by hemimaniac on 2010-02-01
if you are using legacy grub:

sudo update-grub

if you are using grub2

sudo update-grub2

also there is this one you can use:

sudo dpkg-reconfigure grub-pc

---

### Post by robert shearer on 2010-02-01
What other os's are you booting on this machine ? (if any)

If there are others then which one is the default ?.

---

### Post by kansasnoob on 2010-02-01
First lets see what version of grub you have:

```
grub-install -v
```

Then lets look at the boot/grub directory:

```
ls /boot/grub
```

---

### Post by mpsz on 2010-02-02
Hi! thanks for the answers.

I tried update-grub2 didn't work... update-grub2: command not found
I tried sudo dpkg-reconfigure grub-pc and got grub-pc is broken or not installed


I also have win XP and Win Vista in my grub menu.


The thing is that I updated Kernel ok until kernel 2.6.31-14-generic
Then when I updated the kernel the following versions until the last 2.6.31-17 they don't appear in the grub menu.
I can by pressing "e" key edit the menu and 2.6.31-17 boots ok.


I did grub-install -v and got this:
grub-install (GNU GRUB 0.97)

and at the boot/grub directory:

mariano@linux-desktop:~$ ls /boot/grub
915resolution.mod  efiemu64.o     lvm.mod         reiserfs.mod
acpi.mod           efiemu.mod     mdraid.mod      scsi.mod
affs.mod           elf.mod        memdisk.mod     search.mod
afs_be.mod         ext2.mod       memrw.mod       serial.mod
afs.mod            extcmd.mod     menu.lst        setjmp.mod
aout.mod           fat.mod        menu.lst~       sfs.mod
ata.mod            font.mod       minicmd.mod     sh.mod
ata_pthru.mod      fs_file.mod    minix.mod       sleep.mod
at_keyboard.mod    fshelp.mod     mmap.mod        tar.mod
befs_be.mod        fs.lst         moddep.lst      terminfo.mod
befs.mod           fs_uuid.mod    msdospart.mod   test.mod
biosdisk.mod       gfxterm.mod    multiboot.mod   tga.mod
bitmap.mod         gptsync.mod    normal.mod      true.mod
blocklist.mod      grub.cfg       ntfscomp.mod    udf.mod
boot.img           grubenv        ntfs.mod        ufs1.mod
boot.mod           gzio.mod       ohci.mod        ufs2.mod
bsd.mod            halt.mod       part_acorn.mod  uhci.mod
bufio.mod          handler.lst    part_amiga.mod  unicode.pf2
cat.mod            handler.mod    part_apple.mod  usb_keyboard.mod
cdboot.img         hdparm.mod     part_gpt.mod    usb.mod
chain.mod          hello.mod      partmap.lst     usbms.mod
cmp.mod            help.mod       part_msdos.mod  usbtest.mod
command.lst        hexdump.mod    part_sun.mod    vbeinfo.mod
configfile.mod     hfs.mod        parttool.lst    vbe.mod
core.img           hfsplus.mod    parttool.mod    vbetest.mod
cpio.mod           iso9660.mod    password.mod    vga.mod
cpuid.mod          jfs.mod        pci.mod         vga_text.mod
crc.mod            jpeg.mod       play.mod        video_fb.mod
datehook.mod       kernel.img     png.mod         video.mod
date.mod           keystatus.mod  probe.mod       videotest.mod
datetime.mod       linux16.mod    pxeboot.img     xfs.mod
default            linux.mod      pxecmd.mod      xnu.mod
device.map         lnxboot.img    pxe.mod         xnu_uuid.mod
diskboot.img       loadenv.mod    raid5rec.mod    zfsinfo.mod
dm_nv.mod          loopback.mod   raid6rec.mod    zfs.mod
drivemap.mod       lsmmap.mod     raid.mod
echo.mod           ls.mod         read.mod
efiemu32.o         lspci.mod      reboot.mod

---

### Post by mpsz on 2010-02-13
Any idea? 
Please?

---

### Post by kansasnoob on 2010-02-13
Sorry, I let this one slip by me. OK we know from this (GNU GRUB 0.97) you're using legacy grub but from this:

mariano@linux-desktop:~$ ls /boot/grub
915resolution.mod efiemu64.o lvm.mod reiserfs.mod
acpi.mod efiemu.mod mdraid.mod scsi.mod
affs.mod elf.mod memdisk.mod search.mod
afs_be.mod ext2.mod memrw.mod serial.mod
afs.mod extcmd.mod **[COLOR="Red"]menu.lst[/COLOR]** setjmp.mod
aout.mod fat.mod menu.lst~ sfs.mod
ata.mod font.mod minicmd.mod sh.mod
ata_pthru.mod fs_file.mod minix.mod sleep.mod
at_keyboard.mod fshelp.mod mmap.mod tar.mod
befs_be.mod fs.lst moddep.lst terminfo.mod
befs.mod fs_uuid.mod msdospart.mod test.mod
biosdisk.mod gfxterm.mod multiboot.mod tga.mod
bitmap.mod gptsync.mod normal.mod true.mod
blocklist.mod **[COLOR="Red"]grub.cfg[/COLOR]** ntfscomp.mod udf.mod
boot.img grubenv ntfs.mod ufs1.mod
boot.mod gzio.mod ohci.mod ufs2.mod
bsd.mod halt.mod part_acorn.mod uhci.mod
bufio.mod handler.lst part_amiga.mod unicode.pf2
cat.mod handler.mod part_apple.mod usb_keyboard.mod
cdboot.img hdparm.mod part_gpt.mod usb.mod
chain.mod hello.mod partmap.lst usbms.mod
cmp.mod help.mod part_msdos.mod usbtest.mod
command.lst hexdump.mod part_sun.mod vbeinfo.mod
configfile.mod hfs.mod parttool.lst vbe.mod
core.img hfsplus.mod parttool.mod vbetest.mod
cpio.mod iso9660.mod password.mod vga.mod
cpuid.mod jfs.mod pci.mod vga_text.mod
crc.mod jpeg.mod play.mod video_fb.mod
datehook.mod kernel.img png.mod video.mod
date.mod keystatus.mod probe.mod videotest.mod
datetime.mod linux16.mod pxeboot.img xfs.mod
default linux.mod pxecmd.mod xnu.mod
device.map lnxboot.img pxe.mod xnu_uuid.mod
diskboot.img loadenv.mod raid5rec.mod zfsinfo.mod
dm_nv.mod loopback.mod raid6rec.mod zfs.mod
drivemap.mod lsmmap.mod raid.mod
echo.mod ls.mod read.mod
efiemu32.o lspci.mod reboot.mod

You have mixed legacy grub and grub2 files/directories and that prevents either legacy grub or grub2 from updating properly.

Did you revert to legacy grub from grub2, or if this was an upgrade from Jaunty maybe you upgraded to grub2?

Is there a particular reason that you don't want to use grub2?

---

### Post by kansasnoob on 2010-02-13
BTW I don't care which version of grub you want to use, I just need to know so I give you the proper commands to run :)

---

### Post by kansasnoob on 2010-02-13
Also to simplify things I should see the results of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by mpsz on 2010-02-15
Ok, thanks to all.
I'll post the info today later.

:p

---

### Post by loyo on 2010-02-15
haha, good tips.

---

### Post by mpsz on 2010-02-16
Hi,
I don't know how it happened I just upgraded every time the upgrade manager asked me to.
Something mixed the 2 versions of grub.
I want to have 2.0.
How can I do it?

---

### Post by kansasnoob on 2010-02-17
I need to see the results of the Boot Info Script as I said in post #9. This is easy to fix but I need some system specific info.

---

### Post by mpsz on 2010-02-17
Ok, here's the info from the script
thanks for helping me!

---

### Post by kansasnoob on 2010-02-17
Well I see Win XP on sdd1, Vista on sdd4, and Karmic on sdd3. I do however see an entry for Mac OS X on sdc2 that must have been removed, huh?

And this tells me that you were still booting with grub2 even though legacy grub had been installed:

>  => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #4 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #3 for /boot/grub.


So you must have sdd set as the boot drive in BIOS, but we won't take any chances.

Now we're going to backup the old grub directory anyway but when we reinstall grub2 it will overwrite any old configuration files so if you customized anything you'll have to do that over again.

I'm also going to give you the option of using the newest grub2 packages from Lucid if you'd like, but you'll need to know whether you have 32bit or 64bit Ubuntu, so run:

```
uname -m
```

(64 bit = x86_64, and 32 bit = i686)

So we begin:

```
sudo mv /boot/grub /boot/grub_backup
```

```
sudo mkdir /boot/grub
```

```
sudo apt-get --purge remove grub
```

```
sudo apt-get --purge remove grub-common
```

Now **if you want to use the newest grub2** download the proper "grub-common" and "grub-pc" packages here:

[http://packages.ubuntu.com/lucid/grub-common](http://packages.ubuntu.com/lucid/grub-common)

[http://packages.ubuntu.com/lucid/admin/grub-pc](http://packages.ubuntu.com/lucid/admin/grub-pc)

Just save them to the Desktop (or Downloads folder, wherever you wish) then just double-click the package and gdebi will install it. **(Note: grub-common must be installed first and grub-pc second)**

**If you prefer using the official Karmic packages** just:

```
sudo apt-get install grub-pc
```

Then:

```
sudo update-grub
```

And wait for it to say done, it should find all kernels and both Windows.

Then install to the mbr's of sda and sdd:

```
sudo grub-install /dev/sda
```

```
sudo grub-install /dev/sdd
```

There probably is no real need to install to sda but it also won't harm anything and the old legacy grub mbr is useless now.

That should be it but you'll have a really long list of kernels so I wouldn't be surprised if the Windows entries get "pushed off" the end of the list. They should still show up if you arrow down but once you make sure the newer kernels boot OK after reinstalling it would be a good idea to delete some old ones.

I always like to keep two working kernels just in case the newest one gets hosed somehow. The way I like to do that is just by typing the exact kernel number (ie: 2.6.31-14) into Synaptic's Search window (not the quick or rebuilding search) then you can easily see what to remove from there.

Clear as mud?????????

I'll be gone until late tomorrow evening, but if you have any trouble feel free to send me a brief PM pointing me back to this thread.

---

### Post by mpsz on 2010-02-18
:p
thank you!!!!!!!!
It worked perfect!
I really appretiate your help!!!
:P

---

