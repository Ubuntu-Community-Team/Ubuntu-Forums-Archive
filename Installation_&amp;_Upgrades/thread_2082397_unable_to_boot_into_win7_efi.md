---
title: "unable to boot into win7 efi"
date: 2012-11-09
forum: Installation &amp; Upgrades
---

### Post by pulpo69 on 2012-11-09
I have win7 and ubuntu12.10 installed (efi mode both).
3weeks ago i used bootrepair because grub was only showing ubutu not
windows, windows i had to start via clickbios (came with the msi motherboard). after using bootrepair i Couldn't boot into windows any more
if i choosed windows in the clickbios, i ended up in grub there i coul only
start ubuntu.
So i installed windows from new (the recovery option  with the original
win cd Didn't work too.
from time to time i started boot-repair but only for seeing the boot-info.
yesterday i hitted without intention repair and windows was gone.
with f11 is showing windows but leading to a grub2 sreen in which only the ubuntu option is working.
choosing ubuntu in the f11 screen is happening the same. in the grubscreen are also some entries with mac-os (which i never had). 
[http://paste.ubuntu.com/1343589/](http://paste.ubuntu.com/1343589/) here is the bootinfo after the desaster. 
how can i get the boot entry back?
i searched in the net too for information, but being honest i'm a noob so i didn't understand a great part of it. 

when my f11 boot option for windows was working i had the following in boot-repair-info:

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda4        /boot/efi                vfat       (rw)
/dev/sda5        /                        ext4 (rw,errors=remount-ro)
/dev/sdb1        /home                    ext4       (rw)
/dev/sdb2        /storage                 ext4       (rw)

in the new boot info this line is gone:
/dev/sda4        /boot/efi                vfat       (rw)

also before gparted showed me sda4 as not mounted. Now sda4 shows as mounted. if i unmount it and reboot it shows again as
mounted.

the boot/efi partition seems ok.

chris@yoyo:~$ find /boot/efi -iname *.efi
/boot/efi/EFI/ubuntu/grubx64.efi
/boot/efi/EFI/Microsoft/Boot/bootx64.efi
/boot/efi/EFI/Microsoft/Boot/memtest.efi
/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
/boot/efi/EFI/Microsoft/Boot/bootmgr.efi
/boot/efi/EFI/Boot/bootx64.efi 

also i had the mac.. entries in grub.
i hour ago i therewas udate of repair.
did boot repair with updated version and it made a win 7 entry in grub,
but choosing it i come to same grub screen.

even in f11 (clickbios options) my efi-dvd-drive is gone only remaining
the normal dvd-drive.

any idea how i can save my install?

---

### Post by oldfred on 2012-11-09
Please update Boot-Repair. There was a bug where it was adding Mac entries to every system. Re-run repairs and post new BootInfo report.

You also have grub in the MBR. Hope that does not confuse booting.

Just for my curiosity:
You did your efi partition end up as sda4 and after the Windows partitions? The UEFI spec says it should be first, but some Windows installs will have the vendor recovery first then the efi partition as sda2. There may be some limits on how far into the drive the UEFI can read the efi partition.

---

### Post by pulpo69 on 2012-11-09
yes my /boot/efi is sda4.
[http://paste.ubuntu.com/1345790/](http://paste.ubuntu.com/1345790/)  this is the boot-repair output, did it
with newwest boot-repair (updated 5 hours ago). for first time bootrepair
put a windows7 entry into grub, but entry don't work (it's a circle), hitting the entry i'm otherwise back to grub.

---

### Post by oldfred on 2012-11-09
You have a bunch of extra proxy files adding entries. Not sure where they all came from. Do you have a custom.cfg file?

> 11_custom_proxy
12_custom_proxy
15_custom_proxy
18_custom_proxy
20_custom refers to source $prefix/custom.cfg
```
### BEGIN /etc/grub.d/12_custom_proxy ###
menuentry "Windows 7 UEFI" {
search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}
### END /etc/grub.d/12_custom_proxy ###

```The one 12_custom looks like a correct Windows efi entry.

I would change all the others to not executable, so they are not added to grub.cfg. If you find you need them you can change them back with +x.

sudo chmod a-x /etc/grub.d/15_custom_proxy
Same for all the others except 12.

Does Windows show it is starting to boot? Grub may return if boot file not found.

You could also copy this into 12_custom_proxy as an alternative just to see if extra add in modules help. Most do not seem to need them. Edited to be your sda4 and your UUID for the efi partition.

gksudo gedit /etc/grub.d/12_custom

```
menuentry "Windows 7 UEFI alt" {
  insmod part_gpt
  insmod fat
  insmod search_fs_uuid
  insmod chain
  set root='(hd0,gpt4)'
  search --fs-uuid --no-floppy --set=root F112-DFD6
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

```

---

### Post by pulpo69 on 2012-11-09
i deleted #15 because it had only macos (which i never had).
inactivated the rest and copied your code in #12.
reboot. but happened the same choosing the w7 entry (circle back to grub)
and a bunch of macos entries.

my 12-custom-proxy looks like that now:
### BEGIN /etc/grub.d/12_custom_proxy ###
menuentry "Windows 7 UEFI" {
search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}
### END /etc/grub.d/12_custom_proxy ####!/bin/sh
#THIS IS A GRUB PROXY SCRIPT
'/etc/grub.d/proxifiedScripts/custom~1' | /etc/grub.d/bin/grubcfg_proxy "-*
-#text
+'Windows 7 UEFI'~98359908d36303c968019bfd5c599fa7~
"
menuentry "Windows 7 UEFI alt" {
  insmod part_gpt
  insmod fat
  insmod search_fs_uuid
  insmod chain
  set root='(hd0,gpt4)'
  search --fs-uuid --no-floppy --set=root F112-DFD6
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi

also a 12-custom-proxy~ was created an looks like that:
#!/bin/sh
#THIS IS A GRUB PROXY SCRIPT
'/etc/grub.d/proxifiedScripts/custom~1' | /etc/grub.d/bin/grubcfg_proxy "-*
-#text
+'Windows 7 UEFI'~98359908d36303c968019bfd5c599fa7~

---

### Post by oldfred on 2012-11-09
It looks like the proxy scripts are from grub customizer.

[https://answers.launchpad.net/grub-customizer/+faq/1355](https://answers.launchpad.net/grub-customizer/+faq/1355)

I would turn off 15_ also.

and just copy this into 40_custom. Make sure you include last } as it looked like it was missing. If you want Windows before the Ubuntu entires, copy 40_custom to 06_custom and then add entries. But the custom files have to have the couple of lines at the top of the file as in 40_custom.

```
menuentry "Windows 7 UEFI" {
search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

menuentry "Windows 7 UEFI alt" {
insmod part_gpt
insmod fat
insmod search_fs_uuid
insmod chain
set root='(hd0,gpt4)'
search --fs-uuid --no-floppy --set=root F112-DFD6
chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}


```

If you go directly into UEFI, you should have two entries and be able to directly boot Windows. If that does not work then it is a Windows issue.

---

### Post by pulpo69 on 2012-11-09
yes iused one time grub-customizer. idelted '15, because containing only macos.

the last } wasn't missing, only in the post. excuse me.

i don't understand, i have no file with #40 in my grub.d folder and no #6.
should i create one?

chris@yoyo:/etc/grub.d$ ls
00_header        12_custom_proxy   17_uefi-firmware  proxifiedScripts
05_debian_theme  12_custom_proxy~  18_custom_proxy   README
10_linux         14_linux_xen      20_custom
11_custom_proxy  16_os-prober      bin

---

### Post by oldfred on 2012-11-09
I do not have an UEFI install but have all of these.

```
fred@fred-Precise:/media/Quantal/etc/grub.d$ ls -l
total 72
-rwxr-xr-x 1 root root  7541 Oct 14 12:36 00_header
-rwxr-xr-x 1 root root  5488 Oct  4 04:30 05_debian_theme
-rwxr-xr-x 1 root root 10891 Oct 14 12:36 10_linux
-rwxr-xr-x 1 root root 10258 Oct 14 12:36 20_linux_xen
-rwxr-xr-x 1 root root  1688 Oct 11 09:10 20_memtest86+
-rwxr-xr-x 1 root root 10976 Oct 14 12:36 30_os-prober
-rwxr-xr-x 1 root root  1426 Oct 14 12:36 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Oct 14 12:36 40_custom
-rwxr-xr-x 1 root root   216 Oct 14 12:36 41_custom
-rw-r--r-- 1 root root   483 Oct 14 12:36 README

```

You can create a 40_custom, but it needs these lines first.

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

---

### Post by pulpo69 on 2012-11-11
hi oldfred,
did the following: run boot-repair again (uefi option). this created a custoM-40, in this i pasted your code. but grub is now showing only my  ubuntu entry, no windows.
[http://paste.ubuntu.com/1350274/](http://paste.ubuntu.com/1350274/)

never i had such troubles with ubuntu/windows. in all my former installs it worked. it seems that the efi thing is a real troublemaker.

---

### Post by oldfred on 2012-11-11
Post your 40_custom. 
Does it have the few lines at the beginning and is it set as executeable?

sudo chmod a+x /etc/grub.d/40_custom

---

### Post by pulpo69 on 2012-11-11
hi oldfred,
yes it was executable, but didn't work, same as before.
so i did in the meantime delete my first hdd (windows and ubuntu os),
my home partition is on a second disk.
made a new partitioning of the disk (sda1 500mb /boot/efi, sda2 ntfs,
sda3 ext4 /, sda4 swap and at last 2 GB unallocated). efi install of win7 and ubuntu-gnome-remix 12.10.01 went ok. but grub otherwise only showed ubuntu not win7. installed boot-repair, run it and now grub is showing win and ubuntu in its menu and he menu-entries are working as desired.

in the unallocated space win7 put a 128MB microsoft reserved space. this is now at the end of the disk, maybe it's better to have it in the beginnining (but as long as it works, iwill touch or change nothing).

after lot of struggle and bad installs i would recommend for efi win7/ubuntu (don't know for win8) the following partition scheme sd1 300mb fat32 /boot/efi, sd2 128mb unallocated (for ms reserv., sd3 ntfs for win7, sd4 ext4 for ubuntu,sd5 swap.
i don't know nothing about efi but it was the way it worked for me and i hope efi will get easier to handle in the future with an idiot-proof
tutorial for people like me.

oldfred thanks a lot for your help, i appreciated it a lot.

here is my running configuration: [http://paste.ubuntu.com/1351596/](http://paste.ubuntu.com/1351596/)   p.s. i unticked in boot-repair the repair of windows-boot-files

---

### Post by oldfred on 2012-11-11
Glad you got it working. 

Your partition suggestions seem to be similar to what we see in other installs, but they usually start with Windows already installed and just need to add the Linux partitions.

---

