---
title: "HOWTO Update your BIOS using Ubuntu, Grub2, memdisk  and Freedos"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by ghat on 2010-08-04
hello folks... 

I always had trouble upgrading the BIOS on my BOXDG45FC motherboard. Most of the Howto's onlne use the 1.44MB floppy disk images however the intel bios is  about 13M

-rw-r--r-- 1 root root  13M 2010-07-12 09:14 Downloads/IDG4510H.86A.0131/ID0131P.BIO

So here is what you can do after you setup your Ubuntu(or any linux) system.

1. Install the required tools...
```
apt-get update
apt-get install syslinux qemu 

```2. Download the prerequisites...
```

wget 'http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/1.0/fdbasecd.iso'

```3. Prepare grub2 to use memdisk
```

sudo cp -rfp /usr/lib/syslinux/memdisk to /boot
sudo mkdir /boot/images

```4. Create the following file
```

root@pc:~# ls -l /etc/grub.d/50_memdisk 
-rwxr-xr-x 1 root root 661 2010-08-04 09:01 /etc/grub.d/50_memdisk
root@pc:~# cat /etc/grub.d/50_memdisk 
#!/bin/sh

set -e

IMAGES=/boot/images
. /usr/lib/grub/grub-mkconfig_lib
if test -e /boot/memdisk ; then
  MEMDISKPATH=$( make_system_path_relative_to_its_root "/boot/memdisk" )
  echo "Found memdisk: $MEMDISKPATH" >&2
  find $IMAGES -name "*.img" | sort | 
  while read image ; do
      IMAGEPATH=$( make_system_path_relative_to_its_root "$image" )
      echo "Found floppy image: $IMAGEPATH" >&2
      cat << EOF
menuentry "Bootable floppy: $(basename $IMAGEPATH | sed s/.img//)" {
EOF
      prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/"
      cat << EOF
        linux16 $MEMDISKPATH bigraw
        initrd16 $IMAGEPATH
}
EOF
  done
fi

```5. Create a empty image file for freedos
```

dd if=/dev/zero of=/boot/images/fdos-250m-hdd.img bs=1M count=250

```(note the extension of the file is .img as this is the way it is coded in the 50_memdisk. you can choose a smaller size, I just happened to choose 250MB)
6. Install freedos to this image
```
qemu -hda /boot/fdos-250m-hdd.img -cdrom /path/to/fdbasecd.iso -boot d

```Follow the freedos prompts to format the disk, then install the OS on the formatted disk (which is 250MB in this case) You can refer the instructions in the 2nd acknowledgment link below..

To exit out of freedos use 
```

FDAPM POWEROFF

```7. Copy the BIOS utilities into the DOS Image...
```

root@pc:~#sudo -s
root@pc:~# sfdisk -l -uS /boot/images/fdos-250-hdd.img 
Disk /boot/images/fdos-250-hdd.img: cannot get geometry

Disk /boot/images/fdos-250-hdd.img: 31 cylinders, 255 heads, 63 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/16/63 (instead of 31/255/63).
For this listing I'll assume that geometry.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/boot/images/fdos-250-hdd.img1   *        63    511055     510993   e  W95 FAT16 (LBA)
/boot/images/fdos-250-hdd.img2             0         -          0   0  Empty
/boot/images/fdos-250-hdd.img3             0         -          0   0  Empty
/boot/images/fdos-250-hdd.img4             0         -          0   0  Empty
root@pc:~# bc
bc 1.06.95
Copyright 1991-1994, 1997, 1998, 2000, 2004, 2006 Free Software Foundation, Inc.
This is free software with ABSOLUTELY NO WARRANTY.
For details type `warranty'. 
512*63
32256
quit
root@pc:~# mount -o loop,offset=32256 /boot/images/fdos-250-hdd.img /mnt/
root@pc:~# mkdir -p /mnt/INTEL
root@pc:~# cp -rfp ~/Downloads/IDG4510H.86A.0131/ID0131P.BIO  ~/Downloads/IDG4510H.86A.0131/IFLASH2.EXE /mnt/INTEL
root@pc:~# md5sum ~/Downloads/IDG4510H.86A.0131/ID0131P.BIO   ~/Downloads/IDG4510H.86A.0131/IFLASH2.EXE /mnt/INTEL/* | sort 
root@pc:~# sync; cd /
root@pc:~# umount -f /mnt

