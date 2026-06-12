---
title: "Multiple problems after upgrading 7.10 to 8.04"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by IT-Joker on 2008-04-26
Hi all,
I have recently upgraded from Ubuntu 7.10 to 8.04. Sadly, while 7.10 worked perfectly, it's not the case with 8.04.
In fact, there are more problems than I have expected :icon_frown:

The update itself seemed OK but then I rebooted to start using the new version and these problems appeared.

1. I solved this one, so just for info: Administrative tools and anything that requires sudo stopped working. In GUI they load for a while and then close. If this happens to you, open command line and try sudo anything. It'll propably write that sudo can't reach [computer]. The cause is that the /etc/hosts file is missing this record:
127.0.1.1 [computer]
(replace [computer] with your computer name)
I had this in my /etc/hosts:
127.0.1.1 [computer].[domain]
but appearantely it didn't work. It seems either the installation doesn't put correct record in there, or it's a bug that [computer].[domain] doesn't work.
Anyway it's pretty nasty bug, because without sudo you can't even edit /etc/hosts from your account (and recovery mode didn't allow me to use GUI)
Btw. one question: Is there any other editor except vi(m) available in Ubuntu without GUI? 

2. If I boot with older kernel (2.6.22-14, hope I remember it correctly), the nVidia driver doesn't work. There are some other threads about this and they recommend booting with the 2.6.24-16 kernel. Which leads me to:

3. Grub gives me options to boot with the older kernel or 2.6.24-16. The older one boots OK, but nVidia driver doesn't work (see above). 
The newer one doesn't boot. It seems to fail detecting SATA hard drive. 
It says something like this:

ata1: /dev/disk/by-uuid/ (code) does not exist. dropping to shell
and then it opens Busybox.

For now I'm using the older kernel without 3D acceleration so that I can at least do something, but it's only a temporary solution. I'd either get 8.04 with any kernel work, or reinstall back to 7.10.

My HW config, if it's helpful: Athlon64 X2, AMD 580X chipset, nVidia 8600GT graphic card, SATA hard drive.

---

### Post by dstew on 2008-04-26
Boot your older kernel, and post the output of```
sudo fdisk -l
cat /boot/grub/menu.lst
cat /etc/fstab
```Also, if you don't mind, check the UUID of your root partition with```
sudo vol_id *<device>*
```And, for good measure,```
ls -l /dev/disk/by-uuid
```

---

### Post by Poborskiii on 2008-04-26
Other console editor is nano or internal editor in midnight commander.

---

### Post by IT-Joker on 2008-04-27
dstew:
sudo fdisk -l
Hope you don't mind the output is in czech. I think the values are quite self-explanatory, but I can translate the labels or reboot to english and post it again, if needed.
```
Disk /dev/sda: 250,0 GB, 250*059*350*016 bajt&#367;
hlav: 255, sektor&#367; na stopu: 63, cylindr&#367;: 30*401
Jednotky = cylindry po*16065 * 512 = 8*225*280 bajtech
Identifikátor disku:&#8239;0xfbbbfbbb

Za&#345;ízení Zavád&#283;t   Za&#269;átek       Konec    Bloky    Id  Systém
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       30401   223713157+   f  W95 Roz&#353;. (LBA)
/dev/sda5            2551       25497   184321746    7  HPFS/NTFS
/dev/sda6           25498       29631    33206323+  83  Linux
/dev/sda7           29632       30401     6184993+  82  Linux swap/Solaris

```

note: The NTFS partition was my Windows disc before I deleted Windows ;) 

cat /boot/grub/menu.lst
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=ba34e57e-1040-440d-b164-fa30cbb164fd ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash locale=cs_CZ

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ba34e57e-1040-440d-b164-fa30cbb164fd ro quiet splash locale=cs_CZ
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ba34e57e-1040-440d-b164-fa30cbb164fd ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ba34e57e-1040-440d-b164-fa30cbb164fd ro quiet splash locale=cs_CZ
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ba34e57e-1040-440d-b164-fa30cbb164fd ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title		Microsoft Windows XP Professional
#root		(hd0,0)
#savedefault
#makeactive
#chainloader	+1

```
It's strange:
/boot/vmlinuz-2.6.24-16-generic root=UUID=ba34e57e-1040-440d-b164-fa30cbb164fd ro quiet splash locale=cs_CZ
- this one says that it can't find a drive with that uuid

/boot/vmlinuz-2.6.22-14-generic root=UUID=ba34e57e-1040-440d-b164-fa30cbb164fd ro quiet splash locale=cs_CZ
- this one works... with the same uuid

cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=ba34e57e-1040-440d-b164-fa30cbb164fd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=F80C93700C9328A0 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=BCE87C1CE87BD2DE /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=f63b9e7c-8b30-4742-8b5e-b3bee1630140 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

vol_id /dev/sda6 says:
ID_FS_UUID=ba34e57e-1040-440d-b164-fa30cbb164fd
ID_FS_UUID_ENC=ba34e57e-1040-440d-b164-fa30cbb164fd

and ls -l /dev/disk/by-uuid
```
celkem 0
lrwxrwxrwx 1 root root 10 2008-04-27 10:33 ba34e57e-1040-440d-b164-fa30cbb164fd -> ../../sda6
lrwxrwxrwx 1 root root 10 2008-04-27 10:33 BCE87C1CE87BD2DE -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-04-27 10:33 f63b9e7c-8b30-4742-8b5e-b3bee1630140 -> ../../sda7
lrwxrwxrwx 1 root root 10 2008-04-27 10:33 F80C93700C9328A0 -> ../../sda1

```

---

### Post by IT-Joker on 2008-04-27
> **Poborskiii said:**
> Other console editor is nano or internal editor in midnight commander.

Nano looks good, thanks.

---

### Post by IT-Joker on 2008-04-27
(I apologize for multipost)
I have seen some people having similar problems with 8.04 alpha/beta but the only solution I have seen so far is to wait for final version... but I DO have the final version.
So, any ideas?

---

### Post by dstew on 2008-04-27
This problem is a bit strange. Everything looks like it is set up correctly. Did you install Hardy by doing a fresh install from disk, or by using the Upgrade selection on the Update Manager window?

---

### Post by IT-Joker on 2008-04-27
> **dstew said:**
> This problem is a bit strange. Everything looks like it is set up correctly. Did you install Hardy by doing a fresh install from disk, or by using the Upgrade selection on the Update Manager window?
That's worst situation you can ever get with computer program... everything seems set up so that it MUST work, but it just DOESN'T.

Like I said, I upgraded via the update manager from 7.10, which was working quite good. In fact I'm quite disappointed, after installing 7.10 I was just happy that I have finally found a Linux distribution that runs without any problems :(

Well, I think I'll try running the new kernel in recovery again and see if I can get some info from the messages.

Or if someone would tell me how to make the nVidia driver work with 2.6.22-14 so that I could use 2.6.22-14 (which seems to work OK, except the 3D acceleration), that would help too.

---

### Post by IT-Joker on 2008-04-27
So, I checked the messages during boot and here's the point where I think the problem happens:

```
SATA link up 1.5Gbps (SStatus 113 control 300)
(...)
ata1.00: qc timeout (cmd 0xec)
ata1.00: failed to IDENTIFY (I/O error, err_mask: 0x4)
ata1: failed to recover some devices, retrying in 5 secs

```
After this it waits and then writes the same stuff, then it waits again, displays the same stuff again and then it continues booting, until at the end it gets to the line that the disk doesn't exist and drops to Busybox.

---

### Post by dstew on 2008-04-27
This problem seems to be a kernel bug. See [this bug thread]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/219312"). There are some kernel parameters that you can try.

---

### Post by IT-Joker on 2008-04-28
> **dstew said:**
> This problem seems to be a kernel bug. See [this bug thread]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/219312"). There are some kernel parameters that you can try.
I expected something like that because yesterday I tried to explore with Busybox a bit and it was true- the disc /dev/by-uuid/(the code) wasn't there. I didn't even have the by-uuid directory in /dev.
So I guess the newer kernel fails to detect the disc.

Well, now... one question... if there's a kernel with this bug fixed, how difficult it is for not-too-experienced Linux user to upgrade the kernel?

---

### Post by dstew on 2008-04-28
I have never compiled my own kernel. From what I have read, you get a kernel patch, apply the patch, and compile your own custom kernel. [Here]("http://howtoforge.com/kernel_compilation_ubuntu") is a page about that.My guess is that it will be fixed in a few weeks, but I don't really know much about that end of the Ubuntu business. I am looking into it though, maybe helping out fixing bugs.

---

### Post by IT-Joker on 2008-04-28
Hurray!
It's working now!

After messing a bit with BIOS and with Grub options, adding the "pci=nomsi" finally made the newer kernel work.
Now when the newer kernel works, the problem with nVidia driver is gone too. It simply works allright with the newer kernel.

Thanks to dstew for ideas and patience :KS

So, a quick sum up of what I had to do:
1. 
Problem: sudo and therefore all the administrative utilities weren't working. Very nasty as without sudo it's difficult to even explore the problem from your "normal" account.
Cause: missing/wrong record in /etc/hosts 
Solution: Reboot to recovery mode and under root account edit the /etc/hosts and add the missing line

2.
Problem: nVidia driver isn't working with 2.6.22-14 kernel. If you enable it and restart, the system drops to low resolution although the graphic card and monitor model seems to be detected correctly.
Cause: Some bug in the 2.6.22-14 kernel, AFAIK.
Solution: I haven't found any. You'll propably have to use the newer kernel to make it work.

3. 
Problem: When booting with 2.6.24-16 kernel the system can't detect SATA hard drive. 
Cause: A bug in the 2.6.24-16 kernel.
Solution: There are multiple suggestions, each of them seems to work for some people and not to work for others. For me, the one that worked is adding "pci=nomsi" to the Grub menu option that runs the new kernel.

As this is my first Ubuntu upgrade after clean (and non-problematic) installation of 7.10, I hope that this is not how an usual Ubuntu upgrade looks like. If I were some computer newbie just checking Ubuntu, I'd propably give up.

---

