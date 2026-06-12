---
title: "Startup Manager bugs ???"
date: 2009-11-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2009-11-15
Running the latest incarnation of Lucid 2.6.32-4 with Startup Manager 1.9.13-4ubuntu1. If I try to set up a default operating system e.g. 9.04 kernel -16 it boots the -14 kernel ([[COLOR="Red"]bug[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/startupmanager/+bug/483189")). 
If I try to set up a rescue disk (Advanced tab) and the floppy has the write protect enabled I get an error and then subsequent floppy disks are not found ([[COLOR="Red"]bug[/COLOR]]("https://bugs.launchpad.net/ubuntu/+bug/476202")). 
Has anyone one else seen this and can confirm ?
Thx.

---

### Post by ranch hand on 2009-11-15
As a bunch of us keep trying to get across, SUM is NOT fully compatible with grub2 yet.

I would wait before using it at all.  It will be updated, give the poor guy a chance.

---

### Post by Kevbert on 2009-11-16
Hi Ranch Hand.
Startup Manager was working (to set default OS) when I first started using it. Since then the problem has occurred. The way I look at it is that it's better to raise a bug than just leave it to chance.

---

### Post by wilee-nilee on 2009-11-16
For a short while right before the Karmic RC release SUM was removing grub2 on my computer since then it works on my computer. I wouldn't mess with it in lucid for sure. It is a program that seems to have been patched to some extent but as ranch hand suggests trusting it completely may not be so good. I am a serial reinstaller, and my computers have no data but the operating systems so if any mine goes down I just grab the ISO or thumb and reinstall I know all of the extra stuff I want and can be up and running in maybe 3 hours at the most, I have been doing this for awhile.

---

### Post by kansasnoob on 2009-11-17
> **Kevbert said:**
> Running the latest incarnation of Lucid 2.6.32-4 with Startup Manager 1.9.13-4ubuntu1. If I try to set up a default operating system e.g. 9.04 kernel -16 it boots the -14 kernel ([[COLOR="Red"]bug[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/startupmanager/+bug/483189")). 
If I try to set up a rescue disk (Advanced tab) and the floppy has the write protect enabled I get an error and then subsequent floppy disks are not found ([[COLOR="Red"]bug[/COLOR]]("https://bugs.launchpad.net/ubuntu/+bug/476202")). 
Has anyone one else seen this and can confirm ?
Thx.

I'm very curious to see the output of the following:

```
grub-install -v
```

```
ls /boot/grub
```

---

### Post by Kevbert on 2009-11-18
Command outputs as requested:
```
$ grub-install -v
grub-install (GNU GRUB 1.97~beta4)
$ ls /boot/grub
915resolution.mod  efiemu64.o     ls.mod          reboot.mod
acpi.mod           efiemu.mod     lspci.mod       reiserfs.mod
affs.mod           elf.mod        lvm.mod         scsi.mod
afs_be.mod         ext2.mod       mdraid.mod      search.mod
afs.mod            extcmd.mod     memdisk.mod     serial.mod
aout.mod           fat.mod        memrw.mod       setjmp.mod
ata.mod            font.mod       minicmd.mod     sfs.mod
ata_pthru.mod      fs_file.mod    minix.mod       sh.mod
at_keyboard.mod    fshelp.mod     mmap.mod        sleep.mod
befs_be.mod        fs.lst         moddep.lst      tar.mod
befs.mod           fs_uuid.mod    msdospart.mod   terminfo.mod
biosdisk.mod       gfxterm.mod    multiboot.mod   test.mod
bitmap.mod         gptsync.mod    normal.mod      tga.mod
blocklist.mod      grub.cfg       ntfscomp.mod    true.mod
boot.img           grub.cfg.new   ntfs.mod        udf.mod
boot.mod           grubenv        ohci.mod        ufs1.mod
bsd.mod            gzio.mod       part_acorn.mod  ufs2.mod
bufio.mod          halt.mod       part_amiga.mod  uhci.mod
cat.mod            handler.lst    part_apple.mod  unicode.pf2
cdboot.img         handler.mod    part_gpt.mod    usb_keyboard.mod
chain.mod          hdparm.mod     partmap.lst     usb.mod
cmp.mod            hello.mod      part_msdos.mod  usbms.mod
command.lst        help.mod       part_sun.mod    usbtest.mod
configfile.mod     hexdump.mod    parttool.lst    vbeinfo.mod
core.img           hfs.mod        parttool.mod    vbe.mod
cpio.mod           hfsplus.mod    password.mod    vbetest.mod
cpuid.mod          iso9660.mod    pci.mod         vga.mod
crc.mod            jfs.mod        play.mod        vga_text.mod
datehook.mod       jpeg.mod       png.mod         video_fb.mod
date.mod           kernel.img     probe.mod       video.mod
datetime.mod       keystatus.mod  pxeboot.img     videotest.mod
device.map         linux16.mod    pxecmd.mod      xfs.mod
diskboot.img       linux.mod      pxe.mod         xnu.mod
dm_nv.mod          lnxboot.img    raid5rec.mod    xnu_uuid.mod
drivemap.mod       loadenv.mod    raid6rec.mod    zfsinfo.mod
echo.mod           loopback.mod   raid.mod        zfs.mod
efiemu32.o         lsmmap.mod     read.mod
```
For the second command I assume you really meant my grub.cfg file:
```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="11"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,9)
search --no-floppy --fs-uuid --set c5442f96-2482-4ef2-9ddb-8cae0936a559
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.32-4-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,9)
	search --no-floppy --fs-uuid --set c5442f96-2482-4ef2-9ddb-8cae0936a559
	linux	/boot/vmlinuz-2.6.32-4-generic root=UUID=c5442f96-2482-4ef2-9ddb-8cae0936a559 ro  vga=773  quiet splash
	initrd	/boot/initrd.img-2.6.32-4-generic
}
menuentry "Ubuntu, Linux 2.6.32-4-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,9)
	search --no-floppy --fs-uuid --set c5442f96-2482-4ef2-9ddb-8cae0936a559
	linux	/boot/vmlinuz-2.6.32-4-generic root=UUID=c5442f96-2482-4ef2-9ddb-8cae0936a559 ro single  vga=773
	initrd	/boot/initrd.img-2.6.32-4-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root=(hd1,9)
	search --no-floppy --fs-uuid --set c5442f96-2482-4ef2-9ddb-8cae0936a559
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root=(hd1,9)
	search --no-floppy --fs-uuid --set c5442f96-2482-4ef2-9ddb-8cae0936a559
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set f8d82972d8292ff4
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 7b07b906-3503-45c4-be5f-1825a1813680
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=7b07b906-3503-45c4-be5f-1825a1813680 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 7b07b906-3503-45c4-be5f-1825a1813680
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=7b07b906-3503-45c4-be5f-1825a1813680 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-16-generic (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set 9470ea92-8b37-4d18-8132-925d8f1aa888
	linux /boot/vmlinuz-2.6.28-16-generic root=UUID=9470ea92-8b37-4d18-8132-925d8f1aa888 ro quiet splash
	initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode) (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set 9470ea92-8b37-4d18-8132-925d8f1aa888
	linux /boot/vmlinuz-2.6.28-16-generic root=UUID=9470ea92-8b37-4d18-8132-925d8f1aa888 ro single
	initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set 9470ea92-8b37-4d18-8132-925d8f1aa888
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=9470ea92-8b37-4d18-8132-925d8f1aa888 ro quiet splash
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set 9470ea92-8b37-4d18-8132-925d8f1aa888
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=9470ea92-8b37-4d18-8132-925d8f1aa888 ro single
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set 9470ea92-8b37-4d18-8132-925d8f1aa888
	linux /boot/vmlinuz-2.6.28-14-generic root=UUID=9470ea92-8b37-4d18-8132-925d8f1aa888 ro quiet splash
	initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set 9470ea92-8b37-4d18-8132-925d8f1aa888
	linux /boot/vmlinuz-2.6.28-14-generic root=UUID=9470ea92-8b37-4d18-8132-925d8f1aa888 ro single
	initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sdb5)" {
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set 9470ea92-8b37-4d18-8132-925d8f1aa888
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sdb7)" {
	insmod ext2
	set root=(hd1,7)
	search --no-floppy --fs-uuid --set 90413117-5470-4897-bf4a-2f34e11736b7
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=90413117-5470-4897-bf4a-2f34e11736b7 ro quiet splash
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sdb7)" {
	insmod ext2
	set root=(hd1,7)
	search --no-floppy --fs-uuid --set 90413117-5470-4897-bf4a-2f34e11736b7
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=90413117-5470-4897-bf4a-2f34e11736b7 ro single
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sdb7)" {
	insmod ext2
	set root=(hd1,7)
	search --no-floppy --fs-uuid --set 90413117-5470-4897-bf4a-2f34e11736b7
	linux /boot/vmlinuz-2.6.28-14-generic root=UUID=90413117-5470-4897-bf4a-2f34e11736b7 ro quiet splash
	initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sdb7)" {
	insmod ext2
	set root=(hd1,7)
	search --no-floppy --fs-uuid --set 90413117-5470-4897-bf4a-2f34e11736b7
	linux /boot/vmlinuz-2.6.28-14-generic root=UUID=90413117-5470-4897-bf4a-2f34e11736b7 ro single
	initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sdb7)" {
	insmod ext2
	set root=(hd1,7)
	search --no-floppy --fs-uuid --set 90413117-5470-4897-bf4a-2f34e11736b7
	linux /boot/memtest86+.bin 
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb8)" {
	insmod ext2
	set root=(hd1,8)
	search --no-floppy --fs-uuid --set 2c6db2ba-3902-4683-ab62-6bbc1530c8b0
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=2c6db2ba-3902-4683-ab62-6bbc1530c8b0 ro vga=788 quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb8)" {
	insmod ext2
	set root=(hd1,8)
	search --no-floppy --fs-uuid --set 2c6db2ba-3902-4683-ab62-6bbc1530c8b0
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=2c6db2ba-3902-4683-ab62-6bbc1530c8b0 ro single vga=788
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```
As you can see I am booting more than one 9.04 kernel (Ubuntu my default OS on sdb5 and Kubuntu on sdb7).
The files in boot:
```
/boot$ ls
abi-2.6.32-4-generic         memtest86+.bin
config-2.6.32-4-generic      System.map-2.6.32-4-generic
grub                         vmcoreinfo-2.6.32-4-generic
initrd.img-2.6.32-4-generic  vmlinuz-2.6.32-4-generic

```

---

### Post by kansasnoob on 2009-11-18
That all looks fine.

I've seen some that have "mixed" legacy grub and grub2 files and folders. That impairs SUM big time.

I'm currently still using legacy grub and just recently noticed some regression in SUM performance, so I force-installed the Jaunty versions of grub, grub-common and SUM. Still same thing!

Grub2 continues to be a nightmare on my multi-boot, it always picks up all the OS's but also applies boot stanzas for OS's that don't exist, including repetitive entries for it's own /home!

Frustrating at times:)

---

### Post by Kevbert on 2009-11-18
Grub2 is still in development by the look of it. Even so grub2 version 1.97.1 is now available [[COLOR="Red"]here[/COLOR]]("http://grub.enbug.org/"). This should be the one we use in 10.04 rather than the 1.97 beta4 version. It can't help to design a package built around a piece of beta software...

---

### Post by philinux on 2009-11-18
> **Kevbert said:**
> Grub2 is still in development by the look of it. Even so grub2 version 1.97.1 is now available [[COLOR="Red"]here[/COLOR]]("http://grub.enbug.org/"). This should be the one we use in 10.04 rather than the 1.97 beta4 version. It can't help to design a package built around a piece of beta software...

Cant believe that's not been an update for karmic too. It's been out ages. 25/Oct/09 1.97

---

### Post by kansasnoob on 2009-11-18
In Sid last updated 11/15!

Looking like I should play guinea pig:

[http://packages.debian.org/sid/grub-pc](http://packages.debian.org/sid/grub-pc)

Maybe tomorrow.

---

### Post by Gina on 2009-11-18
I think I'll update to the latest grub2 as well.  I see no sense in using out-of-date software.

---

### Post by ranch hand on 2009-11-18
Wow, that is great to see.  I hope it hits our repos soon.

I will wait until then as I have the bugger purring as is.

If I was having problems I would jump all over it.

---

### Post by Kevbert on 2009-11-19
> **kansasnoob said:**
> In Sid last updated 11/15!

Looking like I should play guinea pig:

[http://packages.debian.org/sid/grub-pc](http://packages.debian.org/sid/grub-pc)

Maybe tomorrow.

Breakage... Tried to download deb and needs dependency (grub-common). Tried to download that and says 'Error: Breaks existing package 'grub-pc' dependency grub-common (= 1.97~beta4-1ubuntu4)'.

---

### Post by kansasnoob on 2009-11-19
It appears to have worked well for me on i386. I first installed the new grub-common package then grub-pc:

[ATTACH]136845[/ATTACH]

On restart it however failed to observe my timout settings so I've just changed that again in /etc/default/grub and when I ran update-grub all looks well:

> lance@lance-desktop:~$ sudo gedit /etc/default/grub
[sudo] password for lance: 
lance@lance-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-4-generic
Found initrd image: /boot/initrd.img-2.6.32-4-generic
Found linux image: /boot/vmlinuz-2.6.32-3-generic
Found initrd image: /boot/initrd.img-2.6.32-3-generic
Found linux image: /boot/vmlinuz-2.6.32-2-generic
Found initrd image: /boot/initrd.img-2.6.32-2-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
Found Linux Mint 8 Helena - Main Edition (8) on /dev/sda11
Found Ubuntu 9.04 (9.04) on /dev/sda5
Found Linux Mint 7 Gloria - Main Edition (7) on /dev/sda7
done


That all looks right, now for another reboot.

---

### Post by kansasnoob on 2009-11-19
> **Kevbert said:**
> Breakage... Tried to download deb and needs dependency (grub-common). Tried to download that and says 'Error: Breaks existing package 'grub-pc' dependency grub-common (= 1.97~beta4-1ubuntu4)'.

Oh, BTW I started by renaming the existing /boot/grub, mkdir a new one, purging grub-pc and grub-common, then I installed the new .debs.

Like:

sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
Be sure to also backup any other custom grub2 files you have using cp, ex: 
sudo cp /etc/default/grub /etc/default/grub.old
sudo cp /etc/grub.d /etc/grub.d.old
sudo apt-get --purge remove grub-pc grub-common

Then I installed the grub-common .deb, and then the grub-pc .deb.

It asked where to install grub during installation, for me that's dev/sda. It also asked a couple other questions and I just accepted the defaults.

I'd suspect these new packages will want to update every time I run updates. May need to lock-version.

---

### Post by kansasnoob on 2009-11-19
Definite improvements IMHO, but no progress regarding SUM compatibility. It does appear to work OK for selecting default OS.

Changing timeout to -1 does what I like, that is making the boot screen wait forever until I make a decision.

I'm impressed enough I may try in the next couple of days (busy right now) setting things up where I'll have legacy grub installed to each of the other OS's / partitions rather than the mbr and then seeing how this version of grub2 likes chain loading to each.

That would make me happy!!!!!!!!

---

### Post by kansasnoob on 2009-11-19
All OS's boot fine, boot times from the moment I hit enter to desktop range from 15 to 17 seconds!

I may just clean up some old kernels and leave it be to see what happens. I'm really impressed :D

Now if SUM catches up, Lucid should be awesome!

I think we should push the devs to get this in Karmic's proposed updates!

I might try to find a related bug report. Suggestions welcome.

---

### Post by Kevbert on 2009-11-19
Kansasnoob. Installed grub2 as per your excellent instructions but for 64 bit.
When purging packages removed Startup Manager as well (but left an icon in System-Admin, so I deleted that). Re-installed startup manager on next boot and when I ran it got the message
> An error occurred while loading or saving configuration information for startupmanager. Some of your configuration settings may not work properly. 
and details 
> Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details &#8212;  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
I'm unable to use Startup Manager as it no longer works for me when setting any OS as default (other than the first entry) :(
Looks like I'll need to manually edit my grub2 files now:(
At least I now get
```
$ grub-install -v
grub-install (GNU GRUB 1.97)
```
No beta software here...
I'll confirm the bug if you raise a new one...

---

### Post by kansasnoob on 2009-11-19
I was just playing with SUM some more in my i386.

Since you can't select -1 in the timeout (I even tried typing it) I have to manually edit the timeout settings every time I even launch SUM.

The rescue floppy feature still fails.

So, sadly, for the time being SUM just doesn't work well at all in grub2!

I do hope they get a new build out in time for Lucid.

---

### Post by kansasnoob on 2009-11-19
Bug report here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/485457](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/485457)

> I just tried the i386 packages of grub-pc and grub-common version (1.97+20091115-1) from Debian Sid's package list in Lucid:

[http://packages.debian.org/sid/admin/grub-common](http://packages.debian.org/sid/admin/grub-common)
[http://packages.debian.org/sid/admin/grub-pc](http://packages.debian.org/sid/admin/grub-pc)

The ability to properly identify all OS's; Lucid, Jaunty, Mint 7, Mint 8, and Win XP was flawless.
Definitely improved over the current beta4 version which would improperly identify various /home partitions as root partitions, including it's own (Lucid's) /home.

My thoughts:

(1) Ideally introduce this in Lucid testing, this way I can also try it with an installation from an upcoming daily build to see how it works with ubiquity.

(2) If all appears well in Lucid then introduce this in Karmic proposed updates.

---

### Post by Kevbert on 2009-11-19
Kansanoob. Confirmed your bug and cross-referenced it to this thread. Unfortunately the version of Startup Manager is the same version in Debian sid (1.9.13-4). I was hoping for a newer version to try with grub2...

---

### Post by kansasnoob on 2009-11-19
I'm guessing that SUM is staffed by folks that have limited resources.

I'll bet they get it done though.

---

### Post by Kevbert on 2009-12-07
It looks like grub2 will be updated to a full release prior to lucid coming out in April:p:p:p

---

### Post by Gina on 2009-12-07
> **Kevbert said:**
> It looks like grub2 will be updated to a full release prior to lucid coming out in April:p:p:pI hope so :)

---

### Post by Kevbert on 2009-12-09
Even with the new grub version (now in the repos) startup-manager still won't set the correct OS for booting (it won't now set any OS).

---

### Post by Kevbert on 2010-01-18
Just installed a clean copy of Lucid A2 with startup-manager. It now selects and boots the correct kernel.

---

