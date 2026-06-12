---
title: "GRUB freezes on a clean install with a laptop"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by narcisgarcia on 2010-02-06
Scenario new-clean laptop computer "Hundyx W765TUN" with this test results:

Devices:
- Intel Pentium(R) Dual-Core CPU T4300 @ 2.10GHz: well managed with Live-CD
- VGA NVIDIA G98M/GeForce-G105M: well managed with Live-CD
- CD/DVD Matshita UJ890AS: well managed with Live-CD
- Audio Intel ICH9/82801I: well managed with Live-CD
- Connectors Audio/USB: well managed with Live-CD
- NIC Realtek RTL8111/8168B: well managed with Live-CD
- NIC-wireless Realtek RTL8187B: well managed with Live-CD

- Hard drive: ICH9M/M-E 2 port SATA IDE Controller
- Hard disk: 160GB SAMSUNG HM160HI
- RAM memory: 2x 2GiB SODIMM DDR2 Synchronous 800 MHz (total 4GiB)
(the disk comes clean by the manufacturer, without any previous software installed)

All works fine with Ubuntu GNU/Linux 9.10 Live-CD (either 32-bit as 64-bit), but when install **GRUB freezes in the black screen showing only the text "GRUB Loading."**

I've tried installations on the same computer with the following variants:
[LIST]
[*]Ubuntu 9.10 alternate CD 64-bits, connected to internet
[*]Ubuntu 9.10 alternate CD 64-bits, offline
[*]Ubuntu 9.10 alternate CD 64-bits, offline
[*]Ubuntu 9.10 Live-CD 64 bits, connected to internet
[*]Ubuntu 9.10 Live-CD 64 bits, offline
[*]Ubuntu 9.10 Live-CD 32 bits, connected to internet
[*]Ubuntu 9.10 Live-CD 32 bits, offline
[*]Ubuntu 9.04 Live-CD 32 bits, offline (the message is **GRUB Loading stage1.5.**)
[/LIST]

On every installation I've cleaned the MBR and made new partitioning at all for a single system. Tried to partition the disk manually and tried the "use entire disk" option with the automatic wizard. Same results on all cases, when the installation process goes well at all.

I've tried also to leave the computer some hours with the "GRUB Loading." message, but it doesn't move and remains with the same screen/text. Cursor remains blinking all the time under the GRUB message. In all cases Control+Alt+Del works to reboot.

With hundreds of installations made, I've never found the same situation. It would be so strange to be a hardware issue.

---

### Post by narcisgarcia on 2010-02-06
I've made an installation on a 4GiB USB stick, as if it was a hard disk, and when tries to boot only shows one word: "**GRUB**" (it doesn't complete the phrase with "loading...")

(Ubuntu 9.10 Live-CD 64-bits)

---

### Post by lidex on 2010-02-06
Get your reading glasses:
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

Scroll down for troubleshooting.

---

### Post by narcisgarcia on 2010-02-06
lidex, do you suppose that is a GRUB2 specific issue?
This is happening me also with Ubuntu 9.04 , which installs GRUB1 by default.

---

### Post by oldfred on 2010-02-06
I would be surprised if it is a hardware issue if the liveCD works ok. We often spend hours, days even weeks trying to resolve issues when sometimes a reinstall solves all the issues, but you should not be having this much trouble.

What install do you have now and what error message or screen is last.

I installed Karmic on both my desktop and my laptop (both about 3 years old) without any issues. Both were dual boot with XP and my desktop has multiple drives which often contribute to grub2 issues.

If you install seemed to be complete and grub does not load completely run this script to see your entire configuration for booting:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by sandy8925 on 2010-02-06
GRUB seems to try accessing CD drives as well when it boots. Since I use scratched disks sometimes this makes GRUB wait for some 30-35 seconds before finally showing the menu. Make sure there aren't any CD's in your CD drive.

