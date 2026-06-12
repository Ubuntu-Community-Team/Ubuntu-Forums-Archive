---
title: "attempting to boot from file on ideacenter 300 stick pc"
date: 2016-11-05
forum: Installation &amp; Upgrades
---

### Post by cstmcomps on 2016-11-05
I have a Lenovo Ideacentre 300 stick pc that can boot from a file.  I have followed the instructions on several other forums to setup the boot usb with Xubuntu 16.04.  I am having problems getting the bootia32.efi file setup.  The problem is that I don't have another Linux pc to do the setup.  Can somebody please try the instructions here: [https://github.com/lopaka/instructions/blob/master/ubuntu-16.04-install-asus-x205ta.md]("https://github.com/lopaka/instructions/blob/master/ubuntu-16.04-install-asus-x205ta.md") which is:


# Create the 32bit boot loader and place it on USB install media
apt-get install git bison libopts25 libselinux1-dev autogen \
  m4 autoconf help2man libopts25-dev flex libfont-freetype-perl \
  automake autotools-dev libfreetype6-dev texinfo
git clone git://git.savannah.gnu.org/grub.git
cd grub
./autogen.sh
./configure --with-platform=efi --target=i386 --program-prefix=''
make
cd grub-core
../grub-mkimage -d . -o bootia32.efi -O i386-efi -p /boot/grub \
  ntfs hfs appleldr boot cat efi_gop efi_uga elf fat hfsplus iso9660 linux keylayouts \
  memdisk minicmd part_apple ext2 extcmd xfs xnu part_bsd part_gpt search search_fs_file \
  chain btrfs loadbios loadenv lvm minix minix2 reiserfs memrw mmap msdospart scsi loopback \
  normal configfile gzio all_video efi_gop efi_uga gfxterm gettext echo boot chain eval
cp bootia32.efi /mnt/EFI/BOOT/

umount /mnt

what I need is the files necessary to put on my USB drive so that I can do the boot from file and get Linux installed on this stick pc.

Thanks

---

### Post by alexjpowell on 2016-11-05
If you have any other PC, you can boot from a live cd or usb and do this

---

### Post by cstmcomps on 2016-11-06
I've tried to.  The problem is that the other computers are windows 8.1 or 10 and also have the same problem.  This new ploy by Microsoft has really make it to where no other OS can be booted at all.  It's so incredibly frustrating.  I have spent the better part of 2 weeks simply trying to get a variety of USB drives to work.  I doubt it's a problem with the drive.  It's a problem with being able to boot another bootloader besides Microsoft's.  Oddly enough on another Windows 8.1 pc in our house you can't even boot a Microsoft USB/CD drive.

Rant over... I really just need to be able to put the completed bootloader on a USB and boot up.  I'm sure that somebody has done it and there's an image floating around somewhere, but I haven't found it.  That's why I've come here, is because you guys eat, sleep, and dream Linux.  That's where I want to be, but in order to be able to I have to be able to boot Linux in the first place.

---

### Post by alexjpowell on 2016-11-07
$ make

/usr/bin/ld: -r and -pie may not be used together
collect2: error: ld returned 1 exit status
Makefile:24257: recipe for target 'disk.module' failed
make[3]: *** [disk.module] Error 1
make[3]: Leaving directory '/home/alex/ideacenter/grub/grub-core'
Makefile:23528: recipe for target 'all' failed
make[2]: *** [all] Error 2
make[2]: Leaving directory '/home/alex/ideacenter/grub/grub-core'
Makefile:10892: recipe for target 'all-recursive' failed
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/alex/ideacenter/grub'
Makefile:3118: recipe for target 'all' failed
make: *** [all] Error 2
alex@alex-Inspiron-7520:~/ideacenter/grub$

I tried but it didn't make

---

### Post by RockTeam on 2017-01-27
I had installed Ubuntu 16.04 on the Lenovo IdeaCentre Stick 300 successfully.

Easy steps

1. Downland favorite distro for AMD64 (for example ubuntu-16.04-desktop-amd64.iso).
2. Prepare USB stick for booting. I used Gparted - we need to have FAT32 filesystem with the boot flag.
3. Copy the ISO file to the USB drive.
4. Copy [bootia32.efi]("https://github.com/jfwells/linux-asus-t100ta/blob/master/boot/bootia32.efi") to /EFI/BOOT/ directory on the USB stick with distro for installation.
5. Insert USB stick into IdeaCentre 300. Once it will be powered on press F2 button to go into EFI menu and select USB drive for booting.

Useful URL:
[https://github.com/lopaka/instructions/blob/master/ubuntu-16.04-install-asus-x205ta.md](https://github.com/lopaka/instructions/blob/master/ubuntu-16.04-install-asus-x205ta.md)

That is all.

---

