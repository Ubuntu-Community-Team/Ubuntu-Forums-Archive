---
title: "No boot after feasty upgrade (kernel)"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by drodiger on 2007-04-10
I upgraded from 6.10 to 7.04 yesterday. I got some errors during the upgrade and initramfs-tools, kernel-image, and some other packages didn't upgrade. I finally found out that it was because initrd.img was zero size and lilo was reporting error with map something. After I have commented out initrd from the lilo.conf for the older kernel, lilo was able to update boot sector. Then I finished the upgrade, and installed new kernel 2.6.20-14. Lilo did the job, and I rebooted. The boot with the  new kernel didn't work. It was unable to mount root and I ended in busybox. I am only able to boot to the system if I add root=/dev/hda1 instruction to lilo during boot message.
As I see the problem is because fstab is using UUID, maybe even because of initramfs-tools or lilo.

Here is my fstab:
[FONT="Courier New"]proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=55e9ebfc-3241-427a-ae82-dbf7650ed5a1 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda7 -- converted during upgrade to edgy
UUID=c2c2d004-39bf-47ad-8558-ba2717b33122 /home xfs defaults 0 2
# /dev/hda6 -- converted during upgrade to edgy
UUID=ccef1368-bf07-4dcd-90e1-fb25383dbccf /tmp ext3 defaults 0 2
# /dev/hda2 -- converted during upgrade to edgy
UUID=53f982d8-2072-48c1-aece-85136aaa68e3 /usr xfs defaults 0 2
# /dev/hda3 -- converted during upgrade to edgy
UUID=17233fc0-026b-49fb-a412-e5d60bfc4f13 /var xfs defaults 0 2
# /dev/hda5 -- converted during upgrade to edgy
UUID=7fd30cbb-988b-40a4-bdd4-a113c0137fb1 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0[/FONT]

vol_id is correct for all hda partitioons.

Here is mount:
[FONT="Courier New"]/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/mapper/hda7 on /home type xfs (rw)
/dev/mapper/hda6 on /tmp type ext3 (rw)
/dev/mapper/hda2 on /usr type xfs (rw)
/dev/mapper/hda3 on /var type xfs (rw)
[/FONT]

Here is ls -al /dev/hda?
[FONT="Courier New"]dejanr@server:/dev$ ls -la hda?   
brw-rw---- 1 root disk 3, 1 2007-04-10 16:16 hda1
brw-rw---- 1 root disk 3, 2 2007-04-10 17:41 hda2
brw-rw---- 1 root disk 3, 3 2007-04-10 17:41 hda3
brw-rw---- 1 root disk 3, 4 2007-04-10 17:41 hda4
brw-rw---- 1 root disk 3, 5 2007-04-10 17:41 hda5
brw-rw---- 1 root disk 3, 6 2007-04-10 17:41 hda6
brw-rw---- 1 root disk 3, 7 2007-04-10 17:41 hda7[/FONT]

And here is ls -la /dev/mapper/
[FONT="Courier New"]brw-rw----  1 root disk 254,  0 2007-04-10 15:41 hda1
brw-rw----  1 root disk 254,  1 2007-04-10 15:41 hda2
brw-rw----  1 root disk 254,  2 2007-04-10 15:41 hda3
brw-rw----  1 root disk 254,  3 2007-04-10 15:41 hda5
brw-rw----  1 root disk 254,  4 2007-04-10 15:41 hda6
brw-rw----  1 root disk 254,  5 2007-04-10 15:41 hda7
[/FONT]

What the hell is /dev/mapper? I mean, should I change fstab, lilo.conf or initramfs-tools?

Thanks

---

### Post by bulldog on 2007-04-10
If you add the line 'root=/dev/hda1' to your Lilo? and it boots fine after that,the fault is in Lilo?

Are you sure you use Lilo,because GRUB is the default boot manager for ubuntu.

How to change Lilo to boot correct, I don't know,can tell you a lot about GRUB,but Lilo is something I never used.

---

### Post by drodiger on 2007-04-10
I installed 6.06 and took lilo as my boot manager (because I am more familiar with lilo). I upgraded to 6.10, and yesterday wanted to upgrade to 7.04.

Actually when I get lilo: prompt I enter "Linux root=/dev/hda1" and press Enter to boot kernel.

Well I am not sure where the problem is. Should I change fstab?
Can I change UUID to /dev/hda1 in fstab? Will it work with 2.6.20 kernel ? Maybe the problem is with initramfs-tools. When update-initramfs is run (after the kernel upgrade), I am getting messages that /proc/partitions doesn't match /dev directory structure.
Name Change: /dev/dm-0 -> /dev/evms/hda1

But I am not using mdadm or lvm, so I think this is only a warning.
Well I have /dev/hda1 and /dev/mapper/hda1. Hmmm. I see now that in "cat /proc/partitions" both hda1 and dm-1 exist, one is for /dev/hda1 and the other is for /dev/mapper/hda1.
hda1 is major 3 minor 1 (the same in /dev/hda1), and dm-1 is major 254, minor 1 (mapper).

---

### Post by elinap on 2007-06-06
I think I am having the same problem.
If I enter root=dev/hda7 at the LILO prompt it books ok. Otherwise, it does not.

The contents of lilo.conf has root=/dev/hda7

When I run lilo I get the message:
Warning: '/proc/partitions' does not match '/dev' directory structure
Name change: '/dev/dm-0' -> '/dev/evms/hda1'

The contents of fstab are:
....
# /dev/hda7  - - converted during upgrade to edgy
UUID=a8c65f9d-2ea7-...etc  ext3 defaults,errors=remount -ro 0 1

I have recently deleted one of my windows partitions (installed before the linux), with the result that ubuntu would not boot. Then, I recreated the windows partition.
After recreating the partition, it booted ok.
But, after doing the latest software updates, it does not.

Any help/suggestions would be much appreciated.

Eli

---

### Post by drodiger on 2007-06-06
I have put append="root=/dev/something" in the lilo.conf and it is working.

---

