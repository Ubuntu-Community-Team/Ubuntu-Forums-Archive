---
title: "Add'l drive created by Ubuntu during installation"
date: 2024-05-23
forum: Installation &amp; Upgrades
---

### Post by zrzhu11 on 2024-05-23
I just installed Ubuntu 24.04. I allocated about 45 GB for the system. For some reason, I also see a 2.6GB drive created during the installation. Do I need it? 

Do I need to create swap drive or anything like that? Thanks.

---

### Post by yancek on 2024-05-23
I can't read the print on your image very weel but it looks like partition 8 is your Ubuntu system.  I'm not sure what the partition 7 might be.  Did you do an LVM install and use a separate /boot partition?  Does it boot?  You don't need a swap partition as recent Ubuntu releases have been using a swap file.  You can see this in the output of the command below from a terminal:

>  ls /

---

### Post by zrzhu11 on 2024-05-23
> **yancek said:**
> I can't read the print on your image very weel but it looks like partition 8 is your Ubuntu system.  I'm not sure what the partition 7 might be.  Did you do an LVM install and use a separate /boot partition?  Does it boot?  You don't need a swap partition as recent Ubuntu releases have been using a swap file.  You can see this in the output of the command below from a terminal:

Can you check this image?
 
[[IMG]https://i.ibb.co/NrHXDXG/Screenshot-from-2024-05-23-16-59-23.png[/IMG]]("https://ibb.co/XDv909G")

I installed it using the ISO file. I can boot to Ubuntu.

Below is the result after I ran the code, ls /. 

```
bin                boot   dev  home  lib64              lost+found  mnt  proc  run   sbin.usr-is-merged  srv       sys  usrbin.usr-is-merged  cdrom  etc  lib   lib.usr-is-merged  media       opt  root  sbin  snap                swap.img  tmp  var



```

---

### Post by QIII on 2024-05-23
zrzhu11,

Please do not post cryptic URLs and ask others to click them randomly.  Nobody here knows what might be lurking behind them.

It seems clear that you did not use an official image sanctioned by Canonical for Ubuntu or any of the flavors.  As such, it would be very difficult to determine what might have gone wrong -- or whether you have installed a nefariously altered image.

---

### Post by zrzhu11 on 2024-05-24
> **QIII said:**
> zrzhu11,

Please do not post cryptic URLs and ask others to click them randomly.  Nobody here knows what might be lurking behind them.

It seems clear that you did not use an official image sanctioned by Canonical for Ubuntu or any of the flavors.  As such, it would be very difficult to determine what might have gone wrong -- or whether you have installed a nefariously altered image.

Thanks. I downloaded the ISO file from Ubuntu site and installed it using a USB. I didn't make any changes to the file.

I updated my post above to insert the img.

---

### Post by currentshaft on 2024-05-24
mount
lsblk
df -h
sudo fdisk -l

All are commands you can use to examine active partitions and what they're used for.

---

### Post by zrzhu11 on 2024-05-24
> **currentshaft said:**
> mount
lsblk
df -h
sudo fdisk -l

All are commands you can use to examine active partitions and what they're used for.

Thanks. I guess my question is if Ubuntu needs any other drives besides the system drive. In my case, sda8 is the system drive. sda7 was created when I installed ubuntu 24.04. If I don't need it for ubuntu, i'll combine it with sda6 to use for both ubuntu and windows system. 

```
evice         Start       End   Sectors   Size Type/dev/sda1       2048   1085439   1083392   529M Windows recovery environment
/dev/sda2    1085440   1290239    204800   100M EFI System
/dev/sda3    1290240   1323007     32768    16M Microsoft reserved
/dev/sda4    1323008 100986879  99663872  47.5G Microsoft basic data
/dev/sda5  100986880 102399999   1413120   690M Windows recovery environment
/dev/sda6  102400000 406255615 303855616 144.9G Microsoft basic data
/dev/sda7  406255616 411365375   5109760   2.4G Linux filesystem
/dev/sda8  411365376 500115455  88750080  42.3G Linux filesystem



```

---

### Post by TheFu on 2024-05-24
1 command is helpful, but not the complete picture.   currentshaft  provided a number of commands to run. Please do and 
a) show the exact command used, 
b) along with the output.  
c) Thanks for using code-tags. Very helpful. Keep it up.

