---
title: "Impossible to boot after increasing Ubuntu 14.04 LTS partition !"
date: 2015-09-06
forum: Installation &amp; Upgrades
---

### Post by gperrot on 2015-09-06
Hello !

I am using Ubuntu 14.04 LTS on my laptop with a dual boot (Win7). Last days, using a LiveUSB, I decrease the size of my Win7 partition and I increase the size of my Ubuntu partition. Unfortunately, during the resize of the Ubuntu partition, my laptop was not well connected to main electricity and end of battery life happened before the end of the resizing process...). After that, I was not able to boot on LiveUSB (I recreated one). Furthermore, I was not able to boot on hard disk with dual partition :
```

error : attempt to read or write outside of partition
Entering rescue mode...
grub rescue

```
Now, after booting on my new LiveUSB, I can have some diagnostic command results :
```

ubuntu@ubuntu:~$ df
Filesystem     1K-blocks      Used Available Use% Mounted on
/cow              999320    104688    842204  12% /
udev             1938416         4   1938412   1% /dev
tmpfs             389984      1228    388756   1% /run
/dev/sdb1        3914192   2078080   1836112  54% /cdrom
/dev/loop1        985344    985344         0 100% /rofs
none                   4         0         4   0% /sys/fs/cgroup
tmpfs            1949908      1028   1948880   1% /tmp
none                5120         4      5116   1% /run/lock
none             1949908        80   1949828   1% /run/shm
none              102400        36    102364   1% /run/user
/dev/sda3      153471104 143977488   9493616  94% /media/ubuntu/C8D8BA53D8BA400C
/dev/loop0        999320    104688    842204  12% /media/ubuntu/01322115-d3d3-46ce-83a8-0143153abebb

```
It seems that the content of Win7 partition (sda3) is OK.

When I try to see the content of the Ubuntu partition (sda6), here is the error message :
```

Unable to access “147 GB Volume”
Error mounting /dev/sda6 at /media/ubuntu/370e34c9-1ba6-4cca-a1b2-22bbd261f22b: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda6" "/media/ubuntu/370e34c9-1ba6-4cca-a1b2-22bbd261f22b"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
If I try to see syslog messages about my sda partitions :
```

ubuntu@ubuntu:~$ dmesg  |grep sda
[   10.515500] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[   10.515613] sd 0:0:0:0: [sda] Write Protect is off
[   10.515616] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   10.515775] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   10.583508]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[   10.584836] sd 0:0:0:0: [sda] Attached SCSI disk
[   13.670166] EXT4-fs (sda6): error loading journal
[   34.119371] Adding 4042748k swap on /dev/sda5.  Priority:-1 extents:1 across:4042748k FS
[  334.553551] EXT4-fs (sda6): error loading journal

