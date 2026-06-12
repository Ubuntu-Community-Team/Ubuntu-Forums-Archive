---
title: "Window 8.1, Ubuntu 14.04, Debian, GPT UEFI multi-boot with LVM and encryption"
date: 2014-04-20
forum: Installation &amp; Upgrades
---

### Post by Dáire Fagan on 2014-04-20
Hi

I am installing Ubuntu 14.04 onto my laptop&#8217;s hard disk where Windows 8.1 is already installed in GPT UEFI mode. The Windows install created 4 partitions and uses 150GiB leaving 315GiB on the drive unallocated.

I disabled fast startup in Windows 8.1 power options and booted Ubuntu 14.04 Live using a USB key that was created to only boot in UEFI mode, and I also selected &#8216;UEFI: Verbatim USB key&#8217; when booting.

Using GParted I created a 500MiB Ext4 sda5 partition at the start of the unallocated space that I later selected as /boot in the Ubuntu installer. I understand this is required for for LVM and also encryption.

I created sda6 Ext4 from the remaining space as it was the only way the first of the following commands would input properly:

```
ubuntu@ubuntu:~$ sudo pvcreate /dev/sda6
 Physical volume "/dev/sda6" successfully created
ubuntu@ubuntu:~$ sudo vgcreate system /dev/sda6
 Volume group "system" successfully created
ubuntu@ubuntu:~$ sudo lvcreate -L 8.5G -n swap system
 Logical volume "swap" created
ubuntu@ubuntu:~$ sudo lvcreate -L 20G -n ubuntu-root system
 Logical volume "ubuntu-root" created
ubuntu@ubuntu:~$ sudo lvcreate -L 50G -n ubuntu-home system
 Logical volume "ubuntu-home" created
ubuntu@ubuntu:~$ sudo lvcreate -L 20G -n debian-root system
 Logical volume "debian-root" created
ubuntu@ubuntu:~$ sudo lvcreate -L 20G -n debian-home system
 Logical volume "debian-home" created
ubuntu@ubuntu:~$ sudo lvcreate -L 10G -n kali system
 Logical volume "kali" created
ubuntu@ubuntu:~$ sudo vgdisplay | grep -i free
 Free  PE / Size       47681 / 186.25 GiB
ubuntu@ubuntu:~$ sudo lvcreate -L 100G -n shared system
 Logical volume "shared" created
ubuntu@ubuntu:~$ sudo mkfs.ext4 /dev/mapper/system-ubuntu--root
&#8230;
ubuntu@ubuntu:~$ sudo mkfs.ext4 /dev/mapper/system-ubuntu--home
&#8230;
ubuntu@ubuntu:~$ sudo mkfs.ext4 /dev/mapper/system-shared
...

```

I purposely omitted &#8216;sudo mkswap -f /dev/mapper/system-swap&#8217; as if I enter it with the other commands, when I try to encrypt using the Ubuntu installer later it will give an error due to the unencrypted swap.

After selecting &#8216;something else&#8217; from the Ubuntu installer I can see all of my logical volumes and sda partitions. I clicked on sda5 which the Ubuntu installer displays as 524MB and press change. From the dialogue window that appears I select format, Ext4, and /boot as the mount point. The installer warns me rezising may take a long time, even though I am not reszing, I press continue, and after about a mintue the timer cursor turns into a regular cursor.

I highlighted /dev/mapper/system-ubuntu--home and chose &#8216;physical volume for encryption&#8217;, entered a password, and checked on &#8216;overwrite empty disk space&#8217; before pressing OK. This brings up the timer for another minute and then returns the following warning (error?):

```

Device in use

No modifications can be made to the LVM VG system, LV ubuntu-home for the following reason:

In use as a physical volume for encrypted volume system-ubuntu--home_crypt.

```

I selected the new entry /dev/mapper/system-ubuntu--home_crypt and pressed change. From there I chose Ext4 and /home as the mount point.

I encrypted /dev/mapper/system-shared and received the same warning as above but I did not press &#8216;change&#8217; on it as I do not need to assign it a mount point and it is already Ext4.

Same for /dev/mapper/system-ubuntu--root, same warning afterwards, set to mount on /, formatted, and Ext4.

Same for /dev/mapper/system-swap only /dev/mapper/system-swap_crypt is set to swap area.

I left device for boot loader installation set to /dev/sda

