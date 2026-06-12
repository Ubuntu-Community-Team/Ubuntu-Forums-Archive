---
title: "Failed attempt at triple booting Windows XP with 7 and 12.04 LTS Ubuntu"
date: 2012-04-09
forum: Installation &amp; Upgrades
---

### Post by EEEUser22 on 2012-04-09
Okay so I have an Asus EEE PC 1005HA-PU17 that I had dual booting Ubuntu 12.04 LTS and Windows 7. I was just wanting to put Windows XP just cause (stupid choice). So I partitioned everything correctly and set off 30 GB of my harddrive to it and formatted it to ntfs by using gparted within Ubuntu. So I booted the Windows XP cd with my external USB DVD drive and it installed the setup files to the partition and said it had to restart so when it restarted it said "error loading operating system" so I was just gonna reinstall Ubuntu with a live cd to bring the grub back and fix it all (because that has happened to me before when I tried to triple boot Chromium OS and it fixed everything back to where it was) and when I brought up gparted with the bootable live cd it didn't see the partitions at all, just the whole hard drive to write on. I thought I had formatted my whole drive on accident but I didn't because I put in the bootable Windows 7 recovery disk that was included with my computer and it saw all the partitions and their sizes but I couldn't edit them, all I could do was format it all and start over. Now what I want to do is fix everything without formatting my whole system if I can. I need some files off of the Windows 7 partition and do not want to lose anything I have. So any help will be greatly appreciated!!

---

### Post by oldfred on 2012-04-10
Welcome to the forums.

Did you install XP to a primary NTFS partition?

To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

You just may have the Windows boot loader in the MBR after the XP install, but if boot flag is not on a primary partition it will not boot. You can move boot flag back to your Windows 7 boot partition (the 100MB hidden one) or reinstall grub2's boot loader.

May be best to run the bootinfoscript which documents system so we can make better suggestions before you do anything.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

Post link the Boot-Repair creates for output from bootinfoscript.

---

### Post by Moople on 2012-04-10
For a fact, if you installed Windows XP on a NTFS partition, it's going to have its own bootloader, with its own settings. So, in a case, the default operating system WILL become XP. This is why I would recommend sticking with a bootloader (GRUB) for all operating systems. I recommend replacing the bootloader on 7 and XP.

---

