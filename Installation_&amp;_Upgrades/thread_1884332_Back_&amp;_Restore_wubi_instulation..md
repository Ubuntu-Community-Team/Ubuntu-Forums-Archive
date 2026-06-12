---
title: "Back &amp; Restore wubi instulation."
date: 2011-11-21
forum: Installation &amp; Upgrades
---

### Post by kawaiipikachu on 2011-11-21
I want to know if I can backup & restore my Wubi ubuntu installation after I format & re-install Windows XP.

Is it possible to basically copy the unbuntu folder & boot.ini files to an external hard drive & copy them back once its done or is there more.
My current drive is formated as fat32 & ubuntu is set up with a 12GB install.

Any help would be appreciated.

---

### Post by bcbc on 2011-11-21
It's [possible]("http://askubuntu.com/questions/56726/can-i-copy-my-wubi-install-between-machines"), but why don't you take the opportunity to create a separate partition for Ubuntu and migrate the [wubi]("http://ubuntuforums.org/showthread.php?t=1519354") install to it?

---

### Post by kawaiipikachu on 2011-11-21
> **bcbc said:**
> It's [possible]("http://askubuntu.com/questions/56726/can-i-copy-my-wubi-install-between-machines"), but why don't you take the opportunity to create a separate partition for Ubuntu and migrate the [wubi]("http://ubuntuforums.org/showthread.php?t=1519354") install to it?

So as a quick question it terms of migrating is after I set up XP & my 2 partitions with the setup I can perform the operations from the first guide you link to restore backup then straight to he second guide for the migration?

---

### Post by bcbc on 2011-11-21
> **kawaiipikachu said:**
> So as a quick question it terms of migrating is after I set up XP & my 2 partitions with the setup I can perform the operations from the first guide you link to restore backup then straight to he second guide for the migration?

You can also migrate from the virtual disks themselves - so you can skip the part about reinstalling Wubi.

e.g. if you have 3 virtual disks (root.disk, usr.disk and home.disk) make sure they're in the same location, boot a live CD, create your partitions, then mount the external drive and migrate (change path - in blue):
```
sudo bash wubi-move-2.1.sh /dev/sda5 /dev/sda6 --root-disk=[COLOR="Blue"]/media/external/ubuntu/disks/[/COLOR]root.disk
```

Note: the root.disk migration is only allowed if you have grub2 (which is true for all Wubi installs on 9.10 and later).