1) Once installed and rebooted this loads GRUB 2 where I have an option to boot Ubuntu or Windows Boot Manager. Unfortunately I have to enter my crypt password 3 times on boot for each of the partitions, and then again to login. Is there no more efficient way to encrypt? I could have checked on 'Encrypt my home folder' before installing but should swap and / not also be encrypted?

2) I am also not able to save any files to the shared data partition I set up? I am asked for my password and I can access it fine but I can save any files or create any folders etc.

3) I had read I could turn Windows 8.1 fast boot back on once dual booting was set up but if I do so I can reboot into Windows 8.1 only once, on the next reboot it tells me the computer needs to be repaired and crashes, next reboot lets me back in - happens every second boot. This is only resolved by turning fast boot back off. Is there a way to have fast boot on?

---

### Post by oldfred on 2014-04-21
I do not use LVM nor encryption.
The default install of LVM with encryption is a full drive install or it will erase your Windows.

13.10 LVM install, but should be similar
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by Dáire Fagan on 2014-04-22
> **oldfred said:**
> I do not use LVM nor encryption.
The default install of LVM with encryption is a full drive install or it will erase your Windows.

13.10 LVM install, but should be similar
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

Thanks for the reply oldfred, but that website covers lvm and encrypton which I am already able to configure and boot, the problem is I have to enter my passphrase three times at boot for each partition, /, /home, and swap.


I read in an old thread, and it was suggested to me in #ubuntu’s IRC channel, that if I encrypt just the LVM’s physical volume as all of the logical volumes are contained within it I should only have to enter my passphrase once at boot.

What I have tried:

1) I created the partitions and set up LVM just as in my original post. In the installer I leave all the /dev/mapper entries alone, instead I highlight /dev/sda6, click change, select physical volume for encrypton, enter my new passphrase, check overwrite empty disk space, and click okay. The cursor turns into the timer for a few seconds before the following error appears:

Configuration of encrypted volumes failed.

An error occurred while configuring encrypted volumes

The configuration has been aborted

Even so sda6 was still marked crypto so I assigned the boot partiion, and then / and home to the logical volumes and installed. Ubuntu boots but it first outputs the following:
```

error: diskfilter writes are not support

```
And after I log in nothing is encrypted.

2) GParted would not let me deactivate the lvm on sda6 so I rebooted, deactivated it, and deleted it. This time I just created the physical volume with the following command:


```
sudo pvcreate /dev/sda6 -ff


```
Next, in the installer I selected /dev/sda6 as a physical volume for encryption which created a new volume: /dev/mapper/sda6_crypt

When I try to create the volume group:

```
ubuntu@ubuntu:~$ sudo vgcreate system /dev/sda6

  No physical volume label read from /dev/sda6
  Can't open /dev/sda6 exclusively.  Mounted filesystem?
  Unable to add physical volume '/dev/sda6' to volume group 'system'.

ubuntu@ubuntu:~$ umount /dev/sda6
umount: /dev/sda6 is not mounted (according to mtab)

ubuntu@ubuntu:~$ umount /dev/mapper/sda6_crypt
umount: /dev/mapper/sda6_crypt is not mounted (according to mtab)


```
Unable to create the volume group I stop here.

3) I first try to delete the lvm partition from my last attempt but GParted gives an unspecified error while applying the operations. I rebooted and deleted the crypt-luks partition in GParted.

```
ubuntu@ubuntu:~$ sudo pvcreate /dev/sda6

  Device /dev/sda6 not found (or ignored by filtering).

```
Created sda6 Ext4 from GParted with the remaining space.
```

ubuntu@ubuntu:~$ sudo pvcreate /dev/sda6
  Physical volume "/dev/sda6" successfully created
ubuntu@ubuntu:~$ sudo vgcreate system /dev/sda6
  Volume group "system" successfully created

```
In the installer I select /dev/sda6 as a physical volume for encryption and it creates a new /dev/mapper/sda6_crypt. 

Unfortunately when I try to create any logical volume:

```
ubuntu@ubuntu:~$ sudo lvcreate -L 8.5G -n swap system

  Volume group "system" not found

```

The following is how I have encrypted the /root, /home, and swap partitions on a disk already containing Windows 8.1 and only require a single passphrase entry on boot:

Create 500 MiB ext4 sda5 partition that will later be assigned as /boot

```
ubuntu@ubuntu:~$ sudo dd if=/dev/urandom of=/dev/sda6
```

12 hours elapse.

```
dd: writing to ‘/dev/sda6’: No space left on device
660092929+0 records in
660092928+0 records out
337967579136 bytes (338 GB) copied, 39571.4 s, 8.5 MB/s
```