```
I would like to repair my sda6 partition in order to restore some files I didn't backup before and better than that, if it is possible, restore my dual boot ubuntu/win7 in order to avoid reinstallation of both OS. 

Could you help me to achieve that please ?

Thanks in advance for your help !!!

Gigi

---

### Post by yancek on 2015-09-06
You could try from the Live usb to repair the filesystem on sda with fsck.  The second post at the link below discusses it and gives an example command.

[http://ubuntuforums.org/showthread.php?t=1508294](http://ubuntuforums.org/showthread.php?t=1508294)

---

### Post by Topsiho on 2015-09-06
I guess that the UUID was changed by the repartitioning, and so your /etc/fstab is not correct anymore, and the partition could not be found.
See your file /etc/fstab and follow it's suggestion to use 'blkid' to find the correct UUID's of the partitions. Then correct (as root, using sudo and gedit) /etc/fstab 

Topsiho

---

### Post by gperrot on 2015-09-06
[B]Thanks a lot for your help ! 

I tried [COLOR=#000000][I]sudo e2fsck -f -y -v /dev/sda6 and a lot of errors have been corrected on sda6.
[/I][/COLOR]
Now, I can mount /dev/sda6.

However, when I tried to boot on hard disk, I have the error message :
[/B]
[FONT=arial]*error : file '/boot/grub/i386-pc/normal.mod' not found.*[/FONT]
[FONT=arial]*Entering rescue mode...*[/FONT]
[FONT=arial]*grub rescue>*[/FONT]

[B]When I check the contents of sda6, it seems that some of its content is missing :

[/B][I][FONT=arial]ubuntu@ubuntu:~$ df [/FONT]
[FONT=arial]Filesystem     1K-blocks     Used Available Use% Mounted on[/FONT]
[FONT=arial]/cow              999320   111248    835644  12% /[/FONT]
[FONT=arial]udev             1938416        4   1938412   1% /dev[/FONT]
[FONT=arial]tmpfs             389984     1232    388752   1% /run[/FONT]
[FONT=arial]/dev/sdb1        3914192  2078080   1836112  54% /cdrom[/FONT]
[FONT=arial]/dev/loop1        985344   985344         0 100% /rofs[/FONT]
[FONT=arial]none                   4        0         4   0% /sys/fs/cgroup[/FONT]
[FONT=arial]tmpfs            1949908     1028   1948880   1% /tmp[/FONT]
[FONT=arial]none                5120        4      5116   1% /run/lock[/FONT]
[FONT=arial]none             1949908       76   1949832   1% /run/shm[/FONT]
[FONT=arial]none              102400       40    102360   1% /run/user[/FONT]
[FONT=arial]/dev/sda6       66588320 10701080  52488280  17% /media/ubuntu/370e34c9-1ba6-[/FONT][FONT=arial]4cca-a1b2-22bbd261f22b[/FONT][/I]

[I][FONT=arial]ubuntu@ubuntu:/media/ubuntu/[/FONT][FONT=arial]370e34c9-1ba6-4cca-a1b2-[/FONT][FONT=arial]22bbd261f22b$ ls -a[/FONT]
[FONT=arial].   bin    initrd.img      lost+found  opt   run  vmlinuz[/FONT]
[FONT=arial]..  cdrom  initrd.img.old  mnt         root  var  vmlinuz.old[/FONT]
[/I]
[B]Any idea how to progress now ?

Thanks in advance for your help.

Gigi[/B]

> **yancek said:**
> You could try from the Live usb to repair the filesystem on sda with fsck.  The second post at the link below discusses it and gives an example command.

[http://ubuntuforums.org/showthread.php?t=1508294](http://ubuntuforums.org/showthread.php?t=1508294)

---

### Post by gperrot on 2015-09-06
For information, here is my boot-info link : [http://paste.ubuntu.com/12295989](http://paste.ubuntu.com/12295989)

---

### Post by gperrot on 2015-09-07
I don't understand where is my /home contents :

```
[FONT=arial]ubuntu@ubuntu:~$ ls -la /media/ubuntu/SDA6[/FONT]
[FONT=arial]total 288[/FONT]
[FONT=arial]drwxr-xr-x    10 root root   4096 août  27 18:35 .[/FONT]
[FONT=arial]drwxr-x---+    3 root root   4096 sept.  7 16:48 ..[/FONT]
[FONT=arial]drwxr-xr-x     2 root root   4096 août  27 18:11 bin[/FONT]
[FONT=arial]drwxrwxr-x     2 root root   4096 août  27 18:00 cdrom[/FONT]
[FONT=arial]lrwxrwxrwx     1 root root     33 août  27 18:35 initrd.img -> boot/initrd.img-3.19.0-26-[/FONT][FONT=arial]generic[/FONT]
[FONT=arial]lrwxrwxrwx     1 root root     33 août  27 18:09 initrd.img.old -> boot/initrd.img-3.19.0-25-[/FONT][FONT=arial]generic[/FONT]
[FONT=arial]drwx------  2197 root root 258048 août  27 17:57 lost+found[/FONT]
[FONT=arial]drwxr-xr-x     2 root root   4096 avril 10  2014 mnt[/FONT]
[FONT=arial]drwxr-xr-x     3 root root   4096 août  27 19:22 opt[/FONT]
[FONT=arial]drwx------     2 root root   4096 août   5 05:23 root[/FONT]
[FONT=arial]drwxr-xr-x    12 root root   4096 août   5 05:22 run[/FONT]
[FONT=arial]drwxr-xr-x    13 root root   4096 août   5 05:25 var[/FONT]
[FONT=arial]lrwxrwxrwx     1 root root     30 août  27 18:35 vmlinuz -> boot/vmlinuz-3.19.0-26-generic[/FONT]
[FONT=arial]lrwxrwxrwx     1 root root     30 août  27 18:09 vmlinuz.old -> boot/vmlinuz-3.19.0-25-generic[/FONT]