```8. Update grub to use this image
```

update-grub2

```This should create a menu entry in grub to boot from this new disk image... 

Thats it... 

reboot the system and select the freedos boot option which was created... this will get you into a freedos environment which has over 250MB of space where you can store all your bios files and update as you feel like... 

No need to fiddle with USB pens or sticks... 

Hope his helps... 

Ghat

Acknowledgments:

[LIST=1]
[*][http://machine-cycle.blogspot.com/2009/09/boot-pc-from-floppy-image-w-grub2-and.html](http://machine-cycle.blogspot.com/2009/09/boot-pc-from-floppy-image-w-grub2-and.html)
[*][http://manual.sidux.com/en/bios-freedos-en.htm](http://manual.sidux.com/en/bios-freedos-en.htm)
[/LIST]
Appendix
1. To find out the details of the current bios on you machine use the following command
```

root@pc:~# dmidecode --type bios
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
        Vendor: Intel Corp.
        Version: IDG4510H.86A.0131.2010.0712.0906
        Release Date: 07/12/2010
        Address: 0xF0000
        Runtime Size: 64 kB
        ROM Size: 1024 kB
        Characteristics:
                PCI is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                Selectable boot is supported
                BIOS ROM is socketed
                EDD is supported
                5.25"/1.2 MB floppy services are supported (int 13h)
                3.5"/720 KB floppy services are supported (int 13h)
                3.5"/2.88 MB floppy services are supported (int 13h)
                Print screen service is supported (int 5h)
                8042 keyboard services are supported (int 9h)
                Serial services are supported (int 14h)
                Printer services are supported (int 17h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                LS-120 boot is supported
                ATAPI Zip drive boot is supported
                BIOS boot specification is supported
                Targeted content distribution is supported

Handle 0x0029, DMI type 13, 22 bytes
BIOS Language Information
        Installable Languages: 1
                en|US|iso8859-1
        Currently Installed Language: en|US|iso8859-1

root@pc:~#
```

---

### Post by Slywire on 2010-11-14
Hi there
This all seems very legit and a great idea, just note a couple of mistypes. I have posted the correct lines below(correct me if Im wrong):
step6:
qemu -hda /boot/images/fdos-250m-hdd.img -cdrom /path/to/fdbasecd.iso -boot d

step7:
the line
root@pc:~# fdisk -lus /boot/images/fdos-250-hdd.img 
root@pc:~# mount -o loop,offset=32256 /boot/images/fdos-250m-hdd.img /mnt/

I have followed these instructions and my grub still does not see any DOS operating systems to boot from. Have you done this personally and it worked for you?Also, I noted that the first link you gave ([http://machine-cycle.blogspot.com/20...grub2-and.html](http://machine-cycle.blogspot.com/20...grub2-and.html)) edited the "/etc/grub.d/40_custom" file instead of the 50_memtest. Any reason for this?

---

### Post by ghat on 2011-11-16
> **Slywire said:**
> Hi there
This all seems very legit and a great idea, just note a couple of mistypes. I have posted the correct lines below(correct me if Im wrong):
step6:
qemu -hda /boot/images/fdos-250m-hdd.img -cdrom /path/to/fdbasecd.iso -boot d

step7:
the line
root@pc:~# fdisk -lus /boot/images/fdos-250-hdd.img 
root@pc:~# mount -o loop,offset=32256 /boot/images/fdos-250m-hdd.img /mnt/

I have followed these instructions and my grub still does not see any DOS operating systems to boot from. Have you done this personally and it worked for you?Also, I noted that the first link you gave ([http://machine-cycle.blogspot.com/20...grub2-and.html](http://machine-cycle.blogspot.com/20...grub2-and.html)) edited the "/etc/grub.d/40_custom" file instead of the 50_memtest. Any reason for this?

Yes I have used this, but its possible there are some typos... 

Well my sever went down for other reasons, and I  have to do this procedure again, so I will correct any mistakes in the coming few weeks. 

G

---

### Post by oldos2er on 2011-11-16
Closed, necromancy.

---