PS - the architecture (32-bit vs 64-bit) of the Ubuntu CD also has to match for the root.disk migration (e.g. if you're currently running 32-bit ubuntu you need a 32-bit Ubuntu CD)

---

### Post by kawaiipikachu on 2011-11-21
> **bcbc said:**
> You can also migrate from the virtual disks themselves - so you can skip the part about reinstalling Wubi.

e.g. if you have 3 virtual disks (root.disk, usr.disk and home.disk) make sure they're in the same location, _boot a live_ CD, create your partitions, then mount the external drive and migrate (change path - in blue):



TO help confirm what I'm doing I meant to get there Boot up then select "Try Ubuntu"?

---

### Post by bcbc on 2011-11-21
Yes - that's right: "Try Ubuntu"

---

### Post by kawaiipikachu on 2011-11-22
Thanks.

---

### Post by kawaiipikachu on 2011-11-24
I'm not getting it to work at all.
Using ubuntu 10.10 cd to do it which is the same as the wubi install backup.
here's what showed up in the terminal.

```
ubuntu@ubuntu:~$ sudo bash wubi-move-2.1.sh /dev/sda5 /dev/sda6 --root-disk=/media/Elements_of_Harmony/ubuntu/disks/root.disk
bash: wubi-move-2.1.sh: No such file or directory

```The hard drive does mount & show up & mount & I can access the files on it.

any ideas?

---

### Post by bcbc on 2011-11-24
> **kawaiipikachu said:**
> I'm not getting it to work at all.
Using ubuntu 10.10 cd to do it which is the same as the wubi install backup.
here's what showed up in the terminal.

```
ubuntu@ubuntu:~$ sudo bash wubi-move-2.1.sh /dev/sda5 /dev/sda6 --root-disk=/media/Elements_of_Harmony/ubuntu/disks/root.disk
bash: wubi-move-2.1.sh: No such file or directory

```The hard drive does mount & show up & mount & I can access the files on it.

any ideas?
The error is that it cannot find the script (wubi-move-2.1.sh). Try from the Downloads folder:
```
cd ~/Downloads
```

---

### Post by kawaiipikachu on 2011-11-24
Now it's saying this
```
wubi-move-2.1.sh: target_partition /dev/sda5 must be type 83 - Linux.

```

---

### Post by bcbc on 2011-11-24
The script wants you to migrate to a partition that is type '83 -Linux'. If you create an ext2/3/4 partition using e.g. gparted it will be set as 83. While you can technically put an ext4 filesystem on a partition of type 7 (ntfs) - and it will boot Ubuntu without any issues - it's not ideal...

So to avoid confusion and possibly some problem down the road, the script enforces this.

Just open gparted and replace the /dev/sda5 partition with the an ext4 one and then it will work. 

After that, you can check if it's correct by running 'sudo fdisk -l' it will look something like this:
```
   Device Boot      Start         End      Blocks   Id  System
...
/dev/sda5       751497216   771977215    10240000   **83**  Linux
/dev/sda6       782217216   792457215     5120000   82  Linux swap / Solaris

```

---

### Post by bcbc on 2011-11-24
You can also use something like 'sfdisk' to change it:
From 'man sfdisk':
>       -c or --id number [Id]
              If no Id argument given: print the partition Id of the indicated
              partition. If an Id argument is present: change the type (Id) of
              the indicated partition to the given value.  This option has the
              two very long forms --print-id and --change-id.  For example:
                  % sfdisk --print-id /dev/hdb 5
                  6
                  % sfdisk --change-id /dev/hdb 5 83
                  OK
              first  reports  that  /dev/hdb5  has Id 6, and then changes that
              into 83.


So you would run:
```
sudo umount /dev/sda5
sudo sfdisk --change-id /dev/sda 5 83
```

But my personal recommendation is to use GParted. It's user friendly and safer.

Also: make sure that you have the correct partition (Gparted will tell you if there is any data on it - if there is, you likely have the wrong partition).

---

### Post by kawaiipikachu on 2011-11-25
That problem is appeared to be solved & now I got another problem.
The other problem is that theres no /dev/sda6 for the swap.
does the swap really need the sda6 partition or is there a way to have it share sda5.
I also included a screenshot of GParted . to help out.

---

### Post by bcbc on 2011-11-25
You don't need a swap partition. You can use a swap file instead. Or nothing - if you have enough RAM, then swap may not be required.

A swap partition is only required if you want to be able to hibernate, in which case it should be > the size of RAM. Otherwise you can just use a swap file.

For more info see: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by kawaiipikachu on 2011-11-26
```
ubuntu@ubuntu:~$ sudo bash wubi-move-2.1.sh /dev/sda5 [color=blue]/dev/sda6[/color] --root-disk=/media/Elements_of_Harmony/ubuntu/disks/root.disk
```
[quote=bcbc]A swap partition is only required if you want to be able to hibernate, in which case it should be > the size of RAM. Otherwise you can just use a swap file.[/quote]
1.)Can I iqnore the code in blue & is so what effect would it have in regards of the swap file.

2.)With the swap.disk file is it possible to to migrate that file into sda5 & how?

---

### Post by bcbc on 2011-11-26
> **kawaiipikachu said:**
> ```
ubuntu@ubuntu:~$ sudo bash wubi-move-2.1.sh /dev/sda5 [color=blue]/dev/sda6[/color] --root-disk=/media/Elements_of_Harmony/ubuntu/disks/root.disk
```

1.)Can I iqnore the code in blue & is so what effect would it have in regards of the swap file.

2.)With the swap.disk file is it possible to to migrate that file into sda5 & how?
Yes, just run this:
```
ubuntu@ubuntu:~$ sudo bash wubi-move-2.1.sh /dev/sda5 --root-disk=/media/Elements_of_Harmony/ubuntu/disks/root.disk
```

That means your migrated install won't have any swap. You can't migrate the swap file, but you can just create one when you boot up the new install. That swap faq I linked to has instructions on creating a swap file and adding it to /etc/fstab

---

