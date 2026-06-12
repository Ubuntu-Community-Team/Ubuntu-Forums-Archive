---
title: "[SOLVED] intrepid ibex install guide when you have software raid (dmraid) - grub erro"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by scurry7 on 2008-11-05
This is my install guide for installing intrepid (and previous versions also) on my system using dmraid (for my software raid setup).  When I first tried to install it would not detect my existing partitions, so I ran `apt-get update; apt-get install dmraid'.  then after the install I got a grub error 15.  it sucked....anyway I got it going and here is how i did it!

before you begin you may have to sudo before some commands, and most things are run from a terminal.  If anyone see a better way to do thing let me know please, and please post if this helps you out (it took me a while to get this together i hope it helps people).


**1. boot into live cd**

**2. install dmraid for software raid support**
 > ctrl+alt+f2  > apt-get update; apt-get install dmraid -y
		Notice: after dmraid setup is complete /dev/mapper/??? refer to that as your raided hard drive (normal sata drive would be /dev/sda, yours is /dev/mapper/something (I will refer to it as nvidia_deebdjei because that is what mine is)

**3. install base system**
 > ctrl+alt+f7  --  finish the install
		Note:  when install completes it leaves you at the live cd desktop dont reboot
		notice:  The `df -h` command (from a termial (press alt+f2 then type xterm)) shows mounted file systems (take note of /target and or /target/home)

**4. switch on your new system, re-mount /proc, /sys, /dev**
 > mount --bind /dev/ /target/dev
 > mount -t proc proc /target/proc
 > mount -t sysfs sys /target/sys
 > chroot /target

**5. install ubuntu packages needed**
 > apt-get update
 > apt-get install language-pack-en ubuntu-standard linux-generic dmraid grub
		Note: somethings will just be updated


**6. fix boot loader (grub)**
...copy grub essential files
 > mkdir /boot/grub
 > cp /usr/lib/grub/somefolder/* /boot/grub/   
	Note: somefolder is dependant on your system (i think there should only be 1 folder there)
		Note: This will copy the staging file for the various filesystem in your boot partition. In my example the directory is “/usr/lib/grub/x86_64-pc/” and the files that are copied are “e2fs_stage1_5&#8243;, “jfs_stage1_5&#8243;,…

**7. configure grub**
 > grub 
Note: enters grub interactive shell
 > device (hd0) /dev/mapper/nvidia_deebdjei   
		note: not the partition but the disk  (not nvidia_deebdjei1 but nvidia_deebdjei)
 > root (hd0,1)
		note: (hd0,0 is 1st disk, 1st partition.  My linux partition is on the 1st disk, 2nd partition so i did `root (hd0,1) `
		note: i got an error message but it still worked
 > setup (hd0)  
		note: i got an error message but it still worked
 > quit (exit from grub shell)
 > update-grub
		note: it will ask to you create a menu.lst  say yes

**8. verify you menu.lst is correct before rebooting**
 > nano /boot/grub/menu.lst
 > set the groot option to point to where your harddrive and partition that /boot/grub is located on 
		example: `groot=(hd0,1)` in my case 
		note: it should be necessary to uncomment that line
 > modify, inside “kernel” items, the “root” value to “/dev/mapper/nvidia_deebdjei2&#8243; (the partition that gets mounted as / aka:your root partition)
		example: (this is my /boot/grub/menu.lst file)
```

default         0
timeout         3
hiddenmenu
groot=(hd0,1)
title           Ubuntu 8.10, kernel 2.6.27-7-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.27-7-generic root=/dev/mapper/nvidia_deebdjei2 ro quiet splash 
initrd          /boot/initrd.img-2.6.27-7-generic
title           Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.27-7-generic root=/dev/mapper/nvidia_deebdjei2 ro  single
initrd          /boot/initrd.img-2.6.27-7-generic
title           Ubuntu 8.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
title           Windows XP Media Center ed.
root            (hd0,0)
makeactive
chainloader     +1


```

**9. REBOOT!!!** (this is the scary part....)
		Note: if it works you are awesome, if not don't give up!

tags: dmraid ubuntu intrepid ibex software raid
references: [http://bbossola.wordpress.com/2008/03/07/dmraid-on-ubuntu-with-sata-fakeraid/](http://bbossola.wordpress.com/2008/03/07/dmraid-on-ubuntu-with-sata-fakeraid/)

---

### Post by JD82 on 2008-11-26
Or just use the Alternate Install CD:
> According to [the latest FakeRAID spec]("https://wiki.ubuntu.com/DmraidSupport"), Intrepid users can now install directly to SATA RAID with no additional setup or configuration required. This is is not yet supported in the Ubiquity graphical installer so *you must use the Alternate Install CD.* The installer will prompt you to activate the RAID partitions, which will make them available to the partitioner and allow you to continue with the installation as normal.([source]("https://help.ubuntu.com/community/FakeRaidHowto"))

;)

---