```
ubuntu@ubuntu:~$ modprobe dm-crypt
ubuntu@ubuntu:~$ modprobe aes-x86_64
ubuntu@ubuntu:~$ sudo modprobe sha256
```

When I do this over I will run crptysetup benchmark first to see which aes and sha works best for my system.

```
ubuntu@ubuntu:~$ sudo cryptsetup luksFormat /dev/sda6

WARNING!
========
This will overwrite data on /dev/sda6 irrevocably.

Are you sure? (Type uppercase yes): YES
Enter passphrase:
Verify passphrase:
ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/sda6 enc-pv
Enter passphrase for /dev/sda6:

ubuntu@ubuntu:~$ sudo pvcreate /dev/mapper/enc-pv
  Physical volume "/dev/mapper/enc-pv" successfully created
ubuntu@ubuntu:~$ sudo vgcreate vg /dev/mapper/enc-pv
  Volume group "vg" successfully created
ubuntu@ubuntu:~$ sudo lvcreate -L 8.5G -n swap vg
  Logical volume "swap" created
ubuntu@ubuntu:~$ sudo lvcreate -L 20G -n ubuntu-root vg
  Logical volume "ubuntu-root" created
ubuntu@ubuntu:~$ sudo lvcreate -L 50G -n ubuntu-home vg
  Logical volume "ubuntu-home" created
ubuntu@ubuntu:~$ sudo lvcreate -L 140G -n shared vg
  Logical volume "shared" created

ubuntu@ubuntu:~$ sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/vg/swap
  LV Name                swap
  VG Name                vg
  LV UUID                EMSdc1-yTSS-FF9W-5vcv-jEwF-OeF7-5oOoEI
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2014-04-23 12:57:17 +0000
  LV Status              available
  # open                 0
  LV Size                8.50 GiB
  Current LE             2176
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1

  --- Logical volume ---
  LV Path                /dev/vg/ubuntu-root
  LV Name                ubuntu-root
  VG Name                vg
  LV UUID                TCPIIE-fGv0-3tz8-XP3R-1c9Z-E18R-XTbcOd
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2014-04-23 12:58:41 +0000
  LV Status              available
  # open                 0
  LV Size                20.00 GiB
  Current LE             5120
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2

  --- Logical volume ---
  LV Path                /dev/vg/shared
  LV Name                shared
  VG Name                vg
  LV UUID                dPHDeT-52zj-7bAx-xjzP-p4yC-kXoo-aw7Eac
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2014-04-23 12:59:50 +0000
  LV Status              available
  # open                 0
  LV Size                140.00 GiB
  Current LE             35840
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:4

  --- Logical volume ---
  LV Path                /dev/vg/ubuntu-home
  LV Name                ubuntu-home
  VG Name                vg
  LV UUID                pWFs3D-MXrh-bMez-68r0-4yPc-zMTo-MGhNF1
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2014-04-23 13:06:11 +0000
  LV Status              available
  # open                 0
  LV Size                50.00 GiB
  Current LE             12800
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:3

ubuntu@ubuntu:~$ sudo vgdisplay | grep -i free
  Free  PE / Size       24641 / 96.25 GiB
```

```
ubuntu@ubuntu:~$ sudo mkfs.ext4 /dev/mapper/vg-shared

mke2fs 1.42.9 (4-Feb-2014)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
9175040 inodes, 36700160 blocks
1835008 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
1120 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
    4096000, 7962624, 11239424, 20480000, 23887872

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done     

```

There was similar output for:

```
ubuntu@ubuntu:~$ sudo mkfs.ext4 /dev/mapper/vg-ubuntu-root
ubuntu@ubuntu:~$ sudo mkfs.ext4 /dev/mapper/vg-ubuntu-home
```

I may have needed to add an extra hyphen, like vg-ubuntu--root

Next I opened the Ubuntu 14.04 installer and selected 'something else'. I assigned /boot to the 500 MiB partition on sda5 and then /root, /home, and swap to the logical /dev/mapper/vg volumes. 

After Ubuntu installs, before rebooting from the live USB I entered the following:

```
ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/sda6 enc-pv
Enter passphrase for /dev/sda6:
ubuntu@ubuntu:~$ sudo mount /dev/vg/ubuntu-root /mnt
ubuntu@ubuntu:~$ sudo chroot /mnt mount /proc
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo chroot /mnt mount /boot
ubuntu@ubuntu:~$ sudo echo "enc-pv UUID=`sudo blkid -s UUID -o value /dev/sda6` none luks" | sudo tee -a /mnt/etc/crypttab
enc-pv UUID=ad8b8a32-95ea-4add-abe6-326d151e30fa none luks
ubuntu@ubuntu:~$ sudo chroot /mnt update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.13.0-24-generic
ubuntu@ubuntu:~$ sudo umount /mnt/proc /mnt/dev /mnt/boot /mnt
```

