---
title: "Kernel update, unable to boot into any version"
date: 2024-08-08
forum: Installation &amp; Upgrades
---

### Post by janderson9er on 2024-08-08
Hi, I am stuck with a desktop that I am unable to boot. I upgraded from 22.04 (I believe) to latest version of Ubuntu (I believe at the time it was 24.04), and I'm stuck with none of the kernel versions able to boot into regular mode or recovery mode.

I [ran into this issue before]("https://ubuntuforums.org/showthread.php?t=2483165"), and I'm just trying to decrypt my drive (something like [COLOR=#000000]cryptsetup luksOpen /dev/sda5 sda5_crypt)[/COLOR] so I can try to run initramfs commands to get back to a good state. 

I have the output from [Boot Repair]("https://pastebin.ubuntu.com/p/3NWZGRwsy2/"), which looks very similar to the last one too. All of the sda* drives I expect to see are there.

The problem I'm running into is I don't see the drives I expected at "/dev/sda", so I'm not sure how to decrypt and mount the drive. I have been able to use [this playbook to decrypt the drive]("https://ubuntuforums.org/showthread.php?t=2483165&page=3&p=14132414#post14132414") and make a similar repair last time, there shouldn't have been any major changes since I posted the last thread. Indeed, the contents of most of the commands are identical as the previous thread.

```

DEV="/dev/sda"
root@lubuntu:/# export DM="${DEV##*/}"
root@lubuntu:/# export DEVP="${DEV}$( if [[ "$DEV" =~ "nvme" ]]; then echo "p"; fi )"
root@lubuntu:/# export DM="${DM}$( if [[ "$DM" =~ "nvme" ]]; then echo "p"; fi )"
root@lubuntu:/# sgdisk --print $DEV


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************


Disk /dev/sda: 1000215216 sectors, 476.9 GiB
Model: INTEL SSDSC2KW51
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): 552FB207-68E3-43C7-8EE4-5D44971AFB27
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 1000215182
Partitions will be aligned on 2048-sector boundaries
Total free space is 4717 sectors (2.3 MiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1499135   731.0 MiB   8300  Linux filesystem
   5         1501184      1000214527   476.2 GiB   8300  Linux filesystem

```

and 

```

lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0 786.3M  1 loop /rofs
sda      8:0    0   477G  0 disk 
&#9500;&#9472;sda1   8:1    0   731M  0 part 
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0 476.2G  0 part 
sdb      8:16   0   3.7T  0 disk 
&#9492;&#9472;sdb1   8:17   0   3.7T  0 part 
sdc      8:32   0   477G  0 disk 
sdd      8:48   0   3.7T  0 disk 
&#9492;&#9472;sdd1   8:49   0   3.7T  0 part 
sde      8:64   1 114.6G  0 disk /cdrom
&#9500;&#9472;sde1   8:65   1   880M  0 part 
&#9492;&#9472;sde2   8:66   1   2.4M  0 part 
zram0  252:0    0   3.9G  0 disk [SWAP]
zram1  252:1    0   3.9G  0 disk [SWAP]
zram2  252:2    0   3.9G  0 disk [SWAP]
zram3  252:3    0   3.9G  0 disk [SWAP]
zram4  252:4    0   3.9G  0 disk [SWAP]
zram5  252:5    0   3.9G  0 disk [SWAP]
zram6  252:6    0   3.9G  0 disk [SWAP]
zram7  252:7    0   3.9G  0 disk [SWAP]

```

in particular.

