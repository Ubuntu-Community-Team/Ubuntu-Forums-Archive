---
title: "Grub Help"
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by sic08869 on 2011-02-11
Hi all,
    I have been on this problem for 3 days now and have tried everything I have found in this forum. I realize that I must be missing the post. So here goes. 

I have a debian etch server box that I have done a dirvish backup of the entire filesystem. 

I have taken a dell machine with a sas raid 1 (hardware controller) and loaded the ubuntu livecd 32bit 10.10.  The livecd can see the block device as /dev/sda so I created a /dev/sda1 (ext3) and a /dev/sda2 (swap).

I then mounted my backup drive to a directory I called /source and my /dev/sda1 to /target

Then I restored the filesystem using rsync -av /target /source

I then did a chroot /target
mount /proc
cp /proc/mounts/ /etc/mtab
and made sure that I could do an ls -al /dev/sda1 /dev/sda and /dev/sda2 to confirm that I had the devices. 

This method has worked on countless machines I have used recovered in the past. So here is where I have the problems. 

grub-install --recheck /dev/sda  

results: Probing devices to guess BIOS drives. This may take a long time.
Searching for GRUB installation directory ... found: /boot/grub
The file /boot/grub/stage1 not read correctly.

So I tried:
sudo grub 

find /boot/grub/stage1

results: Error 15: File not found


root (hd0)
results: Filesystem type unknown, using whole disk

setup (hd0)
results: Error 17: Cannot mount selected partition


root (hd0,0)
results: Filesystem type is ext2fs, partition type 0x83

setup (hd0,0)
results: Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 2: Bad file or directory type


So here is my dilemna, while in the chroot environment I can clearly ls -al /boot/grub/stage1 it does exist and is there. 


Last but not least I also did an apt-get remove grub and mv /boot/grub /boot/grub.old apt-get install grub and tried the process all over to no avail same results. Any other ideas?


Thank you in advance for any help that you can provide. 


fstab:


proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda2       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0



menu.lst

title           Debian GNU/Linux, kernel 2.6.18-6-686
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.18-6-686 root=/dev/sda1 ro
initrd          /boot/initrd.img-2.6.18-6-686
savedefault

---

### Post by oldfred on 2011-02-11
I do not know RAID. Are you intentionally using grub legacy? Error 15 is often conflicts between grub legacy and grub2.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by sic08869 on 2011-02-12
Grub legacy, was all that is installed on that debian etch box. I am not sure that grub2 is in the repositories. I had not realized that the error 15 was related to issues to the different packages. 

I have been able to boot the box using a systemrescuecd boot disk and using the option where you have the boot disk "boot an OS all ready installed on the machine"

Even after I am booted into the system, if I try and do an grub-install I still get the same error. So grub is still not working but at least I can get into the system.

---

