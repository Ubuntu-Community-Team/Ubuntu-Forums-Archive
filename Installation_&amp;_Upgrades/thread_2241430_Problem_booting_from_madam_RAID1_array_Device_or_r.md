---
title: "Problem booting from madam RAID1 array: Device or resource busy"
date: 2014-08-26
forum: Installation &amp; Upgrades
---

### Post by bobbus2 on 2014-08-26
Hi,  I'm trying to boot from an mdadm RAID1 array on 14.04.  

From the Grub2 console I can see and access the files on the raid Array
```

ls
> (hd1) (hd1,msdos1) (hd1,msdos2) (md/0) (md/1)

set ROOT=(md/1)
ls /
>initrd.img vmlinuz bin/ boot/ dev/ .... and all the expected folders

```
 

When I continue to boot from the array ...
```

linux /vmlinuz root=/dev/md1 nodmraid bootdegraded=true bootdelay=2000
initrd /initrd.img
boot

```

... it fails to mount md1 to the system root with the message:
```

mounting /dev/md1 on /root failed: Device or Resource busy

```

Additional information:  
- md0 on sdb1 is SWAP & md1 on sdb2 is the system array 
- using UUID to identify md1 makes no difference 
- incrementing the delay to the max 10000 makes no difference
- sda has working installation on 14.04 and can mount md1 to /mnt with no problem
- the array is degraded, having only one disk, but assembles and mounts correctly other than boot.

One thought ... I had to include mdraid1x on the grub install just to be able to see the array ...
```

grub-install --modules=mdraid1x /dev/sdb

```
... are there any other modules I need to pre-load on install?


Any help appreciated.

---

### Post by bobbus2 on 2014-08-27
**Update:**

I can access md1 immediately I get a prompt (initramfs or busy box).  When checking the delay times it looks like bootdelay / rootdelay is simply being ignored and the kernel is trying to load the roots asap.

---

### Post by bobbus2 on 2014-09-03
The answer is that initramfs was trying to mount the array to / (root) before the array had assembled.  The rootdelay command on loading the kernel is ignored .... seems like a bug to me.

The solution was to add a delay script into the initramfs sequence to allow time for the array to assemble.

```


[COLOR=#005CFF][FONT=Helvetica]echo “sleep 60" > /etc/initramfs-tools/scripts/init-premount/delay_for_raid_array_to_build_before_mounting

update-initramfs -u[/FONT][/COLOR]

```

Lots of hours wasted because the documented  'root delay' kernel command doesn't work :(

---

### Post by baldrick-free on 2014-09-06
The script needs to be executable, so:

[COLOR=#005CFF][FONT=Helvetica]echo “sleep 60" > /etc/initramfs-tools/scripts/init-premount/delay_for_raid_array_to_build_before_mounting
chmod a+x [/FONT][/COLOR][COLOR=#005CFF][FONT=Helvetica]/etc/initramfs-tools/scripts/init-premount/delay_for_raid_array_to_build_before_mounting[/FONT][/COLOR][COLOR=#005CFF][FONT=Helvetica]
update-initramfs -u[/FONT][/COLOR]

---

### Post by lopaka-z on 2014-11-27
> **bobbus2 said:**
> The answer is that initramfs was trying to mount the array to / (root) before the array had assembled.  The rootdelay command on loading the kernel is ignored .... seems like a bug to me.

The solution was to add a delay script into the initramfs sequence to allow time for the array to assemble.

```


[COLOR=#005CFF][FONT=Helvetica]echo “sleep 60" > /etc/initramfs-tools/scripts/init-premount/delay_for_raid_array_to_build_before_mounting

update-initramfs -u[/FONT][/COLOR]

```

Lots of hours wasted because the documented  'root delay' kernel command doesn't work :(


Thanks so much for sharing this!  Because of this, instead of spending 20hrs working on this same problem, I only had to waste 10hrs :)  Thanks again!

---

### Post by pmackinney on 2015-01-09
Thanks here also. Same problem, solution worked perfectly. A bit more detail on how to fix:

After booting from Ubuntu Live CD:
        ```
$ sudo su -
# cat /proc/mdstat
Personalities : ...
md127 : active raid1 sda[1] sdj[0]
         78150656 blocks [2/2] [UU] ...
# ls -l /dev/md127*
/dev/md127  /dev/md127p1  /dev/md127p2  /dev/md127p3
# blkid /dev/md127p2
/dev/md127p2: UUID="01234567-89ab-cdef-0123-0123456789ab"  TYPE="ext4"
```
I know that md127p2 is the right partition, and the UUID was the same as grub's "root=UUID=..." argument, so let's try the fix!
```
# mount /dev/md127p2 /mnt
# for D in /dev /dev/pts /proc /sys; do mount -o bind $D /mnt$D; done
# chroot /mnt
# echo ... (see bobbus2's post)
# chmod ... (see baldrick-free's follow-up)
# udate-initramfs -u
# exit
# shutdown -r now
```
And it boots!

---