```

In order to help me to be able to restore my /home contents, here is the results of Analyse and Quick Search of testdisk command :

```
[FONT=arial]Analyse :

Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P Windows RE(store)        0  32 33  1372 250 30   22054912
 2 * HPFS - NTFS           1372 250 31  1385 186 17     204800 [System Reserved]
 3 P HPFS - NTFS           1385 186 18 20491 254 63  306942220
 4 E extended             20492  28 17 38913  70  5  295936000
 5 L Linux Swap           38409 248 48 38913  70  5    8085504
   X extended             20492  28 18 38409 248 47  287850495
 6 L Linux                20492  60 49 38409 248 47  287848448

*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted

[/FONT]
[FONT=arial]Quick Search :[/FONT]

[FONT=arial]Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63
     Partition               Start        End    Size in sectors
   HPFS - NTFS              0  32 33  1372 250 30   22054912 [Recovery]
   HPFS - NTFS           1372 250 31  1385 186 17     204800 [System Reserved]
   HPFS - NTFS           1385 186 18 20492  28 16  306944000
   Linux                20492  60 49 28914 120  6  135303168
   Linux                29987 189 27 38409 248 47  135303168
>  Linux Swap           38409 248 48 38913  70  5    8085504[/FONT]

```

1) Any idea how to restore my /home contents ?

2) Any idea how to install a new ubuntu system + dual boot with my Win7 partition which seems OK

Thanks in advance for your help.

Gigi

---

### Post by yancek on 2015-09-07
Your boot repair output does show grub code in the master boot record.  It is pointing to sda6 where it shows Ubuntu is installed.  Usually with boot repair, one will see several boot files.  On sda6, nothing shows.  Nor is there a grub.cfg file for that partition so it won't boot.  Did you have a separate home partition?  If not, it isn't showing.  If you had a lot of important data there, you might try using testdisk to recover it.

Losing power during a partition change is no doubt what caused all these problems.  Check the link below if you want to reinstall as it is a very detailed tutorial on installing Ubuntu and dual booting and also has a lot of other useful related info with some good links.  Installing windows 7 first will make things a lot easier.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by gperrot on 2015-09-07
Thanks a lot for your reply. No, I did not have a separate home partition. How can use testdisk to recover it ? 
Furthermore, is it possible to recreate a dual boot using my existing sda3 Win7 partition which is supposed to be unhurt ?

Thanks in advance for your help.

Gigi

> **yancek said:**
> Your boot repair output does show grub code in the master boot record.  It is pointing to sda6 where it shows Ubuntu is installed.  Usually with boot repair, one will see several boot files.  On sda6, nothing shows.  Nor is there a grub.cfg file for that partition so it won't boot.  Did you have a separate home partition?  If not, it isn't showing.  If you had a lot of important data there, you might try using testdisk to recover it.

Losing power during a partition change is no doubt what caused all these problems.  Check the link below if you want to reinstall as it is a very detailed tutorial on installing Ubuntu and dual booting and also has a lot of other useful related info with some good links.  Installing windows 7 first will make things a lot easier.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by gperrot on 2015-09-08
Any ideas how to solve my 2 points above ?

Thanks in advance for help.

Gigi

---

### Post by yancek on 2015-09-08
You can download testdisk from the site below.   If you scroll down the page, you will find a Step by Step tutorial link on how to use it.

 [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

You need a windows install disk to put its code in the mbr to boot it.  If you want to boot Ubuntu, you will have to reinstall Grub as you don't have the necessary Grub files according to your boot repair output.  The official Ubuntu Grub page, probably start at section 2.2 to reinstall Grub "Fixing a broken system".

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

