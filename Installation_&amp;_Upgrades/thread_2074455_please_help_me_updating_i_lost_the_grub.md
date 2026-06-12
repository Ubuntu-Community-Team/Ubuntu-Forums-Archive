---
title: "please help me: updating i lost the grub"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by ubunlilluz on 2012-10-21
Hi,
unfortunately today while i waqs updating to 12.10 from 12.04 the system game a message that told it could not write the grub on /dev/hda0. Restarting after finishing updating the system stops after the message operting system loading and the the prompt appears. Please help me what can i do for solving the problem (and without formatting and reinstalling)?
Please note that the grub was on a raid0 of two hd.
Thanks

---

### Post by darkod on 2012-10-21
You need to add grub2 to the MBR of the raid array. Is it a fakeraid (bios raid)?

Boot with the ubuntu cd in live mode, open terminal, and run this to activate the array (if it's not already active):
sudo dmraid -ay

After that post the output of this:
sudo parted -l (small L)

---

### Post by ubunlilluz on 2012-10-21
it's a bios array

```
ubuntu @ ubuntu: ~ $ sudo parted-l
Error: cannot have partition outside the disk.

Error:/dev/sdb: unrecognized disk label

Model: (scsi)
/Dev/sdc drive: 4041MB
Sector size (logical/physical): 512B/512B
Partition table: msdos

Number Start End Type filesystem Flags Size
1 32, 3 KB primary boot 4039MB 4039MB


Model: WDC WD2000BB-98G ATA (scsi)
/Dev/sdd disk: 200 GB
Sector size (logical/physical): 512B/512B
Partition table: msdos

Number Start End Type filesystem Flags Size
1 32, 3 KB 200 GB 200 GB primary ext4


Model: Linux Device-mapper (linear) (dm)
/Dev/mapper/isw_beefbehdgi_Domusraid2 drive: 4302MB
Sector size (logical/physical): 512B/512B
Partition table: loop

Number Start End filesystem Flags Size
1 0 4302MB 4302MB 00B, linux-swap (v1)


Model: Linux Device-mapper (linear) (dm)
/Dev/mapper/isw_beefbehdgi_Domusraid3 drive: 623GB
Sector size (logical/physical): 512B/512B
Partition table: loop

Number Start End filesystem Flags Size
1 0 623GB 623GB 00B, ext4


Model: Linux Device-mapper (linear) (dm)
/Dev/mapper/isw_beefbehdgi_Domusraid1 disk: 13, 1 GB
Sector size (logical/physical): 512B/512B
Partition table: loop

Number Start End filesystem Flags Size
1 0, 13 13 1, 00B, 1 GB ext4


Model: Linux Device-mapper (striped) (dm)
/Dev/mapper/isw_beefbehdgi_Domusraid disk: 640 GB
Sector size (logical/physical): 512B/512B
Partition table: msdos

Number Start End Type filesystem Flags Size
1 32, 13 3 KB, 1 GB, 1 GB 13 primary ext4 start
13, 17 2 1 GB, 4 GB 4302MB primary linux-swap (v1)
17, 3 4 GB 640 GB 623GB primary ext4


Warning: unable to open read-write/dev/sr0 (read-only File system
read). /dev/sr0 has been opened read-only.
Error:/dev/sr0: unrecognized disk label
```

---

### Post by darkod on 2012-10-22
From the partition sizes, I assume partition #1 is your root. You probably know that. If it's #3, just change the 1 into 3 in the mount command because you need to mount the root partition.

Installing grub2 to the MBR of the array from live mode would be (you need to use live cd of the same version, which means 12.10):
```
sudo dmraid -ay (just in case)
sudo mount /Dev/mapper/isw_beefbehdgi_Domusraid1 /mnt
sudo grub-install --root-directory=/mnt /Dev/mapper/isw_beefbehdgi_Domusraid
```

The mount command has the number 1 at the end of the raid device name because you need to mount the root partition. The grub-install command doesn't have any number in the name of the raid device since you need to install grub2 to the MBR of the array, not on any partition.

Try if that can help.

---

### Post by ubunlilluz on 2012-10-22
> **darkod said:**
> From the partition sizes, I assume partition #1 is your root. You probably know that. If it's #3, just change the 1 into 3 in the mount command because you need to mount the root partition.

Installing grub2 to the MBR of the array from live mode would be (you need to use live cd of the same version, which means 12.10):
```
sudo dmraid -ay (just in case)
sudo mount /Dev/mapper/isw_beefbehdgi_Domusraid1 /mnt
sudo grub-install --root-directory=/mnt /Dev/mapper/isw_beefbehdgi_Domusraid
```

The mount command has the number 1 at the end of the raid device name because you need to mount the root partition. The grub-install command doesn't have any number in the name of the raid device since you need to install grub2 to the MBR of the array, not on any partition.

Try if that can help.

thanks i'll try it this evening after work

---

### Post by ubunlilluz on 2012-10-22
> **darkod said:**
> From the partition sizes, I assume partition #1 is your root. You probably know that. If it's #3, just change the 1 into 3 in the mount command because you need to mount the root partition.

Installing grub2 to the MBR of the array from live mode would be (you need to use live cd of the same version, which means 12.10):
```
sudo dmraid -ay (just in case)
sudo mount /Dev/mapper/isw_beefbehdgi_Domusraid1 /mnt
sudo grub-install --root-directory=/mnt /Dev/mapper/isw_beefbehdgi_Domusraid
```

The mount command has the number 1 at the end of the raid device name because you need to mount the root partition. The grub-install command doesn't have any number in the name of the raid device since you need to install grub2 to the MBR of the array, not on any partition.

Try if that can help.

unfortunately it doesn't work, i've this a problem

```
ubuntu@ubuntu:~$ sudo mount /dev/mapper/isw_beefbehdgi_Domusraid1 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/mapper/isw_beefbehdgi_Domusraid1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by darkod on 2012-10-22
That might not be the root partition or it might be corrupted.

You must remember how you installed ubuntu because this doesn't look like a default install. Is #1 the root partition or #3?

---

### Post by ubunlilluz on 2012-10-22
> **darkod said:**
> That might not be the root partition or it might be corrupted.

You must remember how you installed ubuntu because this doesn't look like a default install. Is #1 the root partition or #3?

 yes i've created 3 partition

/root
/home
/swap

---

### Post by darkod on 2012-10-22
Hmm, if that is the root partition, it doesn't look good.

Try running fsck on it (the partition shouldn't be mounted):
sudo fsck /dev/mapper/......Domusraid1

---

### Post by ubunlilluz on 2012-10-22
> **darkod said:**
> Hmm, if that is the root partition, it doesn't look good.

Try running fsck on it (the partition shouldn't be mounted):
sudo fsck /dev/mapper/......Domusraid1

i got:

```
ubuntu@ubuntu:~/Musica$ sudo fsck /dev/mapper/isw_beefbehdgi_Domusraid1 
fsck from util-linux 2.20.1
e2fsck 1.42.5 (29-Jul-2012)
Superblocco has an invalid journal (inode 8).
Azzera<s>? 

```

---

### Post by darkod on 2012-10-22
Well, I don't know what's best to do. But if it's asking you whether to repair it or not, I guess it's better to select yes so it can try and repair it.

After that the previous commands to mount it and reinstall grub2 should work. It's up to you.

---

### Post by ubunlilluz on 2012-10-22
> **darkod said:**
> Well, I don't know what's best to do. But if it's asking you whether to repair it or not, I guess it's better to select yes so it can try and repair it.

After that the previous commands to mount it and reinstall grub2 should work. It's up to you.


seen that i've created 3 partitions for safety reason i've tried to reinstall ubuntu 12.10 formatting only the root but at the time to install the grub still in continue to tell me that it cannot write it. I've tried to chose all location possible but everytime it fails. When i quit the operation of installing cuz i couldn't continue it says that there was a crash on installing provedure so it tried to send the notification of it to ubuntu servedrs. In my opinion there is a bug in ubuntu for system with raid 0. Now i'll try to reinstall the 12.04 and i'll see what happen.

---

### Post by darkod on 2012-10-22
Are you using the alternate install cd? For raid you need to use the alternate installer, the standard desktop live cd does exactly that, it fails to install the bootloader.

---

### Post by ubunlilluz on 2012-10-22
> **darkod said:**
> Are you using the alternate install cd? For raid you need to use the alternate installer, the standard desktop live cd does exactly that, it fails to install the bootloader.

i didn't know that, but i tried to:

reinstall 12.04 and it failes still at the time of grub loadind and i reboot the system
then i tried to
reinstall 12.10 and it failes still at the time of grub loadind and this time i decided to chose to continue with installation without installing the grub

then after finishing installing procedure i rebooted waiting faithless for error message but instead it started and asked me foe password. Crazy i don't understand but i'm happy and tired. All configurations, emails ect are ok. Thats a mystery

The only problem is that the fans of graphic card doesn't slow and it makes noises

---