On reboot Ubuntu boots asking for only one entry of the passphrase instead of three, one for each encrypted volume.

==================================================================

The only problem remaining now is that although the /dev/mapper/vg-shared volume appears like any other partitionin /media/dusf/, and although I can open it without having to enter the passphrase again, I cannot create files on it.

I have tried replacing the command 'sudo mount /dev/vg/ubuntu-root /mnt' with 'sudo mount /dev/vg/shared /mnt' but then when i go onto the next command 'sudo chroot /mnt mount /proc' it gives me the error 'chroot: failed to run command ‘mount’: No such file or directory'. 

Can anyone tell me how I should edit the following commands so that /dev/vg/-shared not only mounts at boot, but I can also write to it?

```
ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/sda6 enc-pv
Enter passphrase for /dev/sda6:
ubuntu@ubuntu:~$ sudo mount /dev/vg/ubuntu-root /mnt
ubuntu@ubuntu:~$ sudo chroot /mnt mount /proc
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo chroot /mnt mount /boot
ubuntu@ubuntu:~$ sudo echo "enc-pv UUID=`sudo blkid -s UUID -o value /dev/sda6` none luks" | sudo tee -a /mnt/etc/crypttab
enc-pv UUID=ad8b8a32-95ea-4add-abe6-326d151e30fa none luks
ubuntu@ubuntu:~$ sudo chroot /mnt update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.13.0-24-generic
ubuntu@ubuntu:~$ sudo umount /mnt/proc /mnt/dev /mnt/boot /mnt
```

---

### Post by oldfred on 2014-04-25
Is it just ownership and permissions like on any other partition once unencrypted?

       sudo chmod -R a+rwX,o-w /mnt/data

 sudo chown -R $USER:$USER /mnt/data
$USER is a variable with your name, you can just use your name.
You have to change the /mnt/data to your mount

-R is recursion, so not run on any system partition, just data partitions.

---

### Post by Dáire Fagan on 2014-06-05
Latest setup where I opted to put all the free space, short some I am keeping for different distro installs, into /home instead of a shared data partition. I only have to enter my crypt passphrase once at startup. I have to enter a key when I load Chrome, but I think this is normal? Please tell me if anything I did can be improved, or if you know where to begin install Truecrypt for the Windows 8.1 partition, I understand it will overwrite grub.

Using GParted I created a 500MiB primary ext4 partition sda5 that will later be set as /boot, and I used the remaining 314GB to create a primary ext4 sda6 partition.

ubuntu@ubuntu:~$ sudo dd if=/dev/urandom of=/dev/sda6

10 hours elapse.

ubuntu@ubuntu:~$ cryptsetup benchmark
# Tests are approximate using memory only (no storage IO).
PBKDF2-sha1       385505 iterations per second
PBKDF2-sha256     226768 iterations per second
PBKDF2-sha512     147271 iterations per second
PBKDF2-ripemd160  316217 iterations per second
PBKDF2-whirlpool  164250 iterations per second
#  Algorithm | Key |  Encryption |  Decryption
     aes-cbc   128b   463.0 MiB/s  19001.0 MiB/s
 serpent-cbc   128b    70.3 MiB/s   228.1 MiB/s
 twofish-cbc   128b   143.4 MiB/s   277.6 MiB/s
     aes-cbc   256b   345.9 MiB/s  1223.1 MiB/s
 serpent-cbc   256b    70.2 MiB/s   230.3 MiB/s
 twofish-cbc   256b   143.4 MiB/s   281.5 MiB/s
     aes-xts   256b  87814.2 MiB/s  265072.0 MiB/s
 serpent-xts   256b   252.5 MiB/s   250.2 MiB/s
 twofish-xts   256b   326.7 MiB/s   334.0 MiB/s
     aes-xts   512b  16467.0 MiB/s  19183.0 MiB/s
 serpent-xts   512b   252.2 MiB/s   247.0 MiB/s
 twofish-xts   512b   327.7 MiB/s   330.3 MiB/s