Are you sure all your install disks are proper? (i.e properly burned and no errors? make sure you check them). It could be that GRUB doesnt work properly with your drive. Also, some BIOS's have the option to prevent software from writing to the boot sector. That could also be a problem.

---

### Post by narcisgarcia on 2010-02-06
Some answers for now:
[LIST]
[*]Now already tested the same with Ubuntu 8.10 32-bits Live-CD: Same result.
[*]Now already tested the same with Ubuntu 8.04 32-bits Live-CD (low resolution graphics and networking doesn't work): Same result.
[*]Tried to boot a Live-USB stick created from an 9.10 ISO image (with the "USB startup disk creator" utility): boots perfectly as the Live-CD
[*]In all the cases I've verified that there isn't any CD in the drive, and waited more than 5 minutes. With the 9.10 attempts I waited for hours.
[*]The particularity may be this (new) computer, because the with same procedures I've succeeded with a lot of other laptops and desktop computers, with all the Ubuntu versions and variants.
[*]It cannot be a Compact Disk surface problem, because I'm doing tests and installations with a lot of different Live and alternate CDs, and different manufacturer of the CDs. And an important point: the Live sessions work as expected.
[*]BIOS is configured to allow MBR/boot sector writing, since the first time. GParted and Partitioner allows me to create new partition tables, and the new MBR works because the short text "GRUB loading" is shown when booting.
[*]With each installation I've cleaned the entire hard disk, then each installation has been a totally clean installation. When installing from Live-CD, the choosen option everytime was "Erase and use the entire disk"; with alternate installation both manual and guided otions tried.
[*]The last installation has been for the Ubuntu 8.04; _All_ the versions here described say only "**GRUB Loading stage1.5.**" (GRUB1), except the 9.10 installations that say "**GRUB Loading**" (GRUB2). These texts appear on the top of black screen and the keyboard cursor remains blinking on the second screen line.
[/LIST]

---

### Post by narcisgarcia on 2010-02-06
Once installed again the Ubuntu 9.10 64-bits with the Live-CD,
Here comes the *Boot Info Script* results:
```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader? is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xce40ce40

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   299,805,029   299,804,967  83 Linux
/dev/sda2         299,805,030   312,576,704    12,771,675   5 Extended
/dev/sda5         299,805,093   312,576,704    12,771,612  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 32.0 GB, 32006733824 bytes
17 heads, 17 sectors/track, 216308 cylinders, total 62513152 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xce8eb281

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               8,064    62,513,151    62,505,088   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        520a1c44-5ce7-4ac4-95ea-a61317e81afb   ext4                                     
/dev/sda5        ddcd3914-1c16-4bad-9e69-151a106526ca   swap                                     
/dev/sdb1        0DCD-5BEF                              vfat       GRIS32GB                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/GRIS32GB          vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 520a1c44-5ce7-4ac4-95ea-a61317e81afb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 520a1c44-5ce7-4ac4-95ea-a61317e81afb
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=520a1c44-5ce7-4ac4-95ea-a61317e81afb ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 520a1c44-5ce7-4ac4-95ea-a61317e81afb
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=520a1c44-5ce7-4ac4-95ea-a61317e81afb ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=520a1c44-5ce7-4ac4-95ea-a61317e81afb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ddcd3914-1c16-4bad-9e69-151a106526ca none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz
```

---

### Post by narcisgarcia on 2010-02-06
Now I've tried to install Microsoft Windows XP Professional (2002, SP1), and it installs succesfully and boots normally.

---

### Post by oldfred on 2010-02-06
Even though it is a new computer did they use an old BIOS that has the 130GB limit?

Since you have installed so many time perhaps one more with a small root of 10-20GB at the front of the disk, swap and either a separate /home or /data for the rest of the drive. This is just a wild guess as I do not see anything that should be a problem.

Another thought.
Have you been able to boot into your install from the liveCD where it says boot HD? Sometimes the initial install of grub is not quite right and it has to be reinstalled.

---

### Post by narcisgarcia on 2010-02-06
Now I've created the complete page for this laptop computer in:
[https://wiki.ubuntu.com/LaptopTestingTeam/Old/HundyxW765TUN](https://wiki.ubuntu.com/LaptopTestingTeam/Old/HundyxW765TUN)

---

### Post by narcisgarcia on 2010-02-06
Thanks oldfred, but no luck:
[LIST]
[*]I've made an installation in a single 20GiB partition (no swap), and same results with Ubuntu 9.10
[*]Then I've tried with the "Boot from first hard disk" option in the Live-CD boot menu, but freezes with the message "**Booting from local disk...**"
[/LIST]

---

### Post by oldfred on 2010-02-06
I am lost too.

I might try chrooting into your system and doing all the updates to see if something there fixes it.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
Method 3 is full chroot just to reinstall grub

I copied and did minor edits to these commands, you should be able to just copy them except for anything after a # comment.
Of course you must first know what partition you want to mount, in this example I'm using sda1:

sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot /mnt
#Then run whatever commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain you mounted the correct partition).
apt-get update
apt-get upgrade
[B]update-grub
[/B][B]grub-install /dev/sda
[/B]**sudo grub-install --recheck /dev/sda**
#When done:
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

---

### Post by narcisgarcia on 2010-02-07
Tried now installing Debian GNU/Linux 5.0.0
The result is exactly the same (GRUB1)

---

### Post by narcisgarcia on 2010-02-07
Thanks oldfred;

No luck with your recipe (followed exactly as is, because sda1 matches). The last messages may not be as expected:

> (...)
Processing triggers for python-support ...
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Cannot find list of partitions!
done
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ sudo umount /mnt/dev
umount: /mnt/dev: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:~$ sudo umount /mnt/proc
umount: /mnt/proc: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:~$ sudo umount /mnt
umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

After all, the result is the same as all other cases: reboot and see only "**GRUB loading.**"

---

### Post by narcisgarcia on 2010-02-07
[LIST]
[*]Installed OpenSUSE 11.0 (Gnome, 32-bits, from Live-CD): **Failed** (*GRUB Loading stage2..*)
[/LIST]

Can somebody explain how to install LiLo instead of GRUB in Ubuntu 9.10 ?
Other bootloaders?

---

### Post by lidex on 2010-02-07
OK. 
Chokes on grub/grub2.
LiveCD/usb work fine.
Windows installs/boots fine.

How are your HDD's set up in bios? Is everything sata or do you have pata device in there? How many actual sata connectors are on your board? How are they grouped? Have you tried removing sdb for install?

Do you think lilo is an option? Or perhaps a troubleshooting tool?

---

### Post by lidex on 2010-02-07
When you followed oldfred's instructions there were two things I questioned.
*Cannot find list of partitions!* and contents of device map as *(hd0) /dev/sda*. Shouldn't sdb be in there also? What causes that error message?

---

### Post by narcisgarcia on 2010-02-07
It's a Laptop, and in the BIOS/CMOS I only see S.ATA options and IDE equivalents as you can see here:
[https://wiki.ubuntu.com/LaptopTestingTeam/Old/HundyxW765TUN](https://wiki.ubuntu.com/LaptopTestingTeam/Old/HundyxW765TUN)

I was going to try also with Mandriva and Fedora distributions, but because of I need to deliver today this computer, I've thinked to install a Microsoft Windows XP and to use Wubi for an Ubuntu installation.

I don't believe Microsoft Windows +Wubi to be a better option than LiLo. Now the only options I see are:
[LIST=1]
[*]Change GRUB for Lilo
[*]Install Ubuntu through Windows+Wubi
[/LIST]

---

### Post by lidex on 2010-02-07
May be of interest:
[http://ubuntuforums.org/showthread.php?t=937729]("http://ubuntuforums.org/showthread.php?t=937729")

---

### Post by narcisgarcia on 2010-02-07
Thanks but in this notebook computer I cannot change cables position.

I don't know the reason of the "Cannot find list of partitions!" message. In this computer there is only 1 hard drive (sda) and the optical drive acts as "sdb" when I'm working in Live-CD.

---

### Post by lidex on 2010-02-07
One thing I'm questioning here are the actual connections of your IDE devices. I have seen boot issues from cdrom and hdd on same "channel". I have seen issues when pata and sata hdd both in use. My motherboard has 2 sata channels with two connectors each:

     [HTML]connector       color      setting      use
  sata 1/3       red       master      boot disk
  sata 2/4      black      slave       data disk[/HTML]

---

### Post by lidex on 2010-02-07
> **narcisgarcia said:**
> Thanks but in this notebook computer I cannot change cables position.

I don't know the reason of the "Cannot find list of partitions!" message. In this computer there is only 1 hard drive (sda) and the optical drive acts as "sdb" when I'm working in Live-CD.

Gotcha. A Headscratcher for sure. I'm throwing whatever I can at the wall to see what sticks.

---

### Post by narcisgarcia on 2010-02-07
This is the process I've done to install it on a "sda1" single partition system: Once the system is installed, boot again with the Live-CD and written this on a Terminal window:
```

sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot /mnt
#Then run whatever commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain you mounted the correct partition).
apt-get update
apt-get remove grub-pc grub-common
apt-get install lilo
# At this point, edit the file /etc/fstab to change UUID references to traditional references: /dev/sda1 , /dev/sda5 ,...
liloconfig # I choose "debian" bitmap , and all other options YES.
lilo
#When done:
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

```

Then reboot the system, and without any other boot media, LiLo menu launches and when you press ENTER the system boots with this text:
> Loading Lin_2.6.31img0.............................
(A lot of dots instead of splash screen)

**Successful. Ubuntu 9.10 (64-bits) working alone in this computer.**
Now I'm trying to see what happens with a kernel update, /boot independent partition and root encryption.

---

### Post by oldfred on 2010-02-07
I never like giving up on grub2. But several users have and reverted to grub legacy, but you have in effect tried that. I have also seen users with windows use easyBCD. I think it chainboots into ubuntu so a grub has to be installed in the ubuntu partition. Grub2 does not like to be installed in a partition but can be forced to, so old grub may be the better choice if you want to try that.

I googled and the partition error seems not to be a major concern. Most other related issues seemed to involve raid which you do not have unless the drive in your portable was tested as raid at some point.

---

### Post by oldfred on 2010-02-07
I missed your lilo post. I am really surprised that that worked and nothing with grub did, but am glad you got it going. Good luck with all the updates.

---

### Post by narcisgarcia on 2010-02-07
I will not mark this thread as solved, because GRUB still has a problem with this computer model.

---

### Post by lidex on 2010-02-07
Maybe grub doesn't like your bios settings. You might have a look at that. SATA mode, maybe? AHCI>IDE? Or a bios update.

---

### Post by narcisgarcia on 2010-02-07
Maybe, maybe...
But fot the moment I'll work with the LiLo solution. I haven't more time for tests.

Thanks to everybody who suggested me different alternatives and tests.

---

### Post by narcisgarcia on 2010-08-27
Today I've the opportunity to install again the same computer from scratch.

I don't find any solution for this intel **ICH9M/M-E** chipset/SATA controller. I've now tried to install Ubuntu 10.04.1 but similar result (now it doesn't appear any "GRUB" text, just freezes after POST).

I'm trying to find a GRUB solution, because I need to encrypt the root (/) filesystem, and with LiLo is not possible.
I've tried also enabling "legacy SATA" in the BIOS and installing GRUB with the "ata" module, but nothing better happens.

---

### Post by narcisgarcia on 2011-01-15
Completely solved updating BIOS.

---

