---
title: "zfs focal &gt; jammy upgrade fail"
date: 2022-10-23
forum: Installation &amp; Upgrades
---

### Post by anystupidassname on 2022-10-23
Can you help me recover this failed jammy upgrade please?
I ran do-release-upgrade on a focal zfs on root (legacy bios, bpool, & rpool) and everything seemed to go fine until after reboot. Grub still showed 20.04 with old kernel and trying to boot it dumps to an emergency mode. The askubuntu should have all relevant details but I'm happy to provide any other necessary info or try any other suggestions. Thanks!

[https://askubuntu.com/questions/1435307/booting-to-emergency-mode-after-20-04-5-focal-to-22-04-jammy-upgrade](https://askubuntu.com/questions/1435307/booting-to-emergency-mode-after-20-04-5-focal-to-22-04-jammy-upgrade)

[https://www.reddit.com/r/Ubuntu/comments/y7k875/how_can_i_reinstall_grub_on_this_system/](https://www.reddit.com/r/Ubuntu/comments/y7k875/how_can_i_reinstall_grub_on_this_system/)

Perhaps related:
[https://ubuntuforums.org/printthread.php?t=2478208&pp=10&page=1](https://ubuntuforums.org/printthread.php?t=2478208&pp=10&page=1)

---

### Post by MAFoElffen on 2022-10-23
I am the contributor to Zannubuntu for ZFS and LUKS for the 'boot-info' and 'boot-repair' script... [Development of the [boot-info] and [boot-repair] Utilities]("https://ubuntuforums.org/showthread.php?t=2470405")

You want me to answer you "here" in this thread or "there" on AskUbuntu?

Before trying to do anything... I would recommend booting from 22.04 LiveCD USB and backup everything to an external USB storage drive... Which you should have done before doing a release upgrade. That way you have one more chance for a fall back point...

[I]ZFS snap shots are not a replacement for backups. 
[/I]
There are a few things that contributed to this over time that need to be corrected first. Or not. Your decision after I expand on this.

---

### Post by anystupidassname on 2022-10-23
Thanks for answering.
Askubuntu please. (unless you have another preference)
Data is backed up, thanks for the advice.

---

### Post by MAFoElffen on 2022-10-24
I think here, in this thread, would be better, as I have more freedom of how long a post can be for instructions.

First, the reason ZSys stopped taking snaphots a while back, is that if you checked your bpool in the /boot partition, you are probably going to find out that it is almost full, which is also probably a reason why your release upgrade failed (not enough space there)... When the bpool has less than 20% free space, then ZSys stops taking any new snapshots. I created a script for mine which deletes the old bpool snapshots, and leaves the 5 newest there.

This usually prompts an error saying that during any apt kinds of activity. You didn't notice that? No matters. Was in the past.

So the plan would be to boot from a Desktop LiveCD, mount the partitions in the installed system, activate the ZFS rpool and bpool of the installed system, delete some of the old bpool snap shots to free up some space... Before trying to roll back to your newest snap shot. If you try to revert too soon, I don't know if you would have enough space left in the bpool to do that.

Does that sound like a good plan?

---

### Post by MAFoElffen on 2022-10-24
Boot from an Ubuntu LiveCD and open up a graphical terminal and a browser. Navigate the browser back to this thread, so you can cut and paste commands and output between those.

From the terminal session:
```

sudo fdisk -l 2>&1 | sed '/\/dev\/loop/,+3 d' 2> /dev/null | uniq | grep 'Solaris'
lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL | grep -v '/snap/\|loop' | grep 'zfs_'
```
Please post the output of those two commands... The first will have output of Solaris boot and Solaris root. The second will ID the names of the ZFS rpool and bpool to be able to mount and activate them...

From that output, I'll post the next commands.

---

### Post by MAFoElffen on 2022-10-24
The next step is 
```

sudo -i
apt update
apt install -y zfs-initramfs
zpool list   # ensure the output says: "no datasets available"
zfs list  # ensure the output says: "no datasets available"
zpool import -N -R /mnt rpool

```
Adjust the name rpool above to either rpool or tmprpool, depending on the output from above...
```

zfs list

```
This output, under the heading of "mount", look for which rpool is mounted directly at /mnt... It should be something like
```

NAME                                                  USED  AVAIL     REFER  MOUNTPOINT[COLOR=#ff0000]
rpool/ROOT/ubuntu_##fs##[/COLOR]                             7.78G  9.15G     3.52G  /mnt 

```
You are going to use that output in the next command, for example
```

zfs mount rpool/ROOT/ubuntu_72fs0l

```
Then the rest of the mount like this
```

zfs mount -a
mount --rbind /dev  /mnt/dev
mount --rbind /proc /mnt/proc
mount --rbind /sys  /mnt/sys
chroot /mnt /bin/bash --login

```
You are now chrooted into the installed system and the ZFS filesystem, able to make live changes to it...

Tell me when you get that far...

Note: Do Not make changes to the installed system and then reboot until you first shutdown the ZFS filesystem and exit out cleanly (for much later, for when that time comes...):
```

zpool export -a
exit
umount /mnt
exit

```

---

### Post by MAFoElffen on 2022-10-24
Next you want to make room in your bpool... 

I wrote this script to automate that for me on mine:
```

#!/bin/bash
# MAFoElffen, <mafoelffen@ubuntu.com>, 2021.12.28, last modified: 2022.02.23
# Purpose: ZFS Snapshots bpool maintenance

function ZfsShowFreeSpace ()
{
    zfs list -o space
    zpool list
}

function ZfsListBpool() {
   zfs list -r -t snapshot -o name,used,referenced,creation bpool/BOOT | less
}

function GetZfsBpoolSnapshotCount()
{
    ZfsSnapshotCount=$(zfs list -r -t snapshot -o name,used,referenced,creation bpool/BOOT | wc -l)
    line_count="$(($ZfsSnapshotCount-1))"
    echo -e "There are $line_count snapshots in bpool."
}

function ZfsTrimLast5()
{
    # Command for removing is: zsysctl state remove --system <statename>
    zfs list -r -t snapshot -o name,used,referenced,creation bpool/BOOT | \
         head -n 5 | \
         cut -c 35-40 | \
         xargs -n 1 zsysctl state remove --system
}

function ShowMenu() {
    
    while [[ "$menu_response" !=  "5" ]]
    do
        clear
        echo -e "=== ZFS BPool Maintenance ==="
        echo
        echo -e "1 - Show space in Zpools"
        echo -e "2 - Show list of BPool Snapshots."
        echo -e "3 - Show count of BPool Snapshots"
        echo -e "4 - Destroy oldest 5 BPool SnapShots"
        echo -e "5 - Exit"
        echo 
        read -p "Enter a valid menu response from 1 through 5:  " menu_response
        case $menu_response in
            1) ZfsShowFreeSpace;;
            2) ZfsListBpool;;
            3) GetZfsBpoolSnapshotCount;;
            4) ZfsTrimLast5;;
            5) exit;;
            *) echo -e "The response was not a valid choice.";; 
        esac
        
        echo
        read -p "Press any <Enter> key to continue" trashbin
    done
}

ShowMenu


```
Use gedit to paste/save it into a script file named "ZfsBpoolMaintenance". Then to run, while you are in the same folder
```

chmod +x ./ZfsBpoolMainteance
./ZfsBpoolMaintenance

```

---

### Post by MAFoElffen on 2022-10-24
Then check the status of the do-release-upgrade
```

apt install -f
dpkg --configure -a

```

---

### Post by anystupidassname on 2022-10-24
> **MAFoElffen said:**
> I think here, in this thread, would be better, as I have more freedom of how long a post can be for instructions.

First, the reason ZSys stopped taking snaphots a while back, is that if you checked your bpool in the /boot partition, you are probably going to find out that it is almost full, which is also probably a reason why your release upgrade failed (not enough space there)... When the bpool has less than 20% free space, then ZSys stops taking any new snapshots. I created a script for mine which deletes the old bpool snapshots, and leaves the 5 newest there.

This usually prompts an error saying that during any apt kinds of activity. You didn't notice that? No matters. Was in the past.

So the plan would be to boot from a Desktop LiveCD, mount the partitions in the installed system, activate the ZFS rpool and bpool of the installed system, delete some of the old bpool snap shots to free up some space... Before trying to roll back to your newest snap shot. If you try to revert too soon, I don't know if you would have enough space left in the bpool to do that.

Does that sound like a good plan?

Although bpool is currently not even close to full, you may be correct that (at some point in 2020) it was too full and snapshots stopped as a result.
Thanks again for the help and I will attempt to follow the rest of your instructions.

---

### Post by anystupidassname on 2022-10-24
> **MAFoElffen said:**
> Boot from an Ubuntu LiveCD and open up a graphical terminal and a browser. Navigate the browser back to this thread, so you can cut and paste commands and output between those.

From the terminal session:
```

sudo fdisk -l 2>&1 | sed '/\/dev\/loop/,+3 d' 2> /dev/null | uniq | grep 'Solaris'
lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL | grep -v '/snap/\|loop' | grep 'zfs_'
```
Please post the output of those two commands... The first will have output of Solaris boot and Solaris root. The second will ID the names of the ZFS rpool and bpool to be able to mount and activate them...

From that output, I'll post the next commands.

```
ubuntu@ubuntu:~$ sudo fdisk -l 2>&1 | sed '/\/dev\/loop/,+3 d' 2> /dev/null | uniq | grep 'Solaris'
ubuntu@ubuntu:~$ lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL | grep -v '/snap/\|loop' | grep 'zfs_'
&#9500;&#9472;sda5     2G zfs_member bpool                                                       
&#9492;&#9472;sda6   927G zfs_member rpool
```

I took the liberty of trying your same command grepping for FreeBSD instead. Hopefully this is what you were aiming for?
root@ubuntu:/home/ubuntu# fdisk -l 2>&1 | sed '/\/dev\/loop/,+3 d' 2> /dev/null | uniq | grep 'FreeBSD'
/dev/sda5       5249024    9443327    4194304    2G a5 FreeBSD
/dev/sda6       9445376 1953525167 1944079792  927G a5 FreeBSD

---

### Post by anystupidassname on 2022-10-24
success > sudo -i
success > apt update
already installed > apt install -y zfs-initramfs
"no pools available" > zpool list   # ensure the output says: "no datasets available"
success > zfs list  # ensure the output says: "no datasets available"
success >  zpool import -N -R /mnt rpool

"rpool" > Adjust the name rpool above to either rpool or tmprpool, depending on the output from above...
zfs list
```
root@ubuntu:~# zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
rpool                                              425G   493G       96K  /mnt
rpool/ROOT                                        17.7G   493G       96K  none
rpool/ROOT/ubuntu_uxtu99                          17.7G   493G     12.5G  /mnt
rpool/ROOT/ubuntu_uxtu99/usr                      16.5M   493G       96K  /mnt/usr
rpool/ROOT/ubuntu_uxtu99/usr/local                16.4M   493G     16.4M  /mnt/usr/local
rpool/ROOT/ubuntu_uxtu99/var                      5.21G   493G       96K  /mnt/var
rpool/ROOT/ubuntu_uxtu99/var/lib                  4.58G   493G     4.40G  /mnt/var/lib
rpool/ROOT/ubuntu_uxtu99/var/lib/AccountServices    96K   493G       96K  /mnt/var/lib/AccountServices
rpool/ROOT/ubuntu_uxtu99/var/lib/NetworkManager    376K   493G      376K  /mnt/var/lib/NetworkManager
rpool/ROOT/ubuntu_uxtu99/var/lib/apt              78.8M   493G     78.8M  /mnt/var/lib/apt
rpool/ROOT/ubuntu_uxtu99/var/lib/dpkg              102M   493G      102M  /mnt/var/lib/dpkg
rpool/ROOT/ubuntu_uxtu99/var/log                   616M   493G      616M  /mnt/var/log
rpool/ROOT/ubuntu_uxtu99/var/mail                   96K   493G       96K  /mnt/var/mail
rpool/ROOT/ubuntu_uxtu99/var/spool                36.4M   493G     36.4M  /mnt/var/spool
rpool/USERDATA                                     405G   493G       96K  /mnt
rpool/USERDATA/ncr_mk6ljb                          405G   493G      319G  /mnt/home/ncr
rpool/USERDATA/root_mk6ljb                        18.8M   493G     14.0M  /mnt/root
```

success > zfs mount rpool/ROOT/ubuntu_uxtu99
success > zfs mount -a
success? > mount --rbind /dev  /mnt/dev
 success? > mount --rbind /proc /mnt/proc
success? > mount --rbind /sys  /mnt/sys
 success? > chroot /mnt /bin/bash --login

---

### Post by anystupidassname on 2022-10-24
> **MAFoElffen said:**
> Next you want to make room in your bpool... 

I wrote this script to automate that for me on mine:
```

#!/bin/bash
# MAFoElffen, <mafoelffen@ubuntu.com>, 2021.12.28, last modified: 2022.02.23
# Purpose: ZFS Snapshots bpool maintenance

function ZfsShowFreeSpace ()
{
    zfs list -o space
    zpool list
}

function ZfsListBpool() {
   zfs list -r -t snapshot -o name,used,referenced,creation bpool/BOOT | less
}

function GetZfsBpoolSnapshotCount()
{
    ZfsSnapshotCount=$(zfs list -r -t snapshot -o name,used,referenced,creation bpool/BOOT | wc -l)
    line_count="$(($ZfsSnapshotCount-1))"
    echo -e "There are $line_count snapshots in bpool."
}

function ZfsTrimLast5()
{
    # Command for removing is: zsysctl state remove --system <statename>
    zfs list -r -t snapshot -o name,used,referenced,creation bpool/BOOT | \
         head -n 5 | \
         cut -c 35-40 | \
         xargs -n 1 zsysctl state remove --system
}

function ShowMenu() {
    
    while [[ "$menu_response" !=  "5" ]]
    do
        clear
        echo -e "=== ZFS BPool Maintenance ==="
        echo
        echo -e "1 - Show space in Zpools"
        echo -e "2 - Show list of BPool Snapshots."
        echo -e "3 - Show count of BPool Snapshots"
        echo -e "4 - Destroy oldest 5 BPool SnapShots"
        echo -e "5 - Exit"
        echo 
        read -p "Enter a valid menu response from 1 through 5:  " menu_response
        case $menu_response in
            1) ZfsShowFreeSpace;;
            2) ZfsListBpool;;
            3) GetZfsBpoolSnapshotCount;;
            4) ZfsTrimLast5;;
            5) exit;;
            *) echo -e "The response was not a valid choice.";; 
        esac
        
        echo
        read -p "Press any <Enter> key to continue" trashbin
    done
}

ShowMenu


```
Use gedit to paste/save it into a script file named "ZfsBpoolMaintenance". Then to run, while you are in the same folder
```

chmod +x ./ZfsBpoolMainteance
./ZfsBpoolMaintenance

```

At this point, bpool was not mounted. I took the liberty of "ad libbing"
from outside the chroot, I ran:
sudo zpool import -f bpool -R /mnt/boot
then I ran your script again inside chroot
```
NAME                                              AVAIL   USED  USEDSNAP  USEDDS  USEDREFRESERV  USEDCHILD
bpool                                              213M   811M        0B     96K             0B       811M
bpool/BOOT                                         213M   808M        0B     96K             0B       807M
bpool/BOOT/ubuntu_uxtu99                           213M   807M      353M    454M             0B         0B
rpool                                              493G   425G        0B     96K             0B       425G
rpool/ROOT                                         493G  17.7G        0B     96K             0B      17.7G
rpool/ROOT/ubuntu_uxtu99                           493G  17.7G        0B   12.5G             0B      5.23G
rpool/ROOT/ubuntu_uxtu99/usr                       493G  16.5M        0B     96K             0B      16.4M
rpool/ROOT/ubuntu_uxtu99/usr/local                 493G  16.4M        0B   16.4M             0B         0B
rpool/ROOT/ubuntu_uxtu99/var                       493G  5.21G        0B     96K             0B      5.21G
rpool/ROOT/ubuntu_uxtu99/var/lib                   493G  4.58G        0B   4.40G             0B       181M
rpool/ROOT/ubuntu_uxtu99/var/lib/AccountServices   493G    96K        0B     96K             0B         0B
rpool/ROOT/ubuntu_uxtu99/var/lib/NetworkManager    493G   376K        0B    376K             0B         0B
rpool/ROOT/ubuntu_uxtu99/var/lib/apt               493G  78.8M        0B   78.8M             0B         0B
rpool/ROOT/ubuntu_uxtu99/var/lib/dpkg              493G   102M        0B    102M             0B         0B
rpool/ROOT/ubuntu_uxtu99/var/log                   493G   616M        0B    616M             0B         0B
rpool/ROOT/ubuntu_uxtu99/var/mail                  493G    96K        0B     96K             0B         0B
rpool/ROOT/ubuntu_uxtu99/var/spool                 493G  36.4M        0B   36.4M             0B         0B
rpool/USERDATA                                     493G   405G        0B     96K             0B       405G
rpool/USERDATA/ncr_mk6ljb                          493G   405G     86.1G    319G             0B         0B
rpool/USERDATA/root_mk6ljb                         493G  18.8M     4.71M   14.0M             0B         0B
NAME    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool  1.88G   812M  1.08G        -         -    10%    42%  1.00x    ONLINE  /mnt/boot
rpool   920G   398G   522G        -         -    34%    43%  1.06x    ONLINE  /mnt
```

There are 31 snapshots only covering a range of one week in June 2020...
 Option #4 of your script threw the error "xargs: zsysctl: No such file or directory"
Maybe I'll wait here for a bit to see if you want me to keep going or if you need to adjust the instructions?

---

### Post by MAFoElffen on 2022-10-24
Utility 'zsysctl' is from package 'zsys' and is located at
```

$ which zsysctl
/usr/sbin/zsysctl

```
You can see the names of the snaphots save by zsys via
```

sudo zsysctl show | less

```
The old snaphots can be removed using the snapshot_name via
```

sudo zsysctl state remove --system snapshot_name

```

You do not need to mount an ESP partition, because you are booting as Legacy, not as UEFI, right?

---

### Post by anystupidassname on 2022-10-25
> **MAFoElffen said:**
> Utility 'zsysctl' is from package 'zsys' and is located at
```

$ which zsysctl
/usr/sbin/zsysctl

```
You can see the names of the snaphots save by zsys via
```

sudo zsysctl show | less

```
The old snaphots can be removed using the snapshot_name via
```

sudo zsysctl state remove --system snapshot_name

```

You do not need to mount an ESP partition, because you are booting as Legacy, not as UEFI, right?


OK, so zsys was not installed (perhaps why snapshots stopped?) and the liveUSB environment's DNS wasn't  working. I added nameserver line to  resolv.conf, ran apt update and apt install zsys.

"sudo zsysctl show | less" and option #4 of the script now throw error: "ERROR couldn't connect to zsys daemon: connection error: desc = "transport: Error while dialing dial unix /run/zsysd.sock: connect: no such file or directory""

I cannot restart the service because systemctl doesn't want to in chroot..?
 I went to reboot but "zpool export -a" says "cannot export 'rpool': pool is busy".
"lsof | grep rpool" shows nothing...

The zsys transport error continues after a reboot.

Yes, I think the original ubuntu install created the ESP unnecessarily and it has confused me ever since. I confirm it is a msdos mbr (not gpt) and legacy bios (not UEFI capable).

Since bpool space doesn't seem to be a primary issue at this point, I went ahead and ran:

"apt install -f" (successful and nothing was done)
"dpkg --configure -a" (successful and nothing was done)
"apt upgrade" (installed about 500mb of stuff including kernel which seems to have failed (zsys...?)

note: zsys transport error also appears in an "apt upgrade" operation.

Do you want to continue trying to clear bpool space (if yes, how? I'm stuck)
Or do we continue from here with the plan?

UPDATE: "zfs list -r -t snapshot -o name bpool/BOOT | grep auto-snap | xargs -n 1 sudo zfs destroy"
I was able to remove all but 5 snapshots from bpool (down to 38% usage) so I just need to get bootable again. What is next please?

---

### Post by anystupidassname on 2022-10-25
While waiting for your expert response/advice, I'm trying to troubleshoot the grub boot issue on my own rather unsuccessfully.

When  I try to boot the system normally, if I hit "e" to edit the grub entry  (which now shows 22.04.1 LTS) the last two lines, however, are still  pointing to a 5.4.0 kernel.
So I try to edit it to boot a 5.15.0-50 entry which I'm looking at from this "[tree /boot]("https://termbin.com/cf2h")"
but this isn't working because of not found and load kernel first errors.
I'm still lost...

UPDATE: I tried adapting the chroot instructions from the gentoo handbook and managed to run "apt install grub2" without errors but "update-grub" throws this:
[https://pastebin.com/UGtcnyfc](https://pastebin.com/UGtcnyfc)

---

### Post by MAFoElffen on 2022-10-25
For Ubuntu 22.04 and newer booting as CSM/Legacy
```

apt install --yes grub-pc linux-image-generic zfs-initramfs zsys

```
But first... check to see in the old /etc/fstab file and check to see if /boot and /boot/efi are there or not... Then try to list the contetnts of those directorys...

Early on with on with ZFS-on-Root, there was a process that created the ESP directory, so that it ended up as a dual boot install. I don't know if that oocurs with the Ubuntu Installer autmatically...

If you mount that ESP directory and post the contents so I can see that, before you try to change things, then I can try to work that out for different instructions... As I remember, (checing my notes) it was something like this:
```

apt install --yes --no-install-recommends linux-image-generic linux-headers-generic
apt install --yes zfs-initramfs cryptsetup keyutils grub-efi-amd64-signed shim-signed
KERNEL=`ls /usr/lib/modules/ | cut -d/ -f1 | sed 's/linux-image-//'`
update-initramfs -u -k $KERNEL
update-grub
grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=Ubuntu --recheck --no-floppy

```
Let me spin up an Ubuntu 22.04 ZFS-on-Root Legacy/CSM image and check what it puts where... That would be the right thing to look at to see what may be on yours. I have some appointments to take care of. I'll do that tonight.

---

### Post by MAFoElffen on 2022-10-25
Even at BIOS boot with CSM/Legacy, It installed with an EFI partition and 'grub-efi-amd65-signed'...
```

mafoelffen@ubuntu-ZFS-PC-Q35-ICH9-22041-02:~$ sudo fdisk -l | grep '^/dev/'
/dev/vda1      2048     4095     2048    1M BIOS boot
/dev/vda2      4096  1054719  1050624  513M EFI System
/dev/vda3   1054720  9037823  7983104  3.8G Linux swap
/dev/vda4   9037824 13178879  4141056    2G Solaris boot
/dev/vda5  13178880 83886046 70707167 33.7G Solaris root

mafoelffen@ubuntu-ZFS-PC-Q35-ICH9-22041-02:~$ sudo apt list grub-* | grep 'installed'

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

grub-common/jammy,now 2.06-2ubuntu7 amd64 [installed]
grub-efi-amd64-bin/jammy,now 2.06-2ubuntu7 amd64 [installed]
grub-efi-amd64-signed/jammy,now 1.180+2.06-2ubuntu7 amd64 [installed]
grub-gfxpayload-lists/jammy,now 0.7 amd64 [installed]
grub-pc-bin/jammy,now 2.06-2ubuntu7 amd64 [installed]
grub-pc/jammy,now 2.06-2ubuntu7 amd64 [installed]
mafoelffen@ubuntu-ZFS-PC-Q35-ICH9-22041-02:~$ 

```
So that would mean making sure the ESP partition "EFI" is mounted and using
```

grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --recheck --no-floppy

```

---

### Post by anystupidassname on 2022-10-26
Information overload, I need to make sure we're on the same page. Too easy for me to miss a detail which could throw everything off.

Steps I'm taking in liveusb right after fresh boot:

sudo -i                               (zsys and zfs-initramfs are already installed)
zpool import -f rpool -R /mnt
zpool import -f bpool -R /mnt
zfs mount rpool/ROOT/ubuntu_uxtu99
zfs mount -a
mount /dev/sda1 /mnt/boot/efi
mount --types proc /proc /mnt/proc
mount --rbind /sys /mnt/sys
mount --make-rslave /mnt/sys
mount --rbind /dev /mnt/dev
mount --make-rslave /mnt/dev
mount --bind /run /mnt/run
mount --make-slave /mnt/run
chroot /mnt /bin/bash --login
                

The resulting environment:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
UUID=7D37-A683    /boot/efi    vfat    umask=0077    0    1
/boot/efi/grub    /boot/grub    none    defaults,bind    0    0
##UUID=72e3d19f-b61e-4212-90d2-f6e333a3c4f7    none    swap    discard    0    0
```

```
lsblk -f               (excluding liveusb stuff)
sda                                                                                                             
&#9500;&#9472;sda1 vfat       FAT32                                     7D37-A683                             499.9M     2% /boot/efi
&#9500;&#9472;sda2                                                                                                          
&#9500;&#9472;sda5 zfs_member 5000             bpool                    12193762941654060240                                
&#9492;&#9472;sda6 zfs_member 5000             rpool                    3453189339821368707
```


tree -R /boot > [https://termbin.com/s72f](https://termbin.com/s72f)

```
sudo apt list grub-* | grep 'installed'

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

grub-common/jammy,now 2.06-2ubuntu7 amd64 [installed]
grub-efi-amd64-bin/jammy,now 2.06-2ubuntu7 amd64 [installed]
grub-gfxpayload-lists/jammy,now 0.7 amd64 [installed,automatic]
grub-pc-bin/jammy,now 2.06-2ubuntu7 amd64 [installed]
grub-pc/jammy,now 2.06-2ubuntu7 amd64 [installed]
```

```
grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --recheck --no-floppy
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
```

```
update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Warning: didn't find any valid initrd or kernel.
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
done

```

A couple questions:
Should it be "zpool import -f bpool -R /mnt" ? or "zpool import -f bpool -R /mnt/boot" ? or does it matter? (I've tried both and not noticed a difference)
Is the mounting order correct? rpool, bpool, esp?
What needs to be verified to make sure all of the things I've tried so far have not changed something in a way you aren't expecting?

Thanks again for your assistance.

---

### Post by MAFoElffen on 2022-10-26
Out of the house. Reading and replying from my phone... LOL. No. I don't see a difference on my test machines either... Besides, when you mount the rpool, and do a 'sudo mount -a', it does the fstab mounts, which should mount the bpool (most of the time). It looks good to me. 

Did you do an 
```
 
apt update && apt upgrade

```
And ensure that during that, that it built intramfs images without errors? If so, then you should be good again.

---

### Post by anystupidassname on 2022-10-27
grub-install and update-grub fail. So the system doesn't boot. initramfs doesn't get called because there is no newer kernel I think.

---

### Post by anystupidassname on 2022-10-27
apt reinstall linux-image-5.15.0-43-generic
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libflashrom1 libftdi1-2 linux-headers-5.15.0-25 linux-headers-5.15.0-25-generic linux-image-5.15.0-25-generic linux-modules-5.15.0-25-generic
  linux-modules-extra-5.15.0-25-generic
Use 'apt autoremove' to remove them.
The following additional packages will be installed:
  linux-modules-5.15.0-43-generic
Suggested packages:
  fdutils linux-doc | linux-source-5.15.0 linux-tools linux-headers-5.15.0-43-generic linux-modules-extra-5.15.0-43-generic
The following NEW packages will be installed:
  linux-image-5.15.0-43-generic linux-modules-5.15.0-43-generic
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 32.9 MB of archives.
After this operation, 123 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 linux-modules-5.15.0-43-generic amd64 5.15.0-43.46 [22.0 MB]
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 linux-image-5.15.0-43-generic amd64 5.15.0-43.46 [10.9 MB]
Fetched 32.9 MB in 3s (12.9 MB/s)                         
Selecting previously unselected package linux-modules-5.15.0-43-generic.
(Reading database ... 438347 files and directories currently installed.)
Preparing to unpack .../linux-modules-5.15.0-43-generic_5.15.0-43.46_amd64.deb ...
Unpacking linux-modules-5.15.0-43-generic (5.15.0-43.46) ...
Selecting previously unselected package linux-image-5.15.0-43-generic.
Preparing to unpack .../linux-image-5.15.0-43-generic_5.15.0-43.46_amd64.deb ...
Unpacking linux-image-5.15.0-43-generic (5.15.0-43.46) ...
Setting up linux-image-5.15.0-43-generic (5.15.0-43.46) ...
I: /boot/vmlinuz.old is now a symlink to vmlinuz-5.15.0-43-generic
I: /boot/initrd.img.old is now a symlink to initrd.img-5.15.0-43-generic
I: /boot/vmlinuz is now a symlink to vmlinuz-5.15.0-43-generic
I: /boot/initrd.img is now a symlink to initrd.img-5.15.0-43-generic
Setting up linux-modules-5.15.0-43-generic (5.15.0-43.46) ...
Processing triggers for linux-image-5.15.0-43-generic (5.15.0-43.46) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.15.0-43-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: vmlinuz-5.15.0-43-generic in rpool/ROOT/ubuntu_uxtu99
Found initrd image: initrd.img-5.15.0-43-generic in rpool/ROOT/ubuntu_uxtu99
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
done

---

### Post by MAFoElffen on 2022-10-27
Please post the output of (within code tags)
```

ls /boot/efi
ls /boot/efi/grub

```

---

### Post by MAFoElffen on 2022-10-27
Well, at this point, you have lots of experience working with and mounting ZFS systems. 

Run the [UbuntuForums 'system-info']("https://github.com/UbuntuForums/system-info") script and upload the report to a pastebin. 
```

wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && chmod +x system-info && ./system-info

```
Please post the report's URL in a post.

From here, you have two choices:
#1) Continue to try to rescue your old install.
#2) Backup your data to your external drive (again). Use the apt 'manually installed' section from that 'system-info' report to do a clean/fresh install of 22.04 LTS, and migrate your data and settings to that new installation.

I'm thinking at this point, and from what has been going on, that #2 would be faster and easier... You would be back up, without problems, in less than a few hours.

---

### Post by anystupidassname on 2022-10-27
> **MAFoElffen said:**
> Please post the output of (within code tags)
```

ls /boot/efi
ls /boot/efi/grub

```

```
ls -hasl /boot/efi
total 21K
4.0K drwxr-xr-x 4 root root 4.0K Jan  1  1970 .
8.5K drwxr-xr-x 4 root root   18 Oct 27 09:40 ..
4.0K drwxr-xr-x 4 root root 4.0K Oct 17 00:03 EFI
4.0K drwxr-xr-x 6 root root 4.0K Oct 17 00:06 grub

```

```
ls -hasl /boot/efi/grub
total 2.4M
4.0K drwxr-xr-x 6 root root 4.0K Oct 17 00:06 .
4.0K drwxr-xr-x 4 root root 4.0K Jan  1  1970 ..
4.0K drwxr-xr-x 2 root root 4.0K Feb 29  2020 fonts
4.0K -rwxr-xr-x 1 root root  712 Feb 20  2020 gfxblacklist.txt
 16K -rwxr-xr-x 1 root root  15K Oct 17 00:06 grub.cfg
4.0K -rwxr-xr-x 1 root root 1.0K Jun 25  2020 grubenv
 44K drwxr-xr-x 2 root root  44K Oct 17 00:05 i386-pc
4.0K drwxr-xr-x 2 root root 4.0K Oct 17 00:05 locale
2.3M -rwxr-xr-x 1 root root 2.3M Apr 17  2020 unicode.pf2
 20K drwxr-xr-x 2 root root  20K Oct 17 00:03 x86_64-efi
```

---

### Post by anystupidassname on 2022-10-27
> **MAFoElffen said:**
> Well, at this point, you have lots of experience working with and mounting ZFS systems. 

Run the [UbuntuForums 'system-info']("https://github.com/UbuntuForums/system-info") script and upload the report to a pastebin. 
```

wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && chmod +x system-info && ./system-info

```
Please post the report's URL in a post.

From here, you have two choices:
#1) Continue to try to rescue your old install.
#2) Backup your data to your external drive (again). Use the apt 'manually installed' section from that 'system-info' report to do a clean/fresh install of 22.04 LTS, and migrate your data and settings to that new installation.

I'm thinking at this point, and from what has been going on, that #2 would be faster and easier... You would be back up, without problems, in less than a few hours.

[https://paste.ubuntu.com/p/jTC9vWry5S/](https://paste.ubuntu.com/p/jTC9vWry5S/)

I'm only interested in #1. But I cannot find the word "manually" in the pastebin at all.

---

### Post by MAFoElffen on 2022-10-27
This is what I have on my ZFS Legacy/CSM test machine, which seems to be the same as yours:
```

mafoelffen@ubuntu-ZFS-PC-Q35-ICH9-22041-02:~$ ls /boot/efi
EFI  grub
mafoelffen@ubuntu-ZFS-PC-Q35-ICH9-22041-02:~$ ls /boot/efi/grub
fonts             grub.cfg  i386-pc  unicode.pf2
gfxblacklist.txt  grubenv   locale   x86_64-efi
mafoelffen@ubuntu-ZFS-PC-Q35-ICH9-22041-02:~$ ls /boot/efi/efi
BOOT  ubuntu
mafoelffen@ubuntu-ZFS-PC-Q35-ICH9-22041-02:~$ ls /boot/efi/efi/BOOT
BOOTX64.EFI  fbx64.efi  mmx64.efi
mafoelffen@ubuntu-ZFS-PC-Q35-ICH9-22041-02:~$ ls /boot/efi/efi/ubuntu
BOOTX64.CSV  grub.cfg  grubx64.efi  mmx64.efi  shimx64.efi

```
Which would confirm that the mounts are correct...

Wait one... Mounting my test VM from a LiveCD ISO and reinstalling grub...

---

### Post by MAFoElffen on 2022-10-27
I think maybe you might have had some of the mounts wrong...

Look at the term log of what I did...
```

ubuntu@ubuntu:~$ sudo apt install zfs-initramfs
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
zfs-initramfs is already the newest version (2.1.4-0ubuntu0.1).
0 upgraded, 0 newly installed, 0 to remove and 250 not upgraded.
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# zfs list
no datasets available
root@ubuntu:~# zpool list
no pools available
root@ubuntu:~# zpool import -N -R /mnt rpool
root@ubuntu:~# zpool list
NAME    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
rpool  33.5G  6.20G  27.3G        -         -     2%    18%  1.00x    ONLINE  /mnt
root@ubuntu:~# zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
rpool                                             6.20G  26.3G       96K  /mnt
rpool/ROOT                                        6.19G  26.3G       96K  none
rpool/ROOT/ubuntu_k930ob                          6.19G  26.3G     3.91G  /mnt
rpool/ROOT/ubuntu_k930ob/srv                        96K  26.3G       96K  /mnt/srv
rpool/ROOT/ubuntu_k930ob/usr                       224K  26.3G       96K  /mnt/usr
rpool/ROOT/ubuntu_k930ob/usr/local                 128K  26.3G      128K  /mnt/usr/local
rpool/ROOT/ubuntu_k930ob/var                      2.28G  26.3G       96K  /mnt/var
rpool/ROOT/ubuntu_k930ob/var/games                  96K  26.3G       96K  /mnt/var/games
rpool/ROOT/ubuntu_k930ob/var/lib                  2.27G  26.3G     2.14G  /mnt/var/lib
rpool/ROOT/ubuntu_k930ob/var/lib/AccountsService    96K  26.3G       96K  /mnt/var/lib/AccountsService
rpool/ROOT/ubuntu_k930ob/var/lib/NetworkManager    132K  26.3G      132K  /mnt/var/lib/NetworkManager
rpool/ROOT/ubuntu_k930ob/var/lib/apt              96.6M  26.3G     96.6M  /mnt/var/lib/apt
rpool/ROOT/ubuntu_k930ob/var/lib/dpkg             35.7M  26.3G     35.7M  /mnt/var/lib/dpkg
rpool/ROOT/ubuntu_k930ob/var/log                  2.97M  26.3G     2.97M  /mnt/var/log
rpool/ROOT/ubuntu_k930ob/var/mail                   96K  26.3G       96K  /mnt/var/mail
rpool/ROOT/ubuntu_k930ob/var/snap                 1.43M  26.3G     1.43M  /mnt/var/snap
rpool/ROOT/ubuntu_k930ob/var/spool                 112K  26.3G      112K  /mnt/var/spool
rpool/ROOT/ubuntu_k930ob/var/www                    96K  26.3G       96K  /mnt/var/www
rpool/USERDATA                                    2.32M  26.3G       96K  /mnt
rpool/USERDATA/mafoelffen_o8mzrf                  2.10M  26.3G     2.10M  /mnt/home/mafoelffen
rpool/USERDATA/root_o8mzrf                         132K  26.3G      132K  /mnt/root
root@ubuntu:~# zfs mount rpool/ROOT/ubuntu_k930ob
root@ubuntu:~# zfs mount -a
root@ubuntu:~# zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
rpool                                             6.20G  26.3G       96K  /mnt
rpool/ROOT                                        6.19G  26.3G       96K  none
rpool/ROOT/ubuntu_k930ob                          6.19G  26.3G     3.91G  /mnt
rpool/ROOT/ubuntu_k930ob/srv                        96K  26.3G       96K  /mnt/srv
rpool/ROOT/ubuntu_k930ob/usr                       224K  26.3G       96K  /mnt/usr
rpool/ROOT/ubuntu_k930ob/usr/local                 128K  26.3G      128K  /mnt/usr/local
rpool/ROOT/ubuntu_k930ob/var                      2.28G  26.3G       96K  /mnt/var
rpool/ROOT/ubuntu_k930ob/var/games                  96K  26.3G       96K  /mnt/var/games
rpool/ROOT/ubuntu_k930ob/var/lib                  2.27G  26.3G     2.14G  /mnt/var/lib
rpool/ROOT/ubuntu_k930ob/var/lib/AccountsService    96K  26.3G       96K  /mnt/var/lib/AccountsService
rpool/ROOT/ubuntu_k930ob/var/lib/NetworkManager    132K  26.3G      132K  /mnt/var/lib/NetworkManager
rpool/ROOT/ubuntu_k930ob/var/lib/apt              96.6M  26.3G     96.6M  /mnt/var/lib/apt
rpool/ROOT/ubuntu_k930ob/var/lib/dpkg             35.7M  26.3G     35.7M  /mnt/var/lib/dpkg
rpool/ROOT/ubuntu_k930ob/var/log                  2.97M  26.3G     2.97M  /mnt/var/log
rpool/ROOT/ubuntu_k930ob/var/mail                   96K  26.3G       96K  /mnt/var/mail
rpool/ROOT/ubuntu_k930ob/var/snap                 1.43M  26.3G     1.43M  /mnt/var/snap
rpool/ROOT/ubuntu_k930ob/var/spool                 112K  26.3G      112K  /mnt/var/spool
rpool/ROOT/ubuntu_k930ob/var/www                    96K  26.3G       96K  /mnt/var/www
rpool/USERDATA                                    2.32M  26.3G       96K  /mnt
rpool/USERDATA/mafoelffen_o8mzrf                  2.10M  26.3G     2.10M  /mnt/home/mafoelffen
rpool/USERDATA/root_o8mzrf                         132K  26.3G      132K  /mnt/root
root@ubuntu:~# zpool list
NAME    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
rpool  33.5G  6.20G  27.3G        -         -     2%    18%  1.00x    ONLINE  /mnt
root@ubuntu:~# zpool import -N -R /mnt/boot bpool
root@ubuntu:~# zpool list
NAME    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool  1.88G   244M  1.64G        -         -     0%    12%  1.00x    ONLINE  /mnt/boot
rpool  33.5G  6.20G  27.3G        -         -     2%    18%  1.00x    ONLINE  /mnt
root@ubuntu:~# zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              244M  1.51G       96K  /mnt/boot/boot
bpool/BOOT                                         243M  1.51G       96K  none
bpool/BOOT/ubuntu_k930ob                           243M  1.51G      243M  /mnt/boot/boot
rpool                                             6.20G  26.3G       96K  /mnt
rpool/ROOT                                        6.19G  26.3G       96K  none
rpool/ROOT/ubuntu_k930ob                          6.19G  26.3G     3.91G  /mnt
rpool/ROOT/ubuntu_k930ob/srv                        96K  26.3G       96K  /mnt/srv
rpool/ROOT/ubuntu_k930ob/usr                       224K  26.3G       96K  /mnt/usr
rpool/ROOT/ubuntu_k930ob/usr/local                 128K  26.3G      128K  /mnt/usr/local
rpool/ROOT/ubuntu_k930ob/var                      2.28G  26.3G       96K  /mnt/var
rpool/ROOT/ubuntu_k930ob/var/games                  96K  26.3G       96K  /mnt/var/games
rpool/ROOT/ubuntu_k930ob/var/lib                  2.27G  26.3G     2.14G  /mnt/var/lib
rpool/ROOT/ubuntu_k930ob/var/lib/AccountsService    96K  26.3G       96K  /mnt/var/lib/AccountsService
rpool/ROOT/ubuntu_k930ob/var/lib/NetworkManager    132K  26.3G      132K  /mnt/var/lib/NetworkManager
rpool/ROOT/ubuntu_k930ob/var/lib/apt              96.6M  26.3G     96.6M  /mnt/var/lib/apt
rpool/ROOT/ubuntu_k930ob/var/lib/dpkg             35.7M  26.3G     35.7M  /mnt/var/lib/dpkg
rpool/ROOT/ubuntu_k930ob/var/log                  2.97M  26.3G     2.97M  /mnt/var/log
rpool/ROOT/ubuntu_k930ob/var/mail                   96K  26.3G       96K  /mnt/var/mail
rpool/ROOT/ubuntu_k930ob/var/snap                 1.43M  26.3G     1.43M  /mnt/var/snap
rpool/ROOT/ubuntu_k930ob/var/spool                 112K  26.3G      112K  /mnt/var/spool
rpool/ROOT/ubuntu_k930ob/var/www                    96K  26.3G       96K  /mnt/var/www
rpool/USERDATA                                    2.32M  26.3G       96K  /mnt
rpool/USERDATA/mafoelffen_o8mzrf                  2.10M  26.3G     2.10M  /mnt/home/mafoelffen
rpool/USERDATA/root_o8mzrf                         132K  26.3G      132K  /mnt/root
root@ubuntu:~# zfs mount -a
root@ubuntu:~# mount --rbind /dev  /mnt/dev
root@ubuntu:~# mount --rbind /proc /mnt/proc
root@ubuntu:~# mount --rbind /sys  /mnt/sys
root@ubuntu:~# chroot /mnt /bin/bash --login
root@ubuntu:/# ls
bin   cdrom  etc   lib    lib64   media  opt   root  sbin  srv  tmp  var
boot  dev    home  lib32  libx32  mnt    proc  run   snap  sys  usr
root@ubuntu:/# ls /boot/efi
root@ubuntu:/# ls /boot/
boot  efi  grub
root@ubuntu:/# mount -a
root@ubuntu:/# ls /boot/efi
EFI  grub
root@ubuntu:/# ls /boot/efi/grub
fonts  gfxblacklist.txt  grub.cfg  grubenv  i386-pc  locale  unicode.pf2  x86_64-efi
root@ubuntu:/# grub-install --target=x86_64-efi --efi-directory=/boot/efi \
>     --bootloader-id=ubuntu --recheck --no-floppy
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
root@ubuntu:/# exit
root@ubuntu:/# zpool export -a
root@ubuntu:/# reboot

```

---

### Post by anystupidassname on 2022-10-28
> **MAFoElffen said:**
> I think maybe you might have had some of the mounts wrong...

Look at the term log of what I did...
```

ubuntu@ubuntu:~$ sudo apt install zfs-initramfs
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
zfs-initramfs is already the newest version (2.1.4-0ubuntu0.1).
0 upgraded, 0 newly installed, 0 to remove and 250 not upgraded.
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# zfs list
no datasets available
root@ubuntu:~# zpool list
no pools available
root@ubuntu:~# zpool import -N -R /mnt rpool
root@ubuntu:~# zpool list
NAME    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
rpool  33.5G  6.20G  27.3G        -         -     2%    18%  1.00x    ONLINE  /mnt
root@ubuntu:~# zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
rpool                                             6.20G  26.3G       96K  /mnt
rpool/ROOT                                        6.19G  26.3G       96K  none
rpool/ROOT/ubuntu_k930ob                          6.19G  26.3G     3.91G  /mnt
rpool/ROOT/ubuntu_k930ob/srv                        96K  26.3G       96K  /mnt/srv
rpool/ROOT/ubuntu_k930ob/usr                       224K  26.3G       96K  /mnt/usr
rpool/ROOT/ubuntu_k930ob/usr/local                 128K  26.3G      128K  /mnt/usr/local
rpool/ROOT/ubuntu_k930ob/var                      2.28G  26.3G       96K  /mnt/var
rpool/ROOT/ubuntu_k930ob/var/games                  96K  26.3G       96K  /mnt/var/games
rpool/ROOT/ubuntu_k930ob/var/lib                  2.27G  26.3G     2.14G  /mnt/var/lib
rpool/ROOT/ubuntu_k930ob/var/lib/AccountsService    96K  26.3G       96K  /mnt/var/lib/AccountsService
rpool/ROOT/ubuntu_k930ob/var/lib/NetworkManager    132K  26.3G      132K  /mnt/var/lib/NetworkManager
rpool/ROOT/ubuntu_k930ob/var/lib/apt              96.6M  26.3G     96.6M  /mnt/var/lib/apt
rpool/ROOT/ubuntu_k930ob/var/lib/dpkg             35.7M  26.3G     35.7M  /mnt/var/lib/dpkg
rpool/ROOT/ubuntu_k930ob/var/log                  2.97M  26.3G     2.97M  /mnt/var/log
rpool/ROOT/ubuntu_k930ob/var/mail                   96K  26.3G       96K  /mnt/var/mail
rpool/ROOT/ubuntu_k930ob/var/snap                 1.43M  26.3G     1.43M  /mnt/var/snap
rpool/ROOT/ubuntu_k930ob/var/spool                 112K  26.3G      112K  /mnt/var/spool
rpool/ROOT/ubuntu_k930ob/var/www                    96K  26.3G       96K  /mnt/var/www
rpool/USERDATA                                    2.32M  26.3G       96K  /mnt
rpool/USERDATA/mafoelffen_o8mzrf                  2.10M  26.3G     2.10M  /mnt/home/mafoelffen
rpool/USERDATA/root_o8mzrf                         132K  26.3G      132K  /mnt/root
root@ubuntu:~# zfs mount rpool/ROOT/ubuntu_k930ob
root@ubuntu:~# zfs mount -a
root@ubuntu:~# zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
rpool                                             6.20G  26.3G       96K  /mnt
rpool/ROOT                                        6.19G  26.3G       96K  none
rpool/ROOT/ubuntu_k930ob                          6.19G  26.3G     3.91G  /mnt
rpool/ROOT/ubuntu_k930ob/srv                        96K  26.3G       96K  /mnt/srv
rpool/ROOT/ubuntu_k930ob/usr                       224K  26.3G       96K  /mnt/usr
rpool/ROOT/ubuntu_k930ob/usr/local                 128K  26.3G      128K  /mnt/usr/local
rpool/ROOT/ubuntu_k930ob/var                      2.28G  26.3G       96K  /mnt/var
rpool/ROOT/ubuntu_k930ob/var/games                  96K  26.3G       96K  /mnt/var/games
rpool/ROOT/ubuntu_k930ob/var/lib                  2.27G  26.3G     2.14G  /mnt/var/lib
rpool/ROOT/ubuntu_k930ob/var/lib/AccountsService    96K  26.3G       96K  /mnt/var/lib/AccountsService
rpool/ROOT/ubuntu_k930ob/var/lib/NetworkManager    132K  26.3G      132K  /mnt/var/lib/NetworkManager
rpool/ROOT/ubuntu_k930ob/var/lib/apt              96.6M  26.3G     96.6M  /mnt/var/lib/apt
rpool/ROOT/ubuntu_k930ob/var/lib/dpkg             35.7M  26.3G     35.7M  /mnt/var/lib/dpkg
rpool/ROOT/ubuntu_k930ob/var/log                  2.97M  26.3G     2.97M  /mnt/var/log
rpool/ROOT/ubuntu_k930ob/var/mail                   96K  26.3G       96K  /mnt/var/mail
rpool/ROOT/ubuntu_k930ob/var/snap                 1.43M  26.3G     1.43M  /mnt/var/snap
rpool/ROOT/ubuntu_k930ob/var/spool                 112K  26.3G      112K  /mnt/var/spool
rpool/ROOT/ubuntu_k930ob/var/www                    96K  26.3G       96K  /mnt/var/www
rpool/USERDATA                                    2.32M  26.3G       96K  /mnt
rpool/USERDATA/mafoelffen_o8mzrf                  2.10M  26.3G     2.10M  /mnt/home/mafoelffen
rpool/USERDATA/root_o8mzrf                         132K  26.3G      132K  /mnt/root
root@ubuntu:~# zpool list
NAME    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
rpool  33.5G  6.20G  27.3G        -         -     2%    18%  1.00x    ONLINE  /mnt
root@ubuntu:~# zpool import -N -R /mnt/boot bpool
root@ubuntu:~# zpool list
NAME    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool  1.88G   244M  1.64G        -         -     0%    12%  1.00x    ONLINE  /mnt/boot
rpool  33.5G  6.20G  27.3G        -         -     2%    18%  1.00x    ONLINE  /mnt
root@ubuntu:~# zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              244M  1.51G       96K  /mnt/boot/boot
bpool/BOOT                                         243M  1.51G       96K  none
bpool/BOOT/ubuntu_k930ob                           243M  1.51G      243M  /mnt/boot/boot
rpool                                             6.20G  26.3G       96K  /mnt
rpool/ROOT                                        6.19G  26.3G       96K  none
rpool/ROOT/ubuntu_k930ob                          6.19G  26.3G     3.91G  /mnt
rpool/ROOT/ubuntu_k930ob/srv                        96K  26.3G       96K  /mnt/srv
rpool/ROOT/ubuntu_k930ob/usr                       224K  26.3G       96K  /mnt/usr
rpool/ROOT/ubuntu_k930ob/usr/local                 128K  26.3G      128K  /mnt/usr/local
rpool/ROOT/ubuntu_k930ob/var                      2.28G  26.3G       96K  /mnt/var
rpool/ROOT/ubuntu_k930ob/var/games                  96K  26.3G       96K  /mnt/var/games
rpool/ROOT/ubuntu_k930ob/var/lib                  2.27G  26.3G     2.14G  /mnt/var/lib
rpool/ROOT/ubuntu_k930ob/var/lib/AccountsService    96K  26.3G       96K  /mnt/var/lib/AccountsService
rpool/ROOT/ubuntu_k930ob/var/lib/NetworkManager    132K  26.3G      132K  /mnt/var/lib/NetworkManager
rpool/ROOT/ubuntu_k930ob/var/lib/apt              96.6M  26.3G     96.6M  /mnt/var/lib/apt
rpool/ROOT/ubuntu_k930ob/var/lib/dpkg             35.7M  26.3G     35.7M  /mnt/var/lib/dpkg
rpool/ROOT/ubuntu_k930ob/var/log                  2.97M  26.3G     2.97M  /mnt/var/log
rpool/ROOT/ubuntu_k930ob/var/mail                   96K  26.3G       96K  /mnt/var/mail
rpool/ROOT/ubuntu_k930ob/var/snap                 1.43M  26.3G     1.43M  /mnt/var/snap
rpool/ROOT/ubuntu_k930ob/var/spool                 112K  26.3G      112K  /mnt/var/spool
rpool/ROOT/ubuntu_k930ob/var/www                    96K  26.3G       96K  /mnt/var/www
rpool/USERDATA                                    2.32M  26.3G       96K  /mnt
rpool/USERDATA/mafoelffen_o8mzrf                  2.10M  26.3G     2.10M  /mnt/home/mafoelffen
rpool/USERDATA/root_o8mzrf                         132K  26.3G      132K  /mnt/root
root@ubuntu:~# zfs mount -a
root@ubuntu:~# mount --rbind /dev  /mnt/dev
root@ubuntu:~# mount --rbind /proc /mnt/proc
root@ubuntu:~# mount --rbind /sys  /mnt/sys
root@ubuntu:~# chroot /mnt /bin/bash --login
root@ubuntu:/# ls
bin   cdrom  etc   lib    lib64   media  opt   root  sbin  srv  tmp  var
boot  dev    home  lib32  libx32  mnt    proc  run   snap  sys  usr
root@ubuntu:/# ls /boot/efi
root@ubuntu:/# ls /boot/
boot  efi  grub
root@ubuntu:/# mount -a
root@ubuntu:/# ls /boot/efi
EFI  grub
root@ubuntu:/# ls /boot/efi/grub
fonts  gfxblacklist.txt  grub.cfg  grubenv  i386-pc  locale  unicode.pf2  x86_64-efi
root@ubuntu:/# grub-install --target=x86_64-efi --efi-directory=/boot/efi \
>     --bootloader-id=ubuntu --recheck --no-floppy
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
root@ubuntu:/# exit
root@ubuntu:/# zpool export -a
root@ubuntu:/# reboot

```



Everything is identical for me until "ls /boot/efi".
```
.......
root@ubuntu:~# zpool list
NAME    SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool  1.88G   576M  1.31G        -         -     8%    29%  1.00x    ONLINE  /mnt/boot
rpool   920G   399G   521G        -         -    34%    43%  1.06x    ONLINE  /mnt
root@ubuntu:~# zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              575M   449M       96K  /mnt/boot/boot
bpool/BOOT                                         573M   449M       96K  none
bpool/BOOT/ubuntu_uxtu99                           573M   449M      298M  /mnt/boot/boot
rpool                                              425G   493G       96K  /mnt
rpool/ROOT                                        18.2G   493G       96K  none
rpool/ROOT/ubuntu_uxtu99                          18.2G   493G     13.0G  /mnt
rpool/ROOT/ubuntu_uxtu99/usr                      16.5M   493G       96K  /mnt/usr
rpool/ROOT/ubuntu_uxtu99/usr/local                16.4M   493G     16.4M  /mnt/usr/local
rpool/ROOT/ubuntu_uxtu99/var                      5.22G   493G       96K  /mnt/var
rpool/ROOT/ubuntu_uxtu99/var/lib                  4.58G   493G     4.40G  /mnt/var/lib
rpool/ROOT/ubuntu_uxtu99/var/lib/AccountServices    96K   493G       96K  /mnt/var/lib/AccountServices
rpool/ROOT/ubuntu_uxtu99/var/lib/NetworkManager    376K   493G      376K  /mnt/var/lib/NetworkManager
rpool/ROOT/ubuntu_uxtu99/var/lib/apt              82.2M   493G     82.2M  /mnt/var/lib/apt
rpool/ROOT/ubuntu_uxtu99/var/lib/dpkg              103M   493G      103M  /mnt/var/lib/dpkg
rpool/ROOT/ubuntu_uxtu99/var/log                   616M   493G      616M  /mnt/var/log
rpool/ROOT/ubuntu_uxtu99/var/mail                   96K   493G       96K  /mnt/var/mail
rpool/ROOT/ubuntu_uxtu99/var/spool                36.4M   493G     36.4M  /mnt/var/spool
rpool/USERDATA                                     405G   493G       96K  /mnt
rpool/USERDATA/ncr_mk6ljb                          405G   493G      319G  /mnt/home/ncr
rpool/USERDATA/root_mk6ljb                        18.8M   493G     14.1M  /mnt/root
root@ubuntu:~# zfs mount -a
root@ubuntu:~# mount --rbind /dev  /mnt/dev
root@ubuntu:~# mount --rbind /proc /mnt/proc
root@ubuntu:~# mount --rbind /sys  /mnt/sys
root@ubuntu:~# chroot /mnt /bin/bash --login
root@ubuntu:/# ls
bin   BpoolClean.sh  dev  hab   keybase  lib64   media  opt   root  sbin  srv  system       tmp  var
boot  cdrom          etc  home  lib      libx32  mnt    proc  run   snap  sys  system-info  usr
root@ubuntu:/# ls /boot/efi
root@ubuntu:/# ls /b
bin/  boot/ 
root@ubuntu:/# ls /boot/
boot/                         initrd.img                    memtest86+.elf                vmlinuz-5.15.0-25-generic
config-5.15.0-25-generic      initrd.img-5.15.0-25-generic  memtest86+_multiboot.bin      vmlinuz-5.15.0-50-generic
config-5.15.0-50-generic      initrd.img-5.15.0-50-generic  System.map-5.15.0-25-generic  vmlinuz-5.15.0-52-generic
config-5.15.0-52-generic      initrd.img-5.15.0-52-generic  System.map-5.15.0-50-generic  vmlinuz.old
efi/                          initrd.img.old                System.map-5.15.0-52-generic  
grub/                         memtest86+.bin                vmlinuz                       
root@ubuntu:/# grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --recheck --no-floppy
Installing for x86_64-efi platform.
grub-install: error: unknown filesystem.
```

In the interest of accelerating this process, I can make myself available at a specific time on an irc channel or element messenger or ..? Communicating in realtime might be beneficial.

This is nuts but I'm not sure exactly what is wrong:
/boot/boot/
/boot/efi/ [empty]
/boot/grub/ (fonts  gfxblacklist.txt  grub.cfg  grubenv  i386-pc  locale  unicode.pf2)
/boot/*initrd*vmlinuz*
/boot/boot/efi/ [empty]
/boot/boot/grub/ (fonts  grub.cfg  grubenv  locale  x86_64-efi)
/boot/boot/*initrd*vmlinuz*

[https://termbin.com/enod](https://termbin.com/enod)

```
sudo grub-probe -d /dev/sda1
sudo: unable to resolve host ubuntu: Name or service not known
fat
```

Can you post the grub-install command from your VM with verbose option please?

```
root@ubuntu:/# grub-install -v --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --recheck --no-floppy
Installing for x86_64-efi platform.
grub-install: info: cannot open `/boot/grub/device.map': No such file or directory.
grub-install: info: /dev/sda6 is not present.
grub-install: info: Looking for /dev/sda6.
grub-install: info: /dev/sda is a parent of /dev/sda6.
grub-install: info: /dev/sda6 starts from 9445376.
grub-install: info: opening the device hostdisk//dev/sda.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1953525168.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1953525168.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Partition 0 starts from 2048.
grub-install: info: Partition 4 starts from 5249024.
grub-install: info: Partition 5 starts from 9445376.
grub-install: info: /dev/sda6 is present.
grub-install: info: Looking for /dev/sda6.
grub-install: info: /dev/sda is a parent of /dev/sda6.
grub-install: info: /dev/sda6 starts from 9445376.
grub-install: info: opening the device hostdisk//dev/sda.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1953525168.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1953525168.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Partition 0 starts from 2048.
grub-install: info: Partition 4 starts from 5249024.
grub-install: info: Partition 5 starts from 9445376.
grub-install: info: /dev/sda6 is present.
grub-install: info: Looking for /dev/sda6.
grub-install: info: /dev/sda is a parent of /dev/sda6.
grub-install: info: /dev/sda6 starts from 9445376.
grub-install: info: opening the device hostdisk//dev/sda.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1953525168.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1953525168.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Scanning for DISKFILTER devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid1x devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09_be devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for mdraid09 devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for dmraid_nv devices on disk hostdisk//dev/sda.
grub-install: info: Scanning for ldm devices on disk hostdisk//dev/sda.
grub-install: info: scanning hostdisk//dev/sda for LDM.
grub-install: info: no LDM signature found.
grub-install: info: Scanning for lvm devices on disk hostdisk//dev/sda.
grub-install: info: no LVM signature found.
grub-install: info: Partition 0 starts from 2048.
grub-install: info: Partition 4 starts from 5249024.
grub-install: info: Partition 5 starts from 9445376.
grub-install: info: drive = 0.
grub-install: info: the size of hostdisk//dev/sda is 1953525168.
grub-install: error: unknown filesystem.
```

---

### Post by MAFoElffen on 2022-10-28
As requested: [https://paste.ubuntu.com/p/7hBGKnPnZd/](https://paste.ubuntu.com/p/7hBGKnPnZd/)

---

### Post by anystupidassname on 2022-10-29
Thanks but I'm lost. Is there another way to do this?

---

### Post by MAFoElffen on 2022-10-29
The difference is, after I do my chroot into it, then I do
```

mount -a  # Which remounts everything in the /etc/fstab file, such as the ESM EFI partition into /boot/EFI

```
That is why I do (after that)
```

ls /boot/efi/
ls /boot/efi/ubuntu

```
And to make sure the boot partitions are mounted before I try to reinstall grub...

When it says "unknown filesystem" as your error, that is a hint that the mounts are wrong...

Are there different ways? Yes, there are 4 different ways.
- Remove/Purge the newest kernel, then install it.
- Let 'boot-repair' repair it.
- Select the latest ZSys "rollback snapshot" to roll back to, which you say is about a year old.
- Install new and migrate what you backed up to the new install.

---

### Post by player-001 on 2022-10-30
Hello!

This thread is really valuable, thanks for sharing the knowledge. @MAFoElffen.  Unfortunately it gets a little convoluted and could be easier to understand.

I am quite interested in:

1. The proper care and feeding for how to support an ubuntu on zfs system that uses zsys.  I've run into similar problems in the past and managed to recover, but what's the official way to monitor and clean up a full bpool partition?  How often should this be performed?

2. Ubuntu on zfs system recovery.  What's the procedure to repair boot partitions, kernel, grub, etc to make a system with existing rpool/ROOT & rpool/USERDATA filesystems?

It would be great to document these procedures in the generalized use-case and sticky the instructions here in the forum, and add to various findable web help resources.

Thanks!

---

### Post by anystupidassname on 2022-10-30
> **MAFoElffen said:**
> The difference is, after I do my chroot into it, then I do
```

mount -a  # Which remounts everything in the /etc/fstab file, such as the ESM EFI partition into /boot/EFI

```
That is why I do (after that)
```

ls /boot/efi/
ls /boot/efi/ubuntu

```
And to make sure the boot partitions are mounted before I try to reinstall grub...
When it says "unknown filesystem" as your error, that is a hint that the mounts are wrong...

rerunning zfs mount -a appears to do away with the  "unknown filesystem" error.

> Remove/Purge the newest kernel, then install it.

apt purge kernel and apt install kernel behaved as expected and the grub boot menu now shows that it is trying to boot the correct kernel but drops directly to emergency mode still (even faster).
Additionally, the rollback snapshots entries are no longer available.

> Let 'boot-repair' repair it.
Doesn't appear to be an option. Sorry, I mentioned it in the [askubuntu]("https://askubuntu.com/questions/1435307/booting-to-emergency-mode-after-20-04-5-focal-to-22-04-jammy-upgrade") and thought you saw it but it demands to be booted to UEFI mode [IMG]https://imgur.com/jBwQTlK[/IMG] 
I created a new bootinfo in case it has changed since the last one. [https://paste.ubuntu.com/p/R3hHb5GGJG/](https://paste.ubuntu.com/p/R3hHb5GGJG/)

> Select the latest ZSys "rollback snapshot" to roll back to, which you say is about a year old.

These are no longer listed in grub boot menu but would not have been useful to me.
 
> Install new and migrate what you backed up to the new install.

Still not really an option for me.

---

### Post by anystupidassname on 2022-10-30
> **player-001 said:**
> Hello!

This thread is really valuable, thanks for sharing the knowledge. @MAFoElffen.  Unfortunately it gets a little convoluted and could be easier to understand.

I am quite interested in:

1. The proper care and feeding for how to support an ubuntu on zfs system that uses zsys.  I've run into similar problems in the past and managed to recover, but what's the official way to monitor and clean up a full bpool partition?  How often should this be performed?

2. Ubuntu on zfs system recovery.  What's the procedure to repair boot partitions, kernel, grub, etc to make a system with existing rpool/ROOT & rpool/USERDATA filesystems?

It would be great to document these procedures in the generalized use-case and sticky the instructions here in the forum, and add to various findable web help resources.

Thanks!

Piggybacking onto this thread will only make it more convoluted. Perhaps you could create a new thread instead?

I had intended to create a "simplified" how-to *IF* I was able to fix my system. Currently, this thread has not accomplished its goal yet.

Also, bear in mind that people's systems can vary significantly. The howto would need to be worded carefully and accommodate differences and not cause breakage.
Boot hardware: BIOS/UEFI/BOTH, Boot managers:GRUB-PC/GRUB-EFI/REFIND/ZFSBOOTMENU/LILO/ELILO....? , FS: GPT/MBR/ESP/legacy boot partitions, pools&dataset layouts: bpool/rpool, OS/DISTRO and whatever else I have not considered...

---

### Post by MAFoElffen on 2022-10-30
For reinstall grub, after I make the mount, I list the contents of /boot/efi and /boot/efi/ubuntu to enusre they are not empty...

Then do
```

DISK=$(fdisk -l | \
    grep '^/dev/' | \
    grep 'boot' | \
    head -n 1 | \
    awk '{print $1}' | \
    sed 's/\/dev\///g' | \
    cut -b -3 )

grub-install $DISK

grub-install --target=x86_64-efi --efi-directory=/boot/efi \
    --bootloader-id=ubuntu --recheck --no-floppy

```
Try that so it installs grub and dual arch/boot...

---

### Post by player-001 on 2022-10-31
> **anystupidassname said:**
> Piggybacking onto this thread will only make it more convoluted. Perhaps you could create a new thread instead?.

Didn't intend to piggyback, hijack, or complexify your support request in any way.  Was more asking for a separate thread or article to be published that lays out zfs on linux system recovery in a way that would help as many people as possible and avoid confusing configuration-specific rabbit-holes that make a complex topic even more so.

I know it's a big ask.  I just see many of the pieces of the puzzle for how a zfs system could be made bootable again and think laying this out in a nice clear straightforward way in a publicly accessible place would be really helpful to the community.

---

### Post by anystupidassname on 2022-10-31
> **MAFoElffen said:**
> For reinstall grub, after I make the mount, I list the contents of /boot/efi and /boot/efi/ubuntu to enusre they are not empty...

Then do
```

DISK=$(fdisk -l | \
    grep '^/dev/' | \
    grep 'boot' | \
    head -n 1 | \
    awk '{print $1}' | \
    sed 's/\/dev\///g' | \
    cut -b -3 )

grub-install $DISK

grub-install --target=x86_64-efi --efi-directory=/boot/efi \
    --bootloader-id=ubuntu --recheck --no-floppy

```
Try that so it installs grub and dual arch/boot...

$DISK is empty/blank.

This is slowly driving me insane. Have you seen this? [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1893964](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1893964)

We may be close because, last time the grub menu was updated (finally - although I lost the snapshots...), and now there is no grub menu at all. It grinds on the SSD for about 10 full seconds, flashes the Xubuntu logo (?!?) for a millisecond and drops to the emergency mode.

Here are the screenshots of the relevant passage.
ibb.co/5LbmggV
ibb.co/rFTfNgQ

What should be in /boot/efi/ubuntu? Because there is never anything there.

EDIT: OK, the grub menu is back but still not booting. Keeps dumping to emergency mode. I think the key is that the efi/ubuntu folder you're talking about actually seems to be under /boot/efi/EFI/grub/ubuntu or something equally weird. Isn't there a *safe* way to remove ESP entirely and use a bios_grub partition or..?

EDIT2: After trying this, [https://ggirelli.info/blog/2022/08/28/ubuntu-grub-zfs](https://ggirelli.info/blog/2022/08/28/ubuntu-grub-zfs), it looked like it would boot for a few seconds. But it ended up at emergency mode again after about 100 lines...

set root=(hd0,msdos5)
linux /BOOT/ubuntu_uxtu99/@/vmlinuz root=ZFS=rpool/ROOT/ubuntu_uxtu99 boot=zfs
initrd /BOOT/ubuntu_uxtu99/@/initrd.img 
boot

---

### Post by MAFoElffen on 2022-10-31
I sent you some PM's on the latest revisions to my script to Yann, it adjusts the Algorithm filter for $DISK based on the output of 'fdisk -l" on your machine. Before doing this with "you", I didn't know that was a variant of this, or that it "could" happen. Thank you for helping me with that.

Please check to see if that updated algorithm filter populates $DISK...

---

### Post by anystupidassname on 2022-11-02
Identifying the boot disk/partition may be useful for the script in future scenarios for other people's broken systems which is all well and good, but we know which disk/partition to install grub to on this system. We've tried them all, even. This still isn't returning this system to a bootable status. What are we missing? I'm starting to lose hope after 2 weeks of getting nowhere. This shouldn't be so complicated and difficult.

---

### Post by MAFoElffen on 2022-11-02
Going through your posts, I didn't see you mount, chroot and do 
```

grub-install /dev/sda

```
Which would be the install of grub to Legacy BIOS boot... Or am I wrong with that?

---

### Post by anystupidassname on 2022-11-02
Yea, I guess it isn't anywhere in this thread. It was in one of the asciinema recordings and it appears to succeed in the same way as when you do it in your VM. 

> 
root@ubuntu:/# grub-install /dev/$DISK
Installing for i386-pc platform.
                                                                                                                                                    Installation finished. No error reported.
                                                                                                                                           root@ubuntu:/# grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --recheck --no-floppy
                                                              Installing for x86_64-efi platform.                                                                                                                                                 grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.

EDIT: I forgot to mention that your latest addition of tmpfs line before chroot seems to cause problems with DNS and apt inside chroot.

---

### Post by MAFoElffen on 2022-11-02
Try this right after that line:
```

mount --bind /etc/resolv.conf /mnt/etc/resolv.conf

```

---

### Post by anystupidassname on 2022-11-03
The new script runs without errors. We're basically just repeating the same steps over and over here. Machine still not bootable.

---

### Post by MAFoElffen on 2022-11-03
So it fails on Linux Kernel 5.15.0-50 right?

Current in main is 5.15.0-52-generic... What happens if you try to boot the last before Linux Kernel 5.15.0-50 from the Grub Menu? 

What happens if you remove the problem kernel and install the latest?
```

sudo dpkg &#8211;&#8211;purge linux-image-5.15.0-50-generic
sudo apt install linux-image-5.15.0-52-generic

```

---

### Post by anystupidassname on 2022-11-05
No change. Check PM please. The only thing I can tell from the emergency console, is that it says it cannot mount the bpool.

---

### Post by MAFoElffen on 2022-11-05
Dang. Yes. I looked at what you where doing.

And it still does not boot on it's own? That doesn't make sense. 

Then it says that the ZSys daemon is not present... You reinstalled that right? And it is enabled right?

---

### Post by anystupidassname on 2022-11-06
> **MAFoElffen said:**
> Dang. Yes. I looked at what you where doing.

And it still does not boot on it's own? That doesn't make sense. 

Then it says that the ZSys daemon is not present... You reinstalled that right? And it is enabled right?

This seems like it should work, which is why it is driving me insane. I'm having trouble just dropping it and moving on because if this kind of crap can keep happening, I have no business even using a computer...

Well, I tried with and without zsys installed. The errors are present when zsys is installed. I suspect zsys requires systemd to work which doesn't in chroot.
I didn't think zsys was required and thus not a reason for failure? Am I wrong?!

(side note, I just remembered, the $DISK variable in your script doesn't survive the chroot so you'll have to find a way to workaround that -  u probably saw that in the recording anyway)

---

### Post by MAFoElffen on 2022-11-06
No... ZSys was something that was installed in 20.04, but is no longer used with 22.04. So it is something you no longer need. 

Yes. I saw that $DISK does not survive the chroot. It's one of those things that I usually write down to remember what to type later.

There is something I am not understanding, seeing or overlooking. It seems like it should work. Maybe I should ask for another set of eyes. LOL

---

### Post by #&amp;thj^% on 2022-11-06
> **anystupidassname said:**
> grub-install and update-grub fail. So the system doesn't boot. initramfs doesn't get called because there is no newer kernel I think.

I was asked to take a look at this thread, and I may have missed some important details here, so I'll ask Are you using separate bpool for /boot ?  If so, make sure that it's properly mounted in rpool/ROOT/utl (/), otherwise update-grub won't be able to locate kernel and initrd image files correctly.

---

### Post by anystupidassname on 2022-11-06
> **1fallen said:**
> I was asked to take a look at this thread, and I may have missed some important details here, so I'll ask Are you using separate bpool for /boot ?  If so, make sure that it's properly mounted in rpool/ROOT/utl (/), otherwise update-grub won't be able to locate kernel and initrd image files correctly.

The partition / pool / dataset layout was created/determined by the focal 20.04 installer when I chose openzfsonroot.
"do-release-upgrade" to jammy 22.04 broke boot silently.

I think you're using shorthand for something, but I don't understand "rpool/ROOT/utl"

How can I verify the bpool is mounted where? Do you need this information for inside chroot or outside? I'll provide it.

These posts in this thread show what things are mounted where: (most recent first)
[https://ubuntuforums.org/showthread.php?t=2480236&p=14117279#post14117279](https://ubuntuforums.org/showthread.php?t=2480236&p=14117279#post14117279)
[https://ubuntuforums.org/showthread.php?t=2480236&p=14117028#post14117028](https://ubuntuforums.org/showthread.php?t=2480236&p=14117028#post14117028)
[https://ubuntuforums.org/showthread.php?t=2480236&p=14116798#post14116798](https://ubuntuforums.org/showthread.php?t=2480236&p=14116798#post14116798)

I've been trying to work from this and what [**[COLOR=#DD4814][B]MAFoElffen**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1044547") has told me:
[https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2022.04%20Root%20on%20ZFS.html#step-5-grub-installation](https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2022.04%20Root%20on%20ZFS.html#step-5-grub-installation)

Thanks for your assistance.

---

### Post by #&amp;thj^% on 2022-11-06
> **anystupidassname said:**
> 
I think you're using shorthand for something, but I don't understand "rpool/ROOT/utl"


Sorry about that, and thanks for pointing that out I work a lot with Developer's so my text at times reflects that, I'll simplify that in my next post's.
Give me some time to absorb what has been written in this thread.
But use:
```
zfs list
```
And I can see this much early on:
```
bpool  1.88G   244M  1.64G        -         -     0%    12%  1.00x    ONLINE  /mnt/boot
rpool  33.5G  6.20G  27.3G        -         -     2%    18%  1.00x    ONLINE  /mnt
```

---

### Post by #&amp;thj^% on 2022-11-06
So just to clear somethings up Here, Is this a non UEFI install AKA Legacy?
I need to know before offering anything./ Here's why, Legacy file systems must be managed through the mount and umount commands and the /etc/vfstab file. ZFS does not automatically mount legacy file systems at boot time, and the ZFS mount and umount commands do not operate on datasets of this type.

---

### Post by anystupidassname on 2022-11-06
> **1fallen said:**
> So just to clear somethings up Here, Is this a non UEFI install AKA Legacy?
I need to know before offering anything./ Here's why, Legacy file systems must be managed through the mount and umount commands and the /etc/vfstab file. ZFS does not automatically mount legacy file systems at boot time, and the ZFS mount and umount commands do not operate on datasets of this type.

Affirmative, this is a Thinkpad T410 which has a NON UEFI capable BIOS. AKA legacy
That said, the focal installer created the layout (1 primary fat ESP, 1 extended partition with 2 logical partitions for bpool and rpool) so EFI is the uninvited guest at the party.
This is what the emergency console says after trying to boot. I suspect the "unable to mount /boot" is the key here, but don't know what to do about it.
[https://ibb.co/zWM3Nkd](https://ibb.co/zWM3Nkd)
[https://ibb.co/VDRc2zv](https://ibb.co/VDRc2zv)
[https://ibb.co/6JWgdvF](https://ibb.co/6JWgdvF)

---

### Post by #&amp;thj^% on 2022-11-06
Ok great, and if you wouldn't mind can we keep it all here in this thread? You have Two threads which not a good thing.
To automatically mount a legacy file system at boot time, you must add an entry to the /etc/vfstab file. are you able to show those contents here:
```
cat  /etc/vfstab
```
Here is a quick example of what it should look like:
```
#device         device        mount           FS      fsck    mount   mount
#to mount       to fsck       point           type    pass    at boot options
#

tank/home/eschrock -		/mnt		   zfs		-		yes		-	
```

---

### Post by anystupidassname on 2022-11-06
dereted for readability

---

### Post by #&amp;thj^% on 2022-11-06
> **anystupidassname said:**
> Should bootfs be "on"?

Please stay current with my questions it's hard enough to stay focused on what you have now. :)
bpool is always active, that dose not mean it's on or mounted to the OS.

---

### Post by anystupidassname on 2022-11-06
> **1fallen said:**
> Ok great, and if you wouldn't mind can we keep it all here in this thread? You have Two threads which not a good thing.
To automatically mount a legacy file system at boot time, you must add an entry to the /etc/vfstab file. are you able to show those contents here:
```
cat  /etc/vfstab
```

The other thread does not pertain to this one.

Inside chroot, /etc/vfstab does not exist, and has never existed to the best of my knowledge.
If you'd like me to create one, can you tell me how to compose it properly?

P.S. I was writing the previous post at the same time as you were writing yours :(
P.P.S. If it would be easier for you, I'm happy to use any other method of communication such as IRC or element or whatever. (maybe not smoke signals..)

---

### Post by #&amp;thj^% on 2022-11-06
I'm having a rough time finding the root cause of all this.
I'm going to coffee up here, stay tuned. ;)
Well that answers that then>>>" (maybe not smoke signals..) "LOL

---

### Post by #&amp;thj^% on 2022-11-06
BTW have you been instructed to run this yet?
```
sudo zpool resilver {pool}
```
What it does "A resilver is an automatic dynamic consistency restoration run after a disk or network failure or slowdown of one or more mirrors. "
I'm going to be offline for short time, about an *hour give or take* sorry for any inconvenience. I have other obligations to handle.
I'll be back.

---

### Post by anystupidassname on 2022-11-06
> **1fallen said:**
> BTW have you been instructed to run this yet?
```
sudo zpool resilver {pool}
```
What it does "A resilver is an automatic dynamic consistency restoration run after a disk or network failure or slowdown of one or more mirrors. "
I'm going to be offline for short time, about an *hour give or take* sorry for any inconvenience. I have other obligations to handle.
I'll be back.

OK, no problem. I'm going for a quick dinner too.

I have not tried a resilver. Should I run "zpool resilver bpool/?what?

Didier Roche ([https://github.com/didrocks](https://github.com/didrocks)) is apparently responsible for the way openzfs on root is setup on ubuntu.
While looking for solutions, I'm finding a lot of bugs similar to this [https://github.com/ubuntu/zsys/issues/60](https://github.com/ubuntu/zsys/issues/60)
and this [https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/1867007/comments/6](https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/1867007/comments/6) online.
/boot doesn't mount properly during boot either because it thinks it isn't empty or something to do with the zfs cache files?

---

### Post by #&amp;thj^% on 2022-11-06
Yep just had a real quick peek and chat there.
> The boot pool has a mountpoint of /boot so that child datasets (created by the admin, not the HOWTO) would inherit nice mountpoints. This comes from the Ubuntu installer design, so I don't intend to change it.
Before you do though I needed to see if this setting was true < **Note that bpool is canmount=off**>
See ya after quick break here.

---

### Post by anystupidassname on 2022-11-06
> **1fallen said:**
> Yep just had a real quick peek and chat there.

Before you do though I needed to see if this setting was true < **Note that bpool is canmount=off**>
See ya after quick break here.

OK, so you're asking me to resilver and find out if bpool is canmount=off ?
I'll try to figure out how to do both of those.

---

### Post by #&amp;thj^% on 2022-11-06
> **anystupidassname said:**
> OK, so you're asking me to resilver and find out if bpool is canmount=off ?

I thought I mentioned not just yet, but I can see the confusion here, I was affirming the bugs on ZFS/Ubuntu
Anyway they should be seen in " **zfs get all zroot/usr** and **zfs get all zroot/ROOT/default**"

---

### Post by MAFoElffen on 2022-11-06
Got most of my wife chores done...

I remmber seeing him PM me a recording of the fstab file from the install... but fleeting as a recording, not as a post yet. If I look back at the system-info report he ran, he didn't run that "while" chrooted into the system... And if he did run that while chrooted in "AND" used 
```

system-info -d

```
... as the startup option, it will print out the fstab info and extra ZFS pool info in that report.

I'm thinking, that for some reason, it is still not mounting boot.

Ubuntu 20.04 LTS with ZFS-On-Root does a dual boot with Grub, installed as both UEFI and CSM/Legacy... So it has a separate boot partition, which it should mount as /boot/, then a seprate ESP partition that it should mount as /boot/EFI... So the /etc/fstab file should have those 3 lines...

Just thinking out loud.


*** And I made sure he backed up everything before he even started, so he can still go back to whatever was there. Nothing should be lost.

---

### Post by #&amp;thj^% on 2022-11-06
> **MAFoElffen said:**
> Got most of my wife chores done...

I remmber seeing him PM me a recording of the fstab file from the install... but fleeting as a recording, not as a post yet. If I look back at the system-info report he ran, he didn't run that "while" chrooted into the system... And if he did run that while chrooted in "AND" used 
```

system-info -d

```
... as the startup option, it will print out the fstab info and extra ZFS pool info in that report.

I'm thinking, that for some reason, it is still not mounting boot.

Ubuntu 20.04 LTS with ZFS-On-Root does a dual boot with Grub, installed as both UEFI and CSM/Legacy... So it has a separate boot partition, which it should mount as /boot/, then a seprate ESP partition that it should mount as /boot/EFI... So the /etc/fstab file should have those 3 lines...

Just thinking out loud.

I like it when you think out loud, that's exactly what we want to see here..;)
I still have a few Devs that have me on perma-hold so bare with me on timely reply's.
*** And I made sure he backed up everything before he even started, so he can still go back to whatever was there. Nothing should be lost.
I like it when you think out loud, that's exactly what we want to see here..;)
I still have a few Devs that have me on perma-hold so bare with me on timely reply's.
And Dude you Rock!>>>"*** And I made sure he backed up everything before he even started, so he can still go back to whatever was there. Nothing should be lost."

---

### Post by anystupidassname on 2022-11-06
> **1fallen said:**
> I thought I mentioned not just yet, but I can see the confusion here, I was affirming the bugs on ZFS/Ubuntu
Anyway they should be seen in " **zfs get all zroot/usr** and **zfs get all zroot/ROOT/default**"

Is this what you're asking for? (forums can't handle this amount of text apparently)

[https://termbin.com/fxxi](https://termbin.com/fxxi)

[https://termbin.com/712j0](https://termbin.com/712j0)

[https://termbin.com/15d0](https://termbin.com/15d0)

I have not resilvered yet. Do you still want me to?

This will likely be the last operation I can do tonight and I won't be able to work on this again until tomorrow evening.

Thanks for your help.

---

### Post by #&amp;thj^% on 2022-11-06
> **anystupidassname said:**
> Is this what you're asking for? (forums can't handle this amount of text apparently)

[https://termbin.com/fxxi](https://termbin.com/fxxi)

[https://termbin.com/712j0](https://termbin.com/712j0)

[https://termbin.com/15d0](https://termbin.com/15d0)

I have not resilvered yet. Do you still want me to?

This will likely be the last operation I can do tonight and I won't be able to work on this again until tomorrow evening.

Thanks for your help.
Yes this is it, good job.
this I need to think about:
```
rpool/ROOT/ubuntu_uxtu99/usr  com.ubuntu.zsys:bootfs              no                                  local
rpool/ROOT/ubuntu_uxtu99/usr  com.ubuntu.zsys:last-booted-kernel  vmlinuz-5.4.0-39-generic            inherited from rpool/ROOT/ubuntu_uxtu99
rpool/ROOT/ubuntu_uxtu99/usr  com.ubuntu.zsys:last-used           1610198601                          inherited from rpool/ROOT/ubuntu_uxtu99

```
But we can resume tomorrow, my time zone now is 3:.08 PM>>>>is this a good time for you?

---

### Post by anystupidassname on 2022-11-06
> **MAFoElffen said:**
> Got most of my wife chores done...

I remmber seeing him PM me a recording of the fstab file from the install... but fleeting as a recording, not as a post yet. If I look back at the system-info report he ran, he didn't run that "while" chrooted into the system... And if he did run that while chrooted in "AND" used 
```

system-info -d

```
... as the startup option, it will print out the fstab info and extra ZFS pool info in that report.

I'm thinking, that for some reason, it is still not mounting boot.

Ubuntu 20.04 LTS with ZFS-On-Root does a dual boot with Grub, installed as both UEFI and CSM/Legacy... So it has a separate boot partition, which it should mount as /boot/, then a seprate ESP partition that it should mount as /boot/EFI... So the /etc/fstab file should have those 3 lines...

Just thinking out loud.


*** And I made sure he backed up everything before he even started, so he can still go back to whatever was there. Nothing should be lost.

There *IS* an fstab, but NOT a vfstab. Is there some confusion here?

```
root@ubuntu:/# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
UUID=7D37-A683    /boot/efi    vfat    umask=0022,fmask=0022,dmask=0022    0    1
/boot/efi/grub    /boot/grub    none    defaults,bind    0    0
##UUID=72e3d19f-b61e-4212-90d2-f6e333a3c4f7    none    swap    discard    0    0
```

I already described the partition layout but a picture is worth 1000 words or something like that:
[https://ibb.co/10YndxV](https://ibb.co/10YndxV)

---

### Post by anystupidassname on 2022-11-06
> **1fallen said:**
> Yes this is it, good job.
this I need to think about:
```
rpool/ROOT/ubuntu_uxtu99/usr  com.ubuntu.zsys:bootfs              no                                  local
rpool/ROOT/ubuntu_uxtu99/usr  com.ubuntu.zsys:last-booted-kernel  vmlinuz-5.4.0-39-generic            inherited from rpool/ROOT/ubuntu_uxtu99
rpool/ROOT/ubuntu_uxtu99/usr  com.ubuntu.zsys:last-used           1610198601                          inherited from rpool/ROOT/ubuntu_uxtu99

```
But we can resume tomorrow, my time zone now is 3:.08 PM>>>>is this a good time for you?

I'm UTC+2 and I guess you're -8 so probalby west coast or something like that?
It is coming up on midnight here now. Earlier would be better, but this is important so I'll make it happen any way I can.

Can you confirm you want me to run "zfs resilver rpool && zfs resilver bpool" at this time?

---

### Post by #&amp;thj^% on 2022-11-06
The " vfstab" was my way of checking the system installed on and No big deal now.
All is good. ;)

---

### Post by #&amp;thj^% on 2022-11-06
> **anystupidassname said:**
> I'm UTC+2 and I guess you're -8 so probalby west coast or something like that?
It is coming up on midnight here now. Earlier would be better, but this is important so I'll make it happen any way I can.

Can you confirm you want me to run "zfs resilver rpool && zfs resilver bpool" at this time?

 Earlier would be better here as well.
> **anystupidassname said:**
> 
Can you confirm you want me to run "zfs resilver rpool && zfs resilver bpool" at this time?
Wait till I read through the system-info, so tomorrow then Ok?

---

### Post by anystupidassname on 2022-11-06
> **1fallen said:**
> Earlier would be better here as well.

Wait till I read through the system-info, so tomorrow then Ok?

OK, ready when you are.

EDIT: OK, I guess something came up, I'll check in on Tuesday.

---

### Post by MAFoElffen on 2022-11-08
Does bpool/BOOT/ubuntu_uxtu99 still exist? Please post (while chroot'ed in)
```

sudo zfs list bpool
sudo zfs mount

```
You can mount everything manually, and do a chroot, and everthing appears as if it is wired together correctly... But it's still not "somewhere..." It's not mounting the filesystem and putting it back together correctly on it's own.

There's two parts of that. One is the fstab and it's mounts, which look to be okay. Second is the ZFS mounts which, honestly, it's been over 15 years since I've had problems of having to dig through ZFS mounting problems. And Solaris ZFS filesystem mounts are different than ZFS on Linux. They don't have bpools (just rpools). They are a lot simpler and basic. I'm going to have to look up how those are wired together internally and try to break and fix them, to see what is possible.

I mean I do ZFS mounts to add created ZFS pools for Home directories, File Shares, and Database pools... And I know how to rename pools... And during my migrations, I just import my old "home" pools into the new installs... I'm wondering if I can rename a bpool as the missing pool's serial import it and make it work... or tell it to use a newer or older bpool if a snapshot is missing. ...to get yours back working.

Like I said in your other thread, yesterday I spun up some Ubuntu 22.04 ZFS instances and have been trying different thing with them...

EDIT: That's okay. The extra work is helping me update and rewrite the scripts I had on ZFS for the Ama-Gi Project. And to work out possibilities of things to add to 'boot-info' for Yann. LOL.

---

### Post by anystupidassname on 2022-11-09
> **MAFoElffen said:**
> Does bpool/BOOT/ubuntu_uxtu99 still exist? Please post (while chroot'ed in)
```

sudo zfs list bpool
sudo zfs mount

```
You can mount everything manually, and do a chroot, and everthing appears as if it is wired together correctly... But it's still not "somewhere..." It's not mounting the filesystem and putting it back together correctly on it's own.

There's two parts of that. One is the fstab and it's mounts, which look to be okay. Second is the ZFS mounts which, honestly, it's been over 15 years since I've had problems of having to dig through ZFS mounting problems. And Solaris ZFS filesystem mounts are different than ZFS on Linux. They don't have bpools (just rpools). They are a lot simpler and basic. I'm going to have to look up how those are wired together internally and try to break and fix them, to see what is possible.

Here are the results to the two commands you requested:
[https://termbin.com/oxg0r](https://termbin.com/oxg0r)
[https://termbin.com/06hi](https://termbin.com/06hi)

> I mean I do ZFS mounts to add created ZFS pools for Home directories, File Shares, and Database pools... And I know how to rename pools... And during my migrations, I just import my old "home" pools into the new installs... I'm wondering if I can rename a bpool as the missing pool's serial import it and make it work... or tell it to use a newer or older bpool if a snapshot is missing. ...to get yours back working.

Like I said in your other thread, yesterday I spun up some Ubuntu 22.04 ZFS instances and have been trying different thing with them...

EDIT: That's okay. The extra work is helping me update and rewrite the scripts I had on ZFS for the Ama-Gi Project. And to work out possibilities of things to add to 'boot-info' for Yann. LOL.

I appreciate the efforts. I wish I knew more and could figure this out on my own.

---

### Post by MAFoElffen on 2022-11-09
[quote=anystupidname]```

rpool/ROOT/ubuntu_uxtu99        /
[COLOR=#ff0000]bpool/BOOT/ubuntu_uxtu99        /boot[/COLOR]
rpool/USERDATA/ncr_mk6ljb       /home/ncr
rpool/USERDATA/root_mk6ljb      /root
rpool/ROOT/ubuntu_uxtu99/var/lib  /var/lib
rpool/ROOT/ubuntu_uxtu99/var/log  /var/log
rpool/ROOT/ubuntu_uxtu99/usr/local  /usr/local
rpool/ROOT/ubuntu_uxtu99/var/spool  /var/spool
rpool/ROOT/ubuntu_uxtu99/var/lib/NetworkManager  /var/lib/NetworkManager
rpool/ROOT/ubuntu_uxtu99/var/lib/AccountServices  /var/lib/AccountServices
rpool/ROOT/ubuntu_uxtu99/var/mail  /var/mail
rpool/ROOT/ubuntu_uxtu99/var/lib/apt  /var/lib/apt
rpool/ROOT/ubuntu_uxtu99/var/lib/dpkg  /var/lib/dpkg
```[/quote]
In one of your link photo's from boot screen errors, it said it could not mount bpool/BOOT/ubuntu_uxtu99... But while you are manually mounted into it, it was mounted. Or at least from the above results, it appeared so. (???)

Post the results of this (while chrooted in):
```

zfs get mountpoint,mounted bpool -t filesystem -r
zpool events -v bpool
zpool history bpool


```
Here is what that looks like on one of mine... I think this is the info and perspective we are wanting to look from...
```

root@ubuntu--zfs-csm-02:/home/mafoelffen# zfs get mountpoint,mounted bpool -t filesystem -r
NAME                      PROPERTY    VALUE       SOURCE
bpool                     mountpoint  /boot       local
bpool                     mounted     no          -
bpool/BOOT                mountpoint  none        local
bpool/BOOT                mounted     no          -
bpool/BOOT/ubuntu_4thxnu  mountpoint  /boot       local
bpool/BOOT/ubuntu_4thxnu  mounted     yes         -
root@ubuntu--zfs-csm-02:/home/mafoelffen# zpool events -v bpool
TIME                           CLASS
Nov  8 2022 00:27:46.368000000 sysevent.fs.zfs.history_event
        version = 0x0
        class = "sysevent.fs.zfs.history_event"
        pool = "bpool"
        pool_guid = 0x59ded5e66266a929
        pool_state = 0x0
        pool_context = 0x0
        history_hostname = "ubuntu--zfs-csm-02"
        history_internal_str = "pool version 5000; software version zfs-2.1.4-0-g52bad4f23-dist; uts ubuntu--zfs-csm-02 5.15.0-52-generic #58-Ubuntu SMP Thu Oct 13 08:03:55 UTC 2022 x86_64"
        history_internal_name = "open"
        history_txg = 0x3b1
        history_time = 0x636a1302
        time = 0x636a1302 0x15ef3c00 
        eid = 0x6

Nov  8 2022 00:27:46.496000000 sysevent.fs.zfs.config_sync
        version = 0x0
        class = "sysevent.fs.zfs.config_sync"
        pool = "bpool"
        pool_guid = 0x59ded5e66266a929
        pool_state = 0x0
        pool_context = 0x0
        time = 0x636a1302 0x1d905c00 
        eid = 0x7

Nov  8 2022 00:27:46.496000000 sysevent.fs.zfs.pool_import
        version = 0x0
        class = "sysevent.fs.zfs.pool_import"
        pool = "bpool"
        pool_guid = 0x59ded5e66266a929
        pool_state = 0x0
        pool_context = 0x0
        time = 0x636a1302 0x1d905c00 
        eid = 0x8

Nov  8 2022 00:27:46.500000000 sysevent.fs.zfs.history_event
        version = 0x0
        class = "sysevent.fs.zfs.history_event"
        pool = "bpool"
        pool_guid = 0x59ded5e66266a929
        pool_state = 0x0
        pool_context = 0x0
        history_hostname = "ubuntu--zfs-csm-02"
        history_internal_str = "pool version 5000; software version zfs-2.1.4-0-g52bad4f23-dist; uts ubuntu--zfs-csm-02 5.15.0-52-generic #58-Ubuntu SMP Thu Oct 13 08:03:55 UTC 2022 x86_64"
        history_internal_name = "import"
        history_txg = 0x3b3
        history_time = 0x636a1302
        time = 0x636a1302 0x1dcd6500 
        eid = 0x9

Nov  8 2022 00:27:46.592000000 sysevent.fs.zfs.config_sync
        version = 0x0
        class = "sysevent.fs.zfs.config_sync"
        pool = "bpool"
        pool_guid = 0x59ded5e66266a929
        pool_state = 0x0
        pool_context = 0x0
        time = 0x636a1302 0x23493400 
        eid = 0xa

root@ubuntu--zfs-csm-02:/home/mafoelffen# zpool history bpool
History for 'bpool':
2022-11-07.23:35:22 zpool create -f -o ashift=12 -o autotrim=on -d -o feature@async_destroy=enabled -o feature@bookmarks=enabled -o feature@embedded_data=enabled -o feature@empty_bpobj=enabled -o feature@enabled_txg=enabled -o feature@extensible_dataset=enabled -o feature@filesystem_limits=enabled -o feature@hole_birth=enabled -o feature@large_blocks=enabled -o feature@lz4_compress=enabled -o feature@spacemap_histogram=enabled -O compression=lz4 -O acltype=posixacl -O xattr=sa -O relatime=on -O normalization=formD -O canmount=off -O devices=off -O mountpoint=/boot -R /target bpool /dev/disk/by-partuuid/44ce6ece-37f9-2542-880d-50dc19777fc0
2022-11-07.23:35:23 zfs create bpool/BOOT -o canmount=off -o mountpoint=none
2022-11-07.23:35:23 zfs create bpool/BOOT/ubuntu_4thxnu -o mountpoint=/boot
2022-11-07.23:48:08 zpool set cachefile= bpool
2022-11-08.00:05:26 zpool export bpool
2022-11-08.00:06:28 zpool import -c /etc/zfs/zpool.cache -aN
2022-11-08.00:27:46 zpool import -c /etc/zfs/zpool.cache -aN

```

---

### Post by anystupidassname on 2022-11-10
First command looks the same.
[https://termbin.com/mm1y](https://termbin.com/mm1y)

the events and history are quite a bit longer than yours but that makes sense..
[https://termbin.com/2i0g](https://termbin.com/2i0g)
[https://termbin.com/qvyx](https://termbin.com/qvyx)

I don't know if you're wanting for me to look for something in particular. I'm not seeing anything obviously useful to me.

I was however under the impression that canmount was supposed to be off which this seems to have changed:
"2022-11-06.15:46:41 zfs set canmount=on bpool/BOOT/ubuntu_uxtu99"

(I don't think I did this directly - was it a side effect of some of the troubleshooting we've been doing since it was 4 days ago)

---

### Post by MAFoElffen on 2022-11-10
Here's what I see from that:
```

2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_daily-2020-06-22-0819
2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_weekly-2020-06-20-0831
2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_a88wsc
2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_p0bujz
2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_r7nh1m
2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_s3shqy
2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_weekly-2020-06-13-0847
2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_zsihdd
2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_8ywnrh
2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_9njc9s
2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_8k0i0s
2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_8jfyyy
2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_ivet2r
2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_wal4es
2020-06-25.12:45:28 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_hc9z43
2020-06-25.12:45:28 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_z1jhlr
2020-06-25.12:45:28 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_ro6l0s
2020-06-25.12:45:28 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_k70miz
2020-06-25.12:45:28 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_5ujij3
2020-06-25.12:45:28 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_0edzqc
2020-06-25.12:45:28 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_sc3oh5
2020-06-25.12:45:28 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_4pe0gq
2020-06-25.12:45:28 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_035ael
2020-06-25.12:45:28 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_weekly-2020-06-06-1151
2022-10-25.12:55:50 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_daily-2020-06-25-0855
2022-10-25.12:55:50 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_daily-2020-06-26-1133
2022-10-25.12:55:50 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_daily-2020-06-28-0925
2022-10-25.12:55:50 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_weekly-2020-06-28-0930
2022-10-25.12:55:50 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_monthly-2020-06-28-0935
2022-10-25.12:55:50 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_daily-2020-06-29-0552
2022-10-25.12:55:50 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_hourly-2020-06-29-0817
2022-10-25.12:55:50 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_hourly-2020-06-29-0917
2022-10-25.12:55:50 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_hourly-2020-06-29-1317
2022-10-25.12:55:50 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_hourly-2020-06-29-1417
2022-10-25.12:55:50 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_hourly-2020-06-29-1617
2022-10-25.12:55:50 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_hourly-2020-06-29-1717
2022-10-25.12:55:50 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_frequent-2020-06-29-1800
2022-11-06.15:46:41 zfs set canmount=on bpool/BOOT/ubuntu_uxtu99

```
Let me think about this a bit before I say anything... It looks like you cleaned up a lot of snapshots from the current bpool's UUID... Then, well... Let me mull this over.

EDIT: Please after you chroot int to it, then rerun the 'system-info' script, using the '-d" startup flag and post the URL to the pastebin... I'm thinking if you install a newer kernel, that it will create a newer bpool/ubuntu_<UUID> and correct itself and all the internal mounts... then export it to save and shutdown the filesystem. I just need some info from that report to figure out which kernel to reommend, that will be replaced by normal updates (soon). Something like Linux Kernel 5.15.0-60 from the Ubuntu Mainline PPA...

---

### Post by MAFoElffen on 2022-11-10
Something like (while chrooted in, and replacing <user_name> with your own...):
```

cd /home/<user_name>/Downloads
mkdir ./mainline && mkdir ./mainline/v5.15.60
cd ./mainline/v5.15.60
wget -N -t 5 -T 10 https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.15.60/amd64/linux-headers-5.15.60-051560-generic_5.15.60-051560.202208110844_amd64.deb
wget -N -t 5 -T 10 https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.15.60/amd64/linux-headers-5.15.60-051560_5.15.60-051560.202208110844_all.deb
wget -N -t 5 -T 10 https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.15.60/amd64/linux-modules-5.15.60-051560-generic_5.15.60-051560.202208110844_amd64.deb
wget -N -t 5 -T 10 https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.15.60/amd64/linux-image-unsigned-5.15.60-051560-generic_5.15.60-051560.202208110844_amd64.deb
dpkg -i *.deb
exit
sudo zfs export bpool
sudo zfs export rpool
sudo reboot

```

---

### Post by #&amp;thj^% on 2022-11-11
Sorry, all I can say here is real life can just dominate my time as of late.
I need to read through all I've missed.
A good system will show:
```
zfs get mountpoint,mounted bpool -t filesystem -r
NAME                      PROPERTY    VALUE       SOURCE
bpool                     mountpoint  /boot       local
bpool                     mounted     no          -
bpool/BOOT                mountpoint  none        local
bpool/BOOT                mounted     no          -
bpool/BOOT/ubuntu_k65d6x  mountpoint  /boot       local
bpool/BOOT/ubuntu_k65d6x  mounted     yes         -


```
I flat hate snaps on a zfs root so that the first thing I dump. **_(NOTE: I'm not advising you to get rid of snapd)_**
I'll also change the memory allowed to zfs...but I'm getting ahead of myself here
In a nut shell here is my layout:
```
Partition:
  ID-1: / size: 222.76 GiB used: 4.24 GiB (1.9%) fs: zfs
    logical: rpool/ROOT/ubuntu_k65d6x
  ID-2: /boot size: 1.75 GiB used: 240.8 MiB (13.4%) fs: zfs
    logical: bpool/BOOT/ubuntu_k65d6x
  ID-3: /boot/efi size: 511 MiB used: 13.4 MiB (2.6%) fs: vfat
    dev: /dev/sdb1
  ID-4: /var/log size: 218.52 GiB used: 4.2 MiB (0.0%) fs: zfs
    logical: rpool/ROOT/ubuntu_k65d6x/var/log
  ID-5: swap-1 size: 495.56 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/dm-1
```
and without snap partitions:
```
 df -a
df: /run/user/1000/doc: Operation not permitted
Filesystem                                       Type             Size  Used Avail Use% Mounted on
sysfs                                            sysfs               0     0     0    - /sys
proc                                             proc                0     0     0    - /proc
udev                                             devtmpfs         3.8G     0  3.8G   0% /dev
devpts                                           devpts              0     0     0    - /dev/pts
tmpfs                                            tmpfs            782M  2.3M  780M   1% /run
/dev/mapper/keystore-rpool                       ext4             437M   28K  404M   1% /run/keystore/rpool
rpool/ROOT/ubuntu_k65d6x                         zfs              222G  5.2G  217G   3% /
securityfs                                       securityfs          0     0     0    - /sys/kernel/security
tmpfs                                            tmpfs            3.9G     0  3.9G   0% /dev/shm
tmpfs                                            tmpfs            5.0M  4.0K  5.0M   1% /run/lock
cgroup2                                          cgroup2             0     0     0    - /sys/fs/cgroup
pstore                                           pstore              0     0     0    - /sys/fs/pstore
efivarfs                                         efivarfs            0     0     0    - /sys/firmware/efi/efivars
bpf                                              bpf                 0     0     0    - /sys/fs/bpf
systemd-1                                        autofs              0     0     0    - /proc/sys/fs/binfmt_misc
mqueue                                           mqueue              0     0     0    - /dev/mqueue
debugfs                                          debugfs             0     0     0    - /sys/kernel/debug
hugetlbfs                                        hugetlbfs           0     0     0    - /dev/hugepages
tracefs                                          tracefs             0     0     0    - /sys/kernel/tracing
fusectl                                          fusectl             0     0     0    - /sys/fs/fuse/connections
configfs                                         configfs            0     0     0    - /sys/kernel/config
ramfs                                            ramfs               0     0     0    - /run/credentials/systemd-sysusers.service
rpool/USERDATA/root_smpmd2                       zfs              217G  2.2M  217G   1% /root
rpool/USERDATA/me_smpmd2                         zfs              218G  1.2G  217G   1% /home/me
rpool/ROOT/ubuntu_k65d6x/srv                     zfs              217G  256K  217G   1% /srv
rpool/ROOT/ubuntu_k65d6x/usr/local               zfs              217G  512K  217G   1% /usr/local
rpool/ROOT/ubuntu_k65d6x/var/games               zfs              217G  256K  217G   1% /var/games
rpool/ROOT/ubuntu_k65d6x/var/lib                 zfs              218G  1.7G  217G   1% /var/lib
rpool/ROOT/ubuntu_k65d6x/var/log                 zfs              217G   14M  217G   1% /var/log
rpool/ROOT/ubuntu_k65d6x/var/mail                zfs              217G  256K  217G   1% /var/mail
rpool/ROOT/ubuntu_k65d6x/var/spool               zfs              217G  384K  217G   1% /var/spool
rpool/ROOT/ubuntu_k65d6x/var/snap                zfs              217G  256K  217G   1% /var/snap
rpool/ROOT/ubuntu_k65d6x/var/www                 zfs              217G  256K  217G   1% /var/www
rpool/ROOT/ubuntu_k65d6x/var/lib/AccountsService zfs              217G  256K  217G   1% /var/lib/AccountsService
rpool/ROOT/ubuntu_k65d6x/var/lib/NetworkManager  zfs              217G  384K  217G   1% /var/lib/NetworkManager
rpool/ROOT/ubuntu_k65d6x/var/lib/apt             zfs              217G   95M  217G   1% /var/lib/apt
rpool/ROOT/ubuntu_k65d6x/var/lib/dpkg            zfs              217G   64M  217G   1% /var/lib/dpkg
bpool/BOOT/ubuntu_k65d6x                         zfs              1.8G  534M  1.3G  30% /boot
/dev/sdb1                                        vfat             511M   14M  498M   3% /boot/efi
/dev/sdb1                                        vfat             511M   14M  498M   3% /boot/grub
tmpfs                                            tmpfs            782M  5.8M  776M   1% /run/user/1000
gvfsd-fuse                                       fuse.gvfsd-fuse     0     0     0    - /run/user/1000/gvfs
/dev/sda3                                        ext4             429G  339G   68G  84% /media/me/Back-ups


```
Let me catch up with any new findings here in your thread.
EDIT Now I'm just making notes I find IE:
```
sudo zfs list bpool
[sudo] password for me: 
NAME    USED  AVAIL     REFER  MOUNTPOINT
bpool   535M  1.23G       96K  /boot


```
Yours is incomplete as in:
```
NAME    USED  AVAIL     REFER  MOUNTPOINT
bpool   394M   630M       96K  /mnt/boot

```
***But Please follow what  MAFoElffen has advised in post # 78 first.***

---

### Post by anystupidassname on 2022-11-12
> **MAFoElffen said:**
> In one of your link photo's from boot screen errors, it said it could not mount bpool/BOOT/ubuntu_uxtu99... But while you are manually mounted into it, it was mounted. Or at least from the above results, it appeared so. (???)

Post the results of this (while chrooted in):
```

zfs get mountpoint,mounted bpool -t filesystem -r
zpool events -v bpool
zpool history bpool


```
Here is what that looks like on one of mine... I think this is the info and perspective we are wanting to look from...
```

root@ubuntu--zfs-csm-02:/home/mafoelffen# zfs get mountpoint,mounted bpool -t filesystem -r
NAME                      PROPERTY    VALUE       SOURCE
bpool                     mountpoint  /boot       local
bpool                     mounted     no          -
bpool/BOOT                mountpoint  none        local
bpool/BOOT                mounted     no          -
bpool/BOOT/ubuntu_4thxnu  mountpoint  /boot       local
bpool/BOOT/ubuntu_4thxnu  mounted     yes         -
root@ubuntu--zfs-csm-02:/home/mafoelffen# zpool events -v bpool
TIME                           CLASS
Nov  8 2022 00:27:46.368000000 sysevent.fs.zfs.history_event
        version = 0x0
        class = "sysevent.fs.zfs.history_event"
        pool = "bpool"
        pool_guid = 0x59ded5e66266a929
        pool_state = 0x0
        pool_context = 0x0
        history_hostname = "ubuntu--zfs-csm-02"
        history_internal_str = "pool version 5000; software version zfs-2.1.4-0-g52bad4f23-dist; uts ubuntu--zfs-csm-02 5.15.0-52-generic #58-Ubuntu SMP Thu Oct 13 08:03:55 UTC 2022 x86_64"
        history_internal_name = "open"
        history_txg = 0x3b1
        history_time = 0x636a1302
        time = 0x636a1302 0x15ef3c00 
        eid = 0x6

Nov  8 2022 00:27:46.496000000 sysevent.fs.zfs.config_sync
        version = 0x0
        class = "sysevent.fs.zfs.config_sync"
        pool = "bpool"
        pool_guid = 0x59ded5e66266a929
        pool_state = 0x0
        pool_context = 0x0
        time = 0x636a1302 0x1d905c00 
        eid = 0x7

Nov  8 2022 00:27:46.496000000 sysevent.fs.zfs.pool_import
        version = 0x0
        class = "sysevent.fs.zfs.pool_import"
        pool = "bpool"
        pool_guid = 0x59ded5e66266a929
        pool_state = 0x0
        pool_context = 0x0
        time = 0x636a1302 0x1d905c00 
        eid = 0x8

Nov  8 2022 00:27:46.500000000 sysevent.fs.zfs.history_event
        version = 0x0
        class = "sysevent.fs.zfs.history_event"
        pool = "bpool"
        pool_guid = 0x59ded5e66266a929
        pool_state = 0x0
        pool_context = 0x0
        history_hostname = "ubuntu--zfs-csm-02"
        history_internal_str = "pool version 5000; software version zfs-2.1.4-0-g52bad4f23-dist; uts ubuntu--zfs-csm-02 5.15.0-52-generic #58-Ubuntu SMP Thu Oct 13 08:03:55 UTC 2022 x86_64"
        history_internal_name = "import"
        history_txg = 0x3b3
        history_time = 0x636a1302
        time = 0x636a1302 0x1dcd6500 
        eid = 0x9

Nov  8 2022 00:27:46.592000000 sysevent.fs.zfs.config_sync
        version = 0x0
        class = "sysevent.fs.zfs.config_sync"
        pool = "bpool"
        pool_guid = 0x59ded5e66266a929
        pool_state = 0x0
        pool_context = 0x0
        time = 0x636a1302 0x23493400 
        eid = 0xa

root@ubuntu--zfs-csm-02:/home/mafoelffen# zpool history bpool
History for 'bpool':
2022-11-07.23:35:22 zpool create -f -o ashift=12 -o autotrim=on -d -o feature@async_destroy=enabled -o feature@bookmarks=enabled -o feature@embedded_data=enabled -o feature@empty_bpobj=enabled -o feature@enabled_txg=enabled -o feature@extensible_dataset=enabled -o feature@filesystem_limits=enabled -o feature@hole_birth=enabled -o feature@large_blocks=enabled -o feature@lz4_compress=enabled -o feature@spacemap_histogram=enabled -O compression=lz4 -O acltype=posixacl -O xattr=sa -O relatime=on -O normalization=formD -O canmount=off -O devices=off -O mountpoint=/boot -R /target bpool /dev/disk/by-partuuid/44ce6ece-37f9-2542-880d-50dc19777fc0
2022-11-07.23:35:23 zfs create bpool/BOOT -o canmount=off -o mountpoint=none
2022-11-07.23:35:23 zfs create bpool/BOOT/ubuntu_4thxnu -o mountpoint=/boot
2022-11-07.23:48:08 zpool set cachefile= bpool
2022-11-08.00:05:26 zpool export bpool
2022-11-08.00:06:28 zpool import -c /etc/zfs/zpool.cache -aN
2022-11-08.00:27:46 zpool import -c /etc/zfs/zpool.cache -aN

```

> **MAFoElffen said:**
> Here's what I see from that:
```

2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_daily-2020-06-22-0819
2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_weekly-2020-06-20-0831
2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_a88wsc
2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_p0bujz
2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_r7nh1m
2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_s3shqy
2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_weekly-2020-06-13-0847
2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_zsihdd
2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_8ywnrh
2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_9njc9s
2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_8k0i0s
2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_8jfyyy
2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_ivet2r
2020-06-25.12:45:27 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_wal4es
2020-06-25.12:45:28 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_hc9z43
2020-06-25.12:45:28 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_z1jhlr
2020-06-25.12:45:28 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_ro6l0s
2020-06-25.12:45:28 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_k70miz
2020-06-25.12:45:28 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_5ujij3
2020-06-25.12:45:28 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_0edzqc
2020-06-25.12:45:28 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_sc3oh5
2020-06-25.12:45:28 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_4pe0gq
2020-06-25.12:45:28 zfs destroy bpool/BOOT/ubuntu_uxtu99@autozsys_035ael
2020-06-25.12:45:28 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_weekly-2020-06-06-1151
2022-10-25.12:55:50 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_daily-2020-06-25-0855
2022-10-25.12:55:50 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_daily-2020-06-26-1133
2022-10-25.12:55:50 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_daily-2020-06-28-0925
2022-10-25.12:55:50 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_weekly-2020-06-28-0930
2022-10-25.12:55:50 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_monthly-2020-06-28-0935
2022-10-25.12:55:50 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_daily-2020-06-29-0552
2022-10-25.12:55:50 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_hourly-2020-06-29-0817
2022-10-25.12:55:50 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_hourly-2020-06-29-0917
2022-10-25.12:55:50 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_hourly-2020-06-29-1317
2022-10-25.12:55:50 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_hourly-2020-06-29-1417
2022-10-25.12:55:50 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_hourly-2020-06-29-1617
2022-10-25.12:55:50 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_hourly-2020-06-29-1717
2022-10-25.12:55:50 zfs destroy bpool/BOOT/ubuntu_uxtu99@zfs-auto-snap_frequent-2020-06-29-1800
2022-11-06.15:46:41 zfs set canmount=on bpool/BOOT/ubuntu_uxtu99

```
Let me think about this a bit before I say anything... It looks like you cleaned up a lot of snapshots from the current bpool's UUID... Then, well... Let me mull this over.

EDIT: Please after you chroot int to it, then rerun the 'system-info' script, using the '-d" startup flag and post the URL to the pastebin... I'm thinking if you install a newer kernel, that it will create a newer bpool/ubuntu_<UUID> and correct itself and all the internal mounts... then export it to save and shutdown the filesystem. I just need some info from that report to figure out which kernel to reommend, that will be replaced by normal updates (soon). Something like Linux Kernel 5.15.0-60 from the Ubuntu Mainline PPA...

Yes, if you look at my 3rd or 4th post, you were hypothesizing that lack of space on bpool was the cause of stopped snapshots and/or all of these problems.
The commands you had given to remove old snapshots were not working because systemd doesn't work in chroot (I think?) and I figured out how to remove the older snapshots a different way. zsys wasn't even installed at the time so probably part of the issue.
Anyway, it doesn't seem like lack of space in the bpool was ever an issue.
Even if reverting to the most "recent" 2020 snapshot was possible (not available in grub menu any more), I need the system back as it was in august 2022 or later.

I've tried several kernels and I'm willing to try another one.
"system-info -d" is not a valid command as root user inside chroot. There is a package "libsystem-info-perl" is that what you want me to install to use?

---

### Post by anystupidassname on 2022-11-12
> **MAFoElffen said:**
> Something like (while chrooted in, and replacing <user_name> with your own...):
```

cd /home/<user_name>/Downloads
mkdir ./mainline && mkdir ./mainline/v5.15.60
cd ./mainline/v5.15.60
wget -N -t 5 -T 10 https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.15.60/amd64/linux-headers-5.15.60-051560-generic_5.15.60-051560.202208110844_amd64.deb
wget -N -t 5 -T 10 https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.15.60/amd64/linux-headers-5.15.60-051560_5.15.60-051560.202208110844_all.deb
wget -N -t 5 -T 10 https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.15.60/amd64/linux-modules-5.15.60-051560-generic_5.15.60-051560.202208110844_amd64.deb
wget -N -t 5 -T 10 https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.15.60/amd64/linux-image-unsigned-5.15.60-051560-generic_5.15.60-051560.202208110844_amd64.deb
dpkg -i *.deb
exit
sudo zfs export bpool
sudo zfs export rpool
sudo reboot

```

After installing the 5.15.60 kernel GRUB does show it and try to boot it. Boot fails in a different way. (initramfs - no ZFS modules loaded..?)
[https://ibb.co/bJZPQdF](https://ibb.co/bJZPQdF)

---

### Post by anystupidassname on 2022-11-12
> **1fallen said:**
> Sorry, all I can say here is real life can just dominate my time as of late.
No worries, I'm just glad I'm getting any help at all.

>  I flat hate snaps on a zfs root so that the first thing I dump. **_(NOTE: I'm not advising you to get rid of snapd)_**
We're on the same page not being snapd fans.
In case it is relevant, I'm pretty sure I had eradicated snap from the focal install prior to this disaster of an upgrade. I hope that didn't contribute to it.
Although it is clearly reinstalled now after the do-release-upgrade.

> 
EDIT Now I'm just making notes I find IE:
```
sudo zfs list bpool
[sudo] password for me: 
NAME    USED  AVAIL     REFER  MOUNTPOINT
bpool   535M  1.23G       96K  /boot


```
Yours is incomplete as in:
```
NAME    USED  AVAIL     REFER  MOUNTPOINT
bpool   394M   630M       96K  /mnt/boot

```
***But Please follow what  MAFoElffen has advised in post # 78 first.***

I've noticed that too. I don't know why during one of the tons of things we've run during this troubleshooting, this has changed.
October 27th and probably later, zfs list bpool in chroot showed /boot but it now shows /mnt/boot even though "mount" shows /boot
                                                             [https://termbin.com/gahw](https://termbin.com/gahw) < mount             

             [LEFT] [https://termbin.com/k3du](https://termbin.com/k3du) < zfs list             
[/LEFT]          
   
Additionally, if the mount points were wrong, wouldn't installing the kernel (from post #78) have failed more spectacularly?
Maybe something related to the vfstab you were originally talking about?

During this entire process, I feel like chroot has been behaving flaky but I don't really understand the intricacies of what is going on so take that with a grain of salt.

---

### Post by MAFoElffen on 2022-11-12
> **anystupidassname said:**
> i've tried several kernels and I'm willing to try another one. No zfs modules.... Dang

To back that kernel back off...
```

cd /home/<user_name>/Downloads
cd ./mainline/v5.15.60
dpkg -r *.deb

```

It was worth a try...

EDIT: 

How about current?
```

apt install --reinstall linux-headers-5.15.0-52-generic linux-image-5.15.0-52-generic linux-modules-5.15.0-52-generic linux-modules-extra-5.15.0-52-generic

```

---

### Post by #&amp;thj^% on 2022-11-12
Agreed No zfs modules....has the OP ran:
```
sudo update-initramfs
```
That dose not get run automaticaly in a chroot environment, and if that fails, we would need to see that output
1.You mount your pool on /mnt
2.You chroot into /mnt which should give you a perfectly valid chroot system.....Then run the command above.
Lets us/me know if we are confusing you, a lot info can lead to an overload for anyone.
BTW the kernel version should not be a factor here, I'm running " Kernel: 6.0.0-1006-oem"
```
 modinfo zfs
filename:       /lib/modules/6.0.0-1006-oem/kernel/zfs/zfs.ko
version:        2.1.5-1ubuntu5
license:        CDDL
author:         OpenZFS
description:    ZFS
alias:          devname:zfs
alias:          char-major-10-249
srcversion:     5A94B4662A7A991696CC35F
depends:        spl,icp,zavl,znvpair,zcommon,zlua,zzstd,zunicode
retpoline:      Y
name:           zfs
vermagic:       6.0.0-1006-oem SMP preempt mod_unload modversions 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key

```

---

### Post by MAFoElffen on 2022-11-14
[quote=1fallen]
```
sudo update-initramfs
```[/quote]
Yes. Agreed. Do that first, before trying to un-install and install a different Kernel...

The reason I want you to try that, is because you are having a problem with it mounting the bpool (on it's own).

By what you have posted back... You have shown that you can mount the pools and filesystem, and chroot into it. It reports back that  everything seems 'appear' okay. It installed Grub successfully, with no erors... Then hung during boot of the initramfs, saying it couldn't mount the bpool.

What is strange, is that it did not saying that it was a a data or filesystem fault, nor returned any ZFS filesystem error codes. So I am leaning towards it either having a mount, kernel or some other unknown problem in the bpool. What is strange there, is that the mounts report back looking okay.

So yes, if it gets another kernel installed (with the appropriate ZFS kernel modules) while under a chroot... THEN the filesystem (bpool and rpool) exported... Then that should take care of both of thos conditions. 

If that does not work... Then try to reinstall the same kernel (5.15.0-52). If that doesn't work... Then install new, and migrate the data to the new install. Running that 'system-info' script before hand would help out with that (documenting manually installed and such).

---

### Post by anystupidassname on 2022-11-16
edit

---

### Post by anystupidassname on 2022-11-16
> **MAFoElffen said:**
> No zfs modules.... Dang

To back that kernel back off...
```

cd /home/<user_name>/Downloads
cd ./mainline/v5.15.60
dpkg -r *.deb

```

It was worth a try...

EDIT: 

How about current?
```

apt install --reinstall linux-headers-5.15.0-52-generic linux-image-5.15.0-52-generic linux-modules-5.15.0-52-generic linux-modules-extra-5.15.0-52-generic

```

So I've tried .60 and .52 (including running update-initramfs for each) and the boot continues to fail in the same 2 ways:
[https://ibb.co/bJZPQdF](https://ibb.co/bJZPQdF)
[https://oshi.at/YQVt](https://oshi.at/YQVt)

---

### Post by MAFoElffen on 2022-11-16
Migrate the data to a new install. The 'system-info' script report has a list of the manually installed packages... Putting it out there so it is there for prosperity.
```

0ad
0install
ansiweather
anydesk
apktool
apt-transport-https
aria2
armcord
atftp
audacious
audacity
baobab
biglybt
bisq
bitwarden
bluez-tools
boot-repair
boxes
brave-browser
btrfs-progs
calligra
cdparanoia
cdrdao
checkra1n
cinnamon
clementine
curl
dconf-editor
deborphan
dialog
dino-im
dissenter-browser
dmtracedump
dot
duplicati
dxvk
efibootmgr
element-desktop
endless-sky
etc1tool
f2fs-tools
fancontrol
fastboot
ferdi
filezilla
firejail
flameshot
franz
gamemode
gconf2
gdebi
gimp
gir1.2-appindicator3-0.1
git
gnome-characters
gnome-logs
gnome-shell-extension-gsconnect-browsers
gnumeric
gparted
grsync
gucharmap
heimdall-flash-frontend
hexer
hprof-conv
htop
imagemagick
img2pdf
iperf3
keepassxc
krita
lftp
libdouble-conversion1
libncurses5
libncurses5:i386
libncursesw5
libpcre16-3
libqt5serialport5
libreoffice-calc
libreoffice-draw
libreoffice-writer
librewolf
liferea
linux-headers-5.15.60-051560
linux-headers-5.15.60-051560-generic
linux-headers-5.4.0-24
linux-headers-5.4.0-24-generic
linux-image-5.15.0-52-generic
linux-image-unsigned-5.15.60-051560-generic
linux-modules-5.15.60-051560-generic
linux-modules-5.4.0-24-generic
lm-sensors
localepurge
lutris
lximage-qt
lxqt-about
lxqt-admin
lxqt-branding-debian
lxqt-core
lxqt-openssh-askpass
lxqt-powermanagement
lxqt-sudo
min
minetest
mktorrent
moc
mono-complete
moon-lander
mosh
muffin
mypaint
nala-legacy
ncdu
net-tools
nomacs
nuntius
ocrmypdf
openjdk-8-jre
openjfx
openshot-qt
oscar
otpclient
p7zip-rar
particl-desktop
pastebinit
pavucontrol-qt
pcscd
pdfsandwich
pdftk
peazip
peazip-unace-plugin-linux
pinta
piper
preload
protonvpn
protonvpn-stable-release
purple-discord
python3-multibootusb
python3-pip
python3-pyudev
python3-setuptools
qbittorrent
qemu-efi
qemu-efi-aarch64
qemu-system-arm
qemu-utils
qlipper
qpdf
qpdfview
qps
qrencode
qterminal
qttranslations5-l10n
quassel
qutebrowser
qview
rclone-browser
remmina
remmina-plugin-spice
scrcpy
screengrab
sddm
sddm-theme-debian-maui
simplenote
smartmontools
smplayer
socat
speedtest-cli
spezepip
sqlite3
stacer
streamlink
streamtuner2
stress
synaptic
telegram-purple
tftp
tftpd-hpa
thinkfan
thunderbird
tixati
torbrowser-launcher
tribler
tusk
udftools
unetbootin
ungoogled-chromium
unrar
usbimager
vera

```
Which I agree is going to be complex, because of your Linux Steam Games.

I do not see why the machine will not boot. You backed off the mainline kernel and reinstalled Ubuntu Kernel 5.15.0-52 and you said that it fails in the same way. which would mean that the ZFS modules are not there fore that either? I'm not understanding something with that. It should have worked.

Okay. So I tried to send/receive from one to another via ssh and failed. I'm not going to recommend something that didn't work for me. But you could "send" to a file on a blank USB thumb drive, which you could receive from a new machine.

Method 1:
The process would be to chroot in. Mount the UCB drive. Make a snap shot of the rpool. Clone it. Send the clone to  usb drive. Receive the clone. Promote the clone. Test it.

Method 2:
Restored the data from the backup to the new install. Use the list above to reinstall what you had installed on the old machine.

---

### Post by MAFoElffen on 2022-11-20
Through with installing my new server... Thought of a few things during the process on mine...

The error you are getting occurs when it tries to mount the bpool. It does that by trying to read 
```

mafoelffen@ubuntu-ZFS-PC-Q35-ICH9-22041-02:~$ cat /etc/zfs/zfs-list.cache/bpool
bpool    /boot    off    on    on    off    on    off    on    off    -none    -    -    -    -    -    -    -    -
bpool/BOOT    none    off    on    on    off    on    off    on    off    -    none    -    -    -    -    -    -    -    -
bpool/BOOT/ubuntu_k930ob    /boot    on    on    on    off    on    off    on    off    -    none    -    -    -    -    -    --    -

```
That is on one of mine... That gets populated by zed...
which is the result of
```

zfs set canmount=off mountpoint=/boot
zfs set canmount=off -mountpoint=none bpool/BOOT
UUID="k930ob"
zfs set mountpoint=/boot bpool/BOOT/ubuntu_$UUID
# Below commented out (was used to create a new file)
# touch /etc/zfs/zfs-list.cache/bpool
zed -F
cat /etc/zfs/zfs-list.cache/bpool
exit
mount | grep -v zfs | tac | awk '/\/mnt/ {print $3}' | xargs -i{} umount -lf {}
zpool export -a

```

---