ubuntu@ubuntu:~$ cat /proc/sys/kernel/random/entropy_avail
1371
ubuntu@ubuntu:~$ sudo cryptsetup -v --cipher aes-xts-plain64 --key-size 512 --hash sha1 --use-urandom --verify-passphrase luksFormat /dev/sda6

WARNING!
========
This will overwrite data on /dev/sda6 irrevocably.

Are you sure? (Type uppercase yes): YES
Enter passphrase:
Verify passphrase:
Command successful.
ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/sda6 enc-pv
Enter passphrase for /dev/sda6:
ubuntu@ubuntu:~$ sudo pvcreate /dev/mapper/enc-pv
  Physical volume "/dev/mapper/enc-pv" successfully created
ubuntu@ubuntu:~$ sudo vgcreate vg /dev/mapper/enc-pv
  Volume group "vg" successfully created
ubuntu@ubuntu:~$ sudo lvcreate -L 8.5G -n swap vg
  Logical volume "swap" created
ubuntu@ubuntu:~$ sudo lvcreate -L 20G -n ubuntu-root vg
  Logical volume "ubuntu-root" created
ubuntu@ubuntu:~$ sudo vgdisplay | grep -i free
  Free  PE / Size       73281 / 286.25 GiB
ubuntu@ubuntu:~$ sudo lvcreate -L 200G -n ubuntu-home vg
  Logical volume "ubuntu-home" created
ubuntu@ubuntu:~$ sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/vg/swap
  LV Name                swap

  VG Name                vg
  LV UUID                Ac6UZZ-et4d-KWli-siK5-5J5M-x6L5-9dw9vq
  LV Write Access        read/write

  LV Creation host, time ubuntu, 2014-06-05 12:58:32 +0000

  LV Status              available
  # open                 0

  LV Size                8.50 GiB

  Current LE             2176

  Segments               1

  Allocation             inherit

  Read ahead sectors     auto

  - currently set to     256

  Block device           252:1

   

  --- Logical volume ---

  LV Path                /dev/vg/ubuntu-root

  LV Name                ubuntu-root

  VG Name                vg

  LV UUID                y67ZR3-nmPV-YZ65-ZS8x-O9C5-VF0j-DiCT4A
  LV Write Access        read/write

  LV Creation host, time ubuntu, 2014-06-05 12:58:42 +0000

  LV Status              available
  # open                 0
  LV Size                20.00 GiB
  Current LE             5120
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2
   
  --- Logical volume ---
  LV Path                /dev/vg/ubuntu-home
  LV Name                ubuntu-home
  VG Name                vg
  LV UUID                082pJo-oLhT-SGyM-VIKj-XGOs-2F1k-mPPLH3
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2014-06-05 13:04:33 +0000
  LV Status              available
  # open                 0
  LV Size                200.00 GiB
  Current LE             51200
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:3

ubuntu@ubuntu:~$ sudo mkfs.ext4 /dev/vg/ubuntu-root
mke2fs 1.42.9 (4-Feb-2014)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
1310720 inodes, 5242880 blocks
262144 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
160 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
    4096000

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done   

ubuntu@ubuntu:~$ sudo mkfs.ext4 /dev/vg/ubuntu-home
mke2fs 1.42.9 (4-Feb-2014)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
13107200 inodes, 52428800 blocks
2621440 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
1600 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
    4096000, 7962624, 11239424, 20480000, 23887872

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done     

Rebooted into live CD

ubuntu@ubuntu:~$ sudo cryptsetup luksOpen /dev/sda6 enc-pv
Enter passphrase for /dev/sda6:
ubuntu@ubuntu:~$ sudo mount /dev/vg/ubuntu-root /mnt
ubuntu@ubuntu:~$ sudo chroot /mnt mount /proc
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo chroot /mnt mount /boot
ubuntu@ubuntu:~$ sudo echo "enc-pv UUID=`sudo blkid -s UUID -o value /dev/sda6` none luks" | sudo tee -a /mnt/etc/crypttab enc-pv UUID=ad8b8a32-95ea-4add-abe6-326d151e30fa none luks
enc-pv UUID=b2dd47cc-5f6b-4141-8ebf-062f94c2c5a4 none luks
ubuntu@ubuntu:~$ sudo chroot /mnt update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.13.0-27-generic
ubuntu@ubuntu:~$ sudo umount /mnt/proc /mnt/dev /mnt/boot /mnt

I have password at login disabled so I only have to enter the cryptsetup passphrase. If this were the same as my Ubuntu password would there be a way to send the passphrase to Ubuntu to unlock my key? When I launch a browser etc I am prompted for my password to unlock the keys.

---