Am I missing something? Can anyone point me in the right direction as to where they might be located, why they are missing, or a way I can decrypt the drives and [continue to mount as I did before]("https://ubuntuforums.org/showthread.php?t=2483165&page=3&p=14132444#post14132444") with [COLOR=#000000]cryptsetup luksOpen /dev/sda5 sda5_crypt[/COLOR]?

---

### Post by janderson9er on 2024-08-08
I tried rebooting into the USB Boot Repair disk again, and now I'm seeing different output from some of the commands, but the[ pastebin output]("https://pastebin.ubuntu.com/p/mqky8hq343/") is the same.

Now I'm seeing more under sdb, for some reason? 

```

lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0 786.3M  1 loop /rofs
sda      8:0    1 114.6G  0 disk /cdrom
&#9500;&#9472;sda1   8:1    1   880M  0 part 
&#9492;&#9472;sda2   8:2    1   2.4M  0 part 
sdb      8:16   0   477G  0 disk 
&#9500;&#9472;sdb1   8:17   0   731M  0 part /mnt/boot-sav/sdb1
&#9500;&#9472;sdb2   8:18   0     1K  0 part 
&#9492;&#9472;sdb5   8:21   0 476.2G  0 part 
sdc      8:32   0   3.7T  0 disk 
&#9492;&#9472;sdc1   8:33   0   3.7T  0 part /mnt/boot-sav/sdc1
sdd      8:48   0   477G  0 disk 
sde      8:64   0   3.7T  0 disk 
&#9492;&#9472;sde1   8:65   0   3.7T  0 part /mnt/boot-sav/sde1
zram0  252:0    0   3.9G  0 disk [SWAP]
zram1  252:1    0   3.9G  0 disk [SWAP]
zram2  252:2    0   3.9G  0 disk [SWAP]
zram3  252:3    0   3.9G  0 disk [SWAP]
zram4  252:4    0   3.9G  0 disk [SWAP]
zram5  252:5    0   3.9G  0 disk [SWAP]
zram6  252:6    0   3.9G  0 disk [SWAP]
zram7  252:7    0   3.9G  0 disk [SWAP]

```

---

### Post by oldfred on 2024-08-08
You show Bionic 18.04 as live installer running Boot-Repair? But report does not actually show installed version as you did not mount the encrypted partition before running report,
That 18.04 expired in 2023 unless you have extended support.

You also show an UEFI system but old BIOS install.
And some drives are old MBR, but others newer gpt.

---

### Post by janderson9er on 2024-08-08
Thanks for the reply!

> [COLOR=#000000]You show Bionic 18.04 as live installer running Boot-Repair? But report does not actually show installed version as you did not mount the encrypted partition before running report,[/COLOR]
[COLOR=#000000]That 18.04 expired in 2023 unless you have extended support.[/COLOR]

Odd, I thought it automatically updated. I'm using bootable USB Boot Repair disk, and allowed it to automatically update itself when it asked. Do you think that's related? I can wipe that USB drive and try an updated version.

> 
[COLOR=#000000]You also show an UEFI system but old BIOS install.[/COLOR]
[COLOR=#000000]And some drives are old MBR, but others newer gpt.
[/COLOR]

At risk of sounding dumb, do you mean there is a mismatch between the way some of the way my disks are configured and the way I am trying to boot? I don't think I changed anything related to disks, but it's entirely possible that issue existed before I tried to upgrade to latest LTS.

Where do I go from here? If I can get access to my encrypted drive, I would be happy if the end result is copying files I need off and nuking the drive to start fresh. Thank you!

---

### Post by oldfred on 2024-08-09
You can have both MBR & gpt drives.
With MBR you normally boot with BIOS and with gpt with UEFI. Windows only allows that.
But Ubuntu lets you use either boot mode with either partitioning, sometimes then causing conflicts with Windows and its defaults.
Or you can install Ubuntu in UEFI mode on a Windows BIOS/MBR drive and have major issues.

Issue often is with UEFI/BIOS updates. That often resets many settings to defaults.
Then if boot mode reset, you have boot issues.
With Windows you may not even see UEFI/BIOS update as it has become just part of Windows updates.
With Linux there now is fwupdate which for some newer systems can update UEFI.
Newer systems since about 2020 are UEFI only. My Dell calls it BIOS, but when in "BIOS" it says it only supports UEFI boot.

Or if UEFI updated, best to check settings.
On Dell I did not make any UEFI settings changes, but older Gigabyte motherboard had so many settings to change I had to keep a list.

---

### Post by janderson9er on 2024-08-10
I appreviate the explanation! I don't think my *current* issues are related to this, unfortunately. I was able to boot to version 24.04 after my upgrade, and did not make any changes to BIOS or anything related to disks. I'm also not dual-booting or running Windows.

The issue I am still seeing is related to the kernel panic when I boot - " not syncing : No working init found". 

The last time this happened was documented in the previous thread, and I'm just trying to figure out how to decrypt my drive so I can use boot repair to mount it and run my [playbook]("https://ubuntuforums.org/showthread.php?t=2483165&page=3&p=14132414#post14132414") from last time.

Does that make sense? I appreciate your replies!

---

### Post by oldfred on 2024-08-10
I have never used encrypted install.
Saved a link or two.
[https://unix.stackexchange.com/questions/677381/lost-boot-option-debian-after-switching-between-uefi-and-legacy](https://unix.stackexchange.com/questions/677381/lost-boot-option-debian-after-switching-between-uefi-and-legacy)
Mount LVM - duckhook
[https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372](https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372)
[https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621](https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621)
F

---