### Post by EEEUser22 on 2012-04-10
I ran boot repair and got this output [http://paste.ubuntu.com/922858/](http://paste.ubuntu.com/922858/) .It installed everything successfully and grub is now back and I can see my Ubuntu and Win 7 and I can choose Ubuntu and boot into it but when I try to go to my Win 7 boot then it just blinks an underscore back and forth. How do I fix the Win 7 partition?

---

### Post by EEEUser22 on 2012-04-10
And also when I boot into Ubuntu and use gparted it still shows my whole harddrive as unallocated space with no partitions.

---

### Post by darkod on 2012-04-10
I don't know how you created the partition for XP, but I don't see XP reported as installed anywhere on the disk.

And the reason why Gparted doesn't show partitions, is because you managed to overlap sda3 with sda4. Look in the results in Drive / Partition Info section (first half of the results file). It clearly says sda3 overlaps with sda4.

On top of that, three swap partitions are reported there. I guess you do reinstalling not knowing that it doesn't use existing partitions unless you use the manual method and tell it to.

If sometimes you need to restore Grub2 on the MBR (like after a windows install), you can restore just Grub2, you don't need to reinstall the whole ubuntu. That just creates new partitions because ubuntu will never overwrite existing partition and use it unless you specifically tell it to.

---

### Post by EEEUser22 on 2012-04-10
This XP never installed properly but it was suppose to be under sda2. That is it's partition. How do I get sda3 and sda4 to not overlap? And how do I properly delete the swap partitions I don't need.

---

### Post by darkod on 2012-04-10
If you want to delete the extra swap partitions, that could solve the overlap problem at the same time because sda4 is a swap partition. It might be the one used right now, but even if it is and you delete it, you can easily configure ubuntu to use one of the others. They are all approx the same size.

I am not sure which tool would not have issues with the overlap so it can show you the partitions and gives you a chance to delete one. Try cfdisk first. You will need to run it from live mode, in terminal try:
sudo cfdisk /dev/sda

That should open sort of text/gui table with the partitions. Double check that /dev/sda4 is a swap partition and delete it. The menu of cfdisk is very easy, you should have no problem figuring it out.

You could delete one more swap partition, /dev/sda6, but that won't help much. The main issue is to delete /dev/sda4 because then the overlap should go away too.

Once you delete it, write the changes before you exit cfdisk (option Write).

After that, without restarting, post the output of:
sudo fdisk -l (small L)

---

### Post by EEEUser22 on 2012-04-10
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x75a91237

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   299648384   149824161    7  HPFS/NTFS/exFAT
/dev/sda2       299649024   375187455    37769216    7  HPFS/NTFS/exFAT
/dev/sda3       375189502   488394751    56602625    5  Extended
/dev/sda5       375189504   379359231     2084864   82  Linux swap / Solaris
/dev/sda6       383537152   480020479    48241664   83  Linux

Disk /dev/sdb: 4022 MB, 4022337024 bytes
124 heads, 62 sectors/track, 1021 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e15fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     7849447     3924693    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$

---

### Post by darkod on 2012-04-10
Sorry for the late reply, you caught me on the train going home.

Looks perfect, no message from fdisk about overlapped partitions. And if you look at the start/end values, they are good.

I said to post without exiting live mode so you could check the fstab in case you need to change the UUID of the swap partition in it.

From live mode (or your hdd ubuntu), you can check partition UUIDs with:
sudo blkid

In case ubuntu complains about missing swap and doesn't boot, from live mode open /dev/sda6, and open /etc/fstab.

Check what UUID is specified for swap. Change if necessary with the UUID you got for /dev/sda5 with the blkid command.

That should sort it out.

---

### Post by EEEUser22 on 2012-04-10
It is fine. It say error loading partition when my computer boots up and says grub rescue under that. I'm not real sure how to change the UUID like you specified but I typed in sudoblk and this popped up:

ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="WIN7" UUID="D8F06420F064075A" TYPE="ntfs" 
/dev/sda2: UUID="DE283C4E283C27C3" TYPE="ntfs" 
/dev/sda5: UUID="ac7982c1-318f-492e-b46c-c11f25c7afa6" TYPE="swap" 
/dev/sda6: UUID="d04459a5-e232-4d22-a1f1-72f30677dffb" TYPE="ext4" 
/dev/sdb1: UUID="B85F-0828" TYPE="vfat"

But idk know how to do anything passed there.. I'm still on the Live CD. Can you elaborate more on how to do this part when you said "In case ubuntu complains about missing swap and doesn't boot, from live mode open /dev/sda6, and open /etc/fstab.

Check what UUID is specified for swap. Change if necessary with the UUID you got for /dev/sda5 with the blkid command." Sorry but I am not very tech savvy with Ubuntu and terminal much at all. So easy steps will help me.

---

### Post by darkod on 2012-04-10
OK, the grub rescue error seems to be because it is looking for the grub files on a wrong partition. Now that you have less partitions, the numbers don't match.

To fix that, from live mode open terminal and execute:
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

That will sort out grub.

While you are there and sda6 is mounted with the previous command, post also the output of:
```
cat /mnt/etc/fstab
```

In there we will see if the swap UUID needs to be changed.

---

### Post by EEEUser22 on 2012-04-10
This is my output from cat /mnt/ect/fstab:

ubuntu@ubuntu:~$ cat /mnt/etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=d04459a5-e232-4d22-a1f1-72f30677dffb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=aeb24a49-dd94-4423-94d9-08bb5fa7a6d8 none            swap    sw              0       0

The command before that to fix grub ran and said Installation complete. No errors.

---

### Post by darkod on 2012-04-10
You see, in /etc/fstab you have UUID for swap ending in 'a6d8' and in your post #11 the blkid output says the only remaining swap partition on the disk has UUID ending in 'afa6'.

You will need to replace the UUID in /etc/fstab with the UUID blkid returned for /dev/sda5. The UUID for the root partition is correct.

If you still haven't rebooted you should be able to edit /etc/fstab with:
gedit /mnt/etc/fstab

That should open the GUI text editor. Just paste the correct UUID in there replacing the wrong one. Save and close the file. Reboot.

If you did reboot already, you can choose whether to edit from live mode, or you can boot your hdd ubuntu (if it works) and edit it. If you select to do it in live mode again, you will need to run the mount first,  before you can use the gedit command above. First mounting /dev/sda6 at /mnt.
sudo mount /dev/sda6 /mnt

The same applies after changing the UUID. Reboot.

After all this, ubuntu should be working fine. You should be able to install XP onto the /dev/sda2 partition without problems. Don't forget it will overwrite grub2 on the MBR. To restore it from live mode you have instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

EDIT: If you want to have both win7 and XP in the grub2 boot menu, you will need to do a small "trick" BEFORE installing XP. If you simply install, it will combine the boot files with win7. That's how windows does it when you have more than one version. But if you move the boot flag to /dev/sda2 first and then install XP, it will leave the boot files on /dev/sda2 together with XP. This will allow grub2 to create separate entries in the boot menu for win7 and XP.

---

### Post by EEEUser22 on 2012-04-10
Okay everything is back to normal with Ubuntu and I really don't want to do XP so can I just delete that partition and it be safe? Or what? And Ubuntu works fine but when I select Windows 7 it just shows a black screen and nothing else. Any tips on that? That's my main OS and need to get that working.

---

### Post by darkod on 2012-04-10
Yes, you don't need to install XP if you don't want to. You don't need to delete the partition too, you can just reformat it as NTFS and both win7 and ubuntu can use it.

If win7 is not booting maybe something git corrupted during the partitioning process (we already saw the disk ended up with overlapped partitions).

The first thing to try is booting ubuntu and in terminal:
sudo update-grub

Restart and try to boot win7. If it still doesn't work, try repairing the boot process with the win7 dvd. That link I posted about bootloaders has the procedure how to do it with the command line from the win7 dvd. It's better than the automated process.

That will also overwrite grub2 on the MBR, you will need to restore it.

---

### Post by EEEUser22 on 2012-04-10
Thanks for the help that fixed it! Thanks for the explanation of what I was doing and what happened.

---

### Post by darkod on 2012-04-11
No problem.

Please mark the thread as Solved. You can do that in Thread Tools above the first post.

---

