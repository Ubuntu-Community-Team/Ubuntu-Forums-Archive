---
title: "wont boot after upgrading! help!"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by cfar893fm on 2008-02-06
we're running ubuntu 7.10 amd_64 on an acer aspire 5520. after installing the routine updates from update manager (there were 28), the menu bar said restart required, so i did. some part of the update reset the grub menu.lst file, removing the nosplash and all_ide_generic parameters.

the real problem is that ubuntu hangs just after "kernel alive" and a couple others, and eventually says /dev/disk/by-uuid/long_cryptic_number does not exist, and drops to a shell. 

how can i fix this? i really dont even have any ideas where to start, since most live cds wont work with this nvidia card. any ideas are appreciated - i have to fix this computer tonight! 

help!

---

### Post by pointone on 2008-02-06
The kernel update changed the UUID of your root partition. You'll need to edit /etc/fstab and point it to the right place. Compare the outputs of:

```
cat /etc/fstab
```

... and:

```
ls /dev/disk/by-uuid -l
```

... to find out what needs fixing.

---

### Post by taurus on 2008-02-06
See if the outputs of these these commands work (and post them here).

```
cat /etc/fstab
ls -la /dev/disk/by-uuid
cat /boot/grub/menu.lst
```

---

### Post by cfar893fm on 2008-02-06
thanks!

so how can i edit these files? the ubuntu live cd will boot in safe graphics mode, but i dont have "permission" to edit the grub menu.lst file or /etc/fstab. (oh yeah. sudo gedit)

and still, the best idea i have is to try pasting the other two uuid numbers in these files, and seeing if it boots. 

what else can i try?

---

### Post by cfar893fm on 2008-02-06
the best i can do is boot from the ubuntu live cd, so a couple commands dont apply.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=98713212-8b92-499a-a46c-dd5e2f1fc0f7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=e78c9cf4-c8a3-4d14-bfe9-ce4b3edcdf13 /home           ext3    defaults        0       2
# /dev/sda5
UUID=0e953d48-5dc6-49b9-8ce3-5874122662b0 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```
```
ubuntu@ubuntu:~$ ls -la /dev/disk/by-uuid
total 0
drwxr-xr-x 2 root root 100 2008-02-07 02:50 .
drwxr-xr-x 5 root root 100 2008-02-07 02:50 ..
lrwxrwxrwx 1 root root  10 2008-02-07 02:50 0e953d48-5dc6-49b9-8ce3-5874122662b0 -> ../../sda5
lrwxrwxrwx 1 root root  10 2008-02-07 02:50 98713212-8b92-499a-a46c-dd5e2f1fc0f7 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-02-07 02:50 e78c9cf4-c8a3-4d14-bfe9-ce4b3edcdf13 -> ../../sda3

```
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=98713212-8b92-499a-a46c-dd5e2f1fc0f7 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=98713212-8b92-499a-a46c-dd5e2f1fc0f7 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

```

---

### Post by cfar893fm on 2008-02-06
i compared the files, the numbers match. also menu.lst. however, the number for sda1 doesnt exist when booting. what is uuid? how can i make menu.lst, fstab, and /dev/by-uuid match, and point to the kernel? 

and why the hell did this happen?

---

### Post by pointone on 2008-02-06
Could you post the output of those two commands from above?

---

### Post by cfar893fm on 2008-02-06
since all i can do is boot from an ubuntu or mepis live cd, the commands dont apply. 
all the same, 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=98713212-8b92-499a-a46c-dd5e2f1fc0f7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=e78c9cf4-c8a3-4d14-bfe9-ce4b3edcdf13 /home           ext3    defaults        0       2
# /dev/sda5
UUID=0e953d48-5dc6-49b9-8ce3-5874122662b0 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```
```
ubuntu@ubuntu:~$ ls -la /dev/disk/by-uuid
total 0
drwxr-xr-x 2 root root 100 2008-02-07 02:50 .
drwxr-xr-x 5 root root 100 2008-02-07 02:50 ..
lrwxrwxrwx 1 root root  10 2008-02-07 02:50 0e953d48-5dc6-49b9-8ce3-5874122662b0 -> ../../sda5
lrwxrwxrwx 1 root root  10 2008-02-07 02:50 98713212-8b92-499a-a46c-dd5e2f1fc0f7 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-02-07 02:50 e78c9cf4-c8a3-4d14-bfe9-ce4b3edcdf13 -> ../../sda3

```
menu.lst
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=98713212-8b92-499a-a46c-dd5e2f1fc0f7 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=98713212-8b92-499a-a46c-dd5e2f1fc0f7 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

```

---

### Post by pointone on 2008-02-06
> **cfar893fm said:**
> since all i can do is boot from an ubuntu or mepis live cd, the commands dont apply. 

Whoops! You're right, of course. I didn't think that through.

Nonetheless, I do have a simple solution: edit menu.lst and change the UUID to the /dev/sd* notation, assuming you know which drive is your root partition. Based on your fstab file, it should be /dev/sda1.

Once you're able to boot into Ubuntu, you can then run those commands to correct the UUIDs... if you want to. UUIDs are considered safer than the /dev/sd* notation, but you probably won't have any problems just leaving it as /dev/sda1 until you try to add a new drive or create a new partition in your system.

---

### Post by Partyboi2 on 2008-02-06
>  some part of the update reset the grub menu.lst file, removing the nosplash and all_ide_generic parameters. if you add your boot  parameters to this part of the grub menu.lst 
> title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,0)
[COLOR=Blue] kernel        /boot/vmlinuz-2.6.22-14-generic[/COLOR] [COLOR=Blue]root=UUID=98713212-8b92-499a-a46c-dd5e2f1fc0f7 ro quiet splash[/COLOR]
initrd        /boot/initrd.img-2.6.22-14-generic
quietwhen there is a kernel upgrade it will remove the boot parameters.
adding them to this part
> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
[COLOR=Red] # kopt=root=UUID=84495dab-d870-4c31-abe5-94e21c04a4ab ro quiet[/COLOR] [COLOR=Red]splash[/COLOR] will make the boot parameters survive kernel upgrades

---

### Post by cfar893fm on 2008-02-07
thanks!!!

---

### Post by cfar893fm on 2008-02-07
thanks! that explains what happened. i still dont see why it did that. luckily i had hours to spend working on this. anyway, on another thread in general help, i learned that replacing the uuid with /dev/sda1 eliminates the problem.

---

### Post by frodon on 2008-02-07
Threads merged

---