I'd like to see these commands myself:
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```
and
```
lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
```

Those commands prevent the useless cruft from being in the output, but show the important stuff ... with the fdisk output already provided, the complete picture will be known.

Lastly, you aren't using LVM.

---

### Post by yancek on 2024-05-24
I don't know what that partition is or why it was created but in addition to the suggestions above, before deleting it and combining it with sda6, it would be a good idea to mount that partition and see what, if anything is on it.

---

### Post by zrzhu11 on 2024-05-24
> **TheFu said:**
> 1 command is helpful, but not the complete picture.   currentshaft  provided a number of commands to run. Please do and 
a) show the exact command used, 
b) along with the output.  
c) Thanks for using code-tags. Very helpful. Keep it up.

I'd like to see these commands myself:
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```
and
```
lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
```

Those commands prevent the useless cruft from being in the output, but show the important stuff ... with the fdisk output already provided, the complete picture will be known.

Lastly, you aren't using LVM.

Thanks. Result for df -hT -x squashfs -x tmpfs -x devtmpfs

```
Filesystem     Type      Size  Used Avail Use% Mounted on/dev/sda8      ext4       42G   12G   28G  29% /
efivarfs       efivarfs  108K   70K   33K  69% /sys/firmware/efi/efivars
/dev/sda2      vfat       96M   33M   64M  35% /boot/efi
```

Result for lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint

```
NAME   TYPE FSTYPE   SIZE FSAVAIL FSUSE% LABEL    MOUNTPOINsda    disk        238.5G                         
&#9500;&#9472;sda1 part ntfs     529M                Recovery 
&#9500;&#9472;sda2 part vfat     100M   63.3M    34%          /boot/efi
&#9500;&#9472;sda3 part           16M                         
&#9500;&#9472;sda4 part ntfs    47.5G                         
&#9500;&#9472;sda5 part ntfs     690M                         
&#9500;&#9472;sda6 part ntfs   144.9G                         
&#9500;&#9472;sda7 part ext4     2.4G                         
&#9492;&#9472;sda8 part ext4    42.3G   27.9G    27%          /
sr0    rom          1024M                         



```

---

### Post by zrzhu11 on 2024-05-24
> **yancek said:**
> I don't know what that partition is or why it was created but in addition to the suggestions above, before deleting it and combining it with sda6, it would be a good idea to mount that partition and see what, if anything is on it.

Nothing in sda7. I have no idea either. if it's not needed, i rather not to keep a 2.6GB drive there.

---

### Post by TheFu on 2024-05-24
sda7 has an ext4 file system. Mount it and see if there's anything inside it.  Doesn't seem to be part of the install. No clue how it was created, unless you attempted the install, twice, killing it very early in the first attempt.  That doesn't seem likely. Could be a bug.  I haven't see that.  2.6G is too small for swap, IMHO.  For any desktop, 4.1G is the "correct" size for swap, unless you hibernate.  A swap partition wouldn't be ext4, so it isn't for swap.

---

### Post by zrzhu11 on 2024-05-25
> **TheFu said:**
> sda7 has an ext4 file system. Mount it and see if there's anything inside it.  Doesn't seem to be part of the install. No clue how it was created, unless you attempted the install, twice, killing it very early in the first attempt.  That doesn't seem likely. Could be a bug.  I haven't see that.  2.6G is too small for swap, IMHO.  For any desktop, 4.1G is the "correct" size for swap, unless you hibernate.  A swap partition wouldn't be ext4, so it isn't for swap.

I used Gparted to create a 48 GB drive for installation. I don't know why it split the drive into 2, 45gb for system installation and 2gb.

---

### Post by TheFu on 2024-05-26
> **zrzhu11 said:**
> I used Gparted to create a 48 GB drive for installation. I don't know why it split the drive into 2, 45gb for system installation and 2gb.

I've never seen that, but I tend to setup more flexible partitioning than most people, so I don't know the "minimal" required partitions for every possible storage choice in every different installer.

The 24.04 desktop installers don't make me happy with their limited storage options. They removed the main volume manager capability that I depend on.  I spent far too much time trying to get it working in Lubuntu and Xubuntu before someone else pointed out that the feature I'd been using 15+ yrs had been removed AND the thought that support for MSFT's crypto-storage was more important than something which has been enterprise trusted since the 1990s. Clearly, I disagree, but I can appreciate that when new users all bring MSFT crypto-storage with them, it is easy to believe that could be more important.

---

### Post by zrzhu11 on 2024-05-26
Thanks for all your help, @TheFu. I'll combine the drives later and report back.

---

