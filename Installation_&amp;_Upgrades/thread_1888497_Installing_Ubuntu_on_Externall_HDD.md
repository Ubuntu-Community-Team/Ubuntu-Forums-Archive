---
title: "Installing Ubuntu on Externall HDD"
date: 2011-11-29
forum: Installation &amp; Upgrades
---

### Post by Kalnor on 2011-11-29
Hi.

I've already looked around the web and still can't solve this problem. I have a 1TB Seagate Ext HDD and have a ntfs partition on it which holds my data. I want to install Ubuntu 11.10 on it but it just keeps failing. I run Windows 7 Professional x86 on the 500GB internal hard drive.

I did the following. Shrinked the ntfs (sdb1) partition to 750gb and created the following partitions for Ubuntu:

sdb2 ext4 (tried ext2 as well) /boot (300mb)
sdb5 ext4 / (root) (10gb)
sdb6 swap (can't remember how much space)
sdb7 ext4 /home (rest of space)

I selected the boot loader to get installed on sdb drive which is the Seagate 1TB.

The installation completes and tells me to reboot the computer, when I do that and try to boot from the USB HDD I get redirected to Grub Rescue prompt and the message I get is 'unknown file system'.

I've been faced with the Grub Rescue prompt before when I didn't install the boot loader in the appropriate space. When I got this sorted (formatted the partitions and started again) I got this problem.

If I don't manually tell the computer to boot from USB HDD it boots to Windows because it is before the USB HDD in the boot order.

I've also tried reinstalling the Grub 2 boot loader on the MBR of the Ext HDD by following the on-line instructions but that didn't help either.

Could you please help me out as I have no ideas now.

Thanks.

---

### Post by deonis on 2011-11-29
Did you try to use Start up Disk Creator to make the life image work from HDD? Was it working? Can you df -h in terminal with your hdd attached to the computer.

---

### Post by raja.genupula on 2011-11-29
1...look at my signature for grubrecovery link and try that .
2.... in my signature itself bootinfoscript will be there , post that also

Thank you

---

### Post by Kalnor on 2011-11-29
@Denis I didn't use the disk creator. Here is the df -h result:

```
Filesystem            Size  Used Avail Use% Mounted on
/cow                 1007M  172M  836M  17% /
udev                 1000M   12K 1000M   1% /dev
tmpfs                 403M  880K  402M   1% /run
/dev/sr0              696M  696M     0 100% /cdrom
/dev/loop0            668M  668M     0 100% /rofs
tmpfs                1007M  1.2M 1006M   1% /tmp
none                  5.0M  4.0K  5.0M   1% /run/lock
none                 1007M  216K 1007M   1% /run/shm
/dev/sda2             173G   97G   76G  57% /mnt/clean/sda2
/dev/sdb1             708G   65G  643G  10% /mnt/clean/sdb1
/dev/sdb5             9.2G  2.8G  6.0G  32% /mnt/clean/sdb5
/dev/sdb7             210G  188M  199G   1% /mnt/clean/sdb7
/dev/sda1             293G  135G  159G  46% /mnt/clean/sda1
/dev/sdb2             277M   38M  225M  15% /mnt/clean/sdb2
```@raja.genupula I'm just looking at the Boot-Repair now. Will post the result of it soon. The boot info script is attached in the post.

---

### Post by Kalnor on 2011-11-29
I tried the recommended option in Boot-Repair and it didn't work. I'll try the other way which is explained in your link.

Edit: I need to restore the lilo boot loader now as Windows 7 doesn't load and I just get sent to Grub Rescue prompt which says 'device not found: blah blah blah'.

Need help ASAP.

Thanks.

Edit: I used the following code to get the Windows back up and running but the boot loader problem for Ubuntu is still not solved so I'm waiting for your help.

```
sudo apt-get install lilo 
sudo lilo -M /dev/sda mbr
```

---

### Post by raja.genupula on 2011-11-29
put a live cd and run live system .
open terminal and do this

```
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-partition=/mnt /dev/sdb
```

restart and choose your ubuntu in grub if its then fine.
 
if failed, then again live cd..terminal ...and do this. 

```
sudo mount /dev/sdb2 /mnt
sudo grub-install --root-partition=/mnt /dev/sdb
```

I am sure any of the thing going to help you . 

all the best.

---

### Post by Kalnor on 2011-11-29
I get this error when running

```
sudo grub-install --root-partition=/mnt /dev/sdb
```

Unrecognized option `--root-partition=/mnt'

---

### Post by efflandt on 2011-11-29
Wrong option, it should be **--boot-directory=/mnt** (not --root-partition).  See **man grub-install**

However, that may not fix the issue because some computers seem unable to boot very far out on an external drive even if they can boot farther out on an internal drive.  For example my Dell desktop purchased last year can boot fine with Ubuntu near the end of a 160 GB USB drive, and boots Maverick fine about 900 GB into its 1 TB internal drive. But it is unable to boot Ubuntu farther out on a 500 GB external drive that boots fine with an old Dell laptop from about 2005 or 6, or can be mounted on the Dell once it boots something that it can.  Even if you boot grub on an internal drive and know your way around the grub command line, you may be able to see the / directory of partitions and maybe /boot, but maybe not /boot/grub if you are getting that grub rescue prompt when normally attempting to boot the external drive.

I have never found any sensible explanation why "some" computers that can boot a large internal drive cannot boot a smaller large external drive.

What I have not tried is making a /boot partition at the beginning of one of the larger external drives to see if grub can find the rest of itself that way.

---

### Post by oldfred on 2011-11-29
You have a separate /boot so you have to mount both to reinstall grub. Most desktops do not need a separate /boot, but as efflandt says we have seen issues with large / (root) partition. You have a separate /home so your root is not huge.

#If separate /boot & Natty grub 1.99 or later
$ sudo mount /dev/sdb5 /mnt
$ sudo mount /dev/sdb2 /mnt/boot
$ sudo grub-install --boot-directory=/mnt/boot /dev/sdb

Did you encrypt swap?
/dev/mapper/cryptswap1 none swap sw 0 0

---

### Post by Kalnor on 2011-11-30
I see that it can be an unsolvable problem then.

I tried the code you gave me but it didn't help either. I get sent to grub rescue prompt and the message is 'unknown filesystem'. And no I didn't encrypt the swap.

Is there anything I can do to solve this problem?

---

### Post by james2b on 2011-11-30
When you have some Linux installed on an external hard drive, and you have Windows and or some Linux on your internal drive, then it is best to have the boot loader installed onto MBR of the internal drive. So with your Windows 7 on the internal you should use the windows boot manager, and add your Linux with Easy BCD tool which is found here; [http://neosmart.net/EasyBCD/](http://neosmart.net/EasyBCD/) , this is really true if your computer is a Dell with that Data Safe and 7, as it will just remove grub and put back the windows boot loader. Also this will allow you to boot the PC without the external USB hard drive connected.

---

### Post by Kalnor on 2011-11-30
Thanks for all of your help. I have managed to solve this problem by removing the /dev/sdb1 partition (750GB) and all the Linux partitions. I then re-created the Linux partitions so that the /boot partition is at the very beginning of the hard drive because according to effland there is a problem on some computers when the boot partition is too far on the drive. This has solved the problem and I now have Ubuntu running of the external hdd.

Thanks a lot guys and I hope others will find this solution useful as well.

---

