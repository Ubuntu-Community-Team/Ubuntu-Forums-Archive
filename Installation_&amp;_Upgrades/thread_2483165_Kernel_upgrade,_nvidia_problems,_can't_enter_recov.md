---
title: "Kernel upgrade, nvidia problems, can't enter recovery mode or access terminal"
date: 2023-01-22
forum: Installation &amp; Upgrades
---

### Post by janderson9er on 2023-01-22
My desktop machine is unable to boot. I strongly suspect it is related to nvidia driver issues, I would love to get to a console so I can nuke it from the system and see if I can boot again.

I am running Ubuntu 18.04 with Nvidia EVGA GeForce RTX 2070 card.

This started when I was trying to upgrade my linux drivers by running command: `sudo ubuntu-drivers autoinstall`


After that, I was unable to login to my account, where I would constantly get directed back to the login screen after entering my password.


After failing to boot, I went to advanced mode and had the option of 4.15.0-96-generic or 4.15.0-91-generic. (see [https://i.imgur.com/2uLTP6e.jpg](https://i.imgur.com/2uLTP6e.jpg))


I booted into recovery mode with 4.15.0-91-generic, and after [following another post]([https://askubuntu.com/questions/41930/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block0-0](https://askubuntu.com/questions/41930/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block0-0)) was able to get the machine to boot with: 
 - `sudo apt-get remove --purge "nvidia-*"`
 - `update-initramfs -u -k 4.15.0-91-generic`
 - `update-grub`


This let me login and get to my desktop, but it was running in resolution 1024X768 resolution on my 4k monitor, which wasn't usable. I rebooted, and now I can't get any of the options to work.


Working through them in order:


- 4.15.0-96-generic (both) fail with: Kernel panic - not syncing: VFS: Unable to mount fs on unknown-block(0,0). (see [https://i.imgur.com/ue1KjBq.jpg](https://i.imgur.com/ue1KjBq.jpg)) From what I can tell, when you see this the best option is to try the other kernels listed. 


- 4.15.0-91-generic now gets stuck booting to recover mode at: "[ OK ]: AppArmor initialiation" or "[ OK ] Started Network Time Synchronization". (see [https://i.imgur.com/7vRWMT1.jpg](https://i.imgur.com/7vRWMT1.jpg)) This was how I was able to run the `update-initramfs` command earlier, and now it's not responding to Alt+Shift+F3 to bring me to console

- 4.15.0-91-generic (recovery mode) lets me decrypt my drives, and then ends in a series of black flashing screens. I suspect this is nvidia related based on what I have read.


As best as I can tell, I may want to update grub so that it uses 4.15.0-91-generic (currently initrd.img-4-15-0-96-generic, see [https://i.imgur.com/ClgcDVS.jpg](https://i.imgur.com/ClgcDVS.jpg)) and replacing `quiet splash` with `nomodeset` to try to get to a terminal. From there, I'm cautiously optimistic I can follow the stickied Nvidia post, but I'm not sure how to do this with kernel problems as I'm dealing with nvidia problems and I really don't want to make this worse.


Thank you!

---

### Post by deadflowr on 2023-01-22
Why are you running such an old and out of date kernel?

---

### Post by janderson9er on 2023-01-22
No reason in particular. It hasn't been a problem and I wasn't aware I was that out of date. 

Is that going to be a problem? Is there anything I can do to get back to a terminal from here?

---

### Post by Impavidus on 2023-01-22
You didn't mention your Ubuntu release or any details on your nvidia graphics (not that I know much about nvidia stuff).

Kernel series 4.15 is used on Ubuntu 18.04 (3 months of support left), which is currently at 4.15.0-202. 4.15.0-96 was apparently released in April 2020. I don't know what nvidia provides, but they won't support old kernels forever.

---

### Post by janderson9er on 2023-01-22
Whoops, I missed copy pasting that into my original message. Sorry about that. I'll update that.

I am running Ubuntu 18.04 with Nvidia EVGA GeForce RTX 2070 card.

Basically, I'm wondering if I can just edit the grub config to point to 91 and try to access console from there. If I can get to the console, I can uninstall nvidia drivers, get to a state where I can boot and login, and back everything up. I'll re-format and install latest version, but I can't even access the terminal.

---

### Post by ajgreeny on 2023-01-22
What nvidia driver are you using and how did you install it?  I hope you used the Additional Drivers utility and did not go direct to nvidia.

There have been a few difficulties with the nvidia 525 driver pulling in unusual and broken kernels in the 22.04 Ubuntu version but I haven't heard anything about this happening in 18.04, and in the 22.04 problems the kernel pulled in by the nvidia driver was a 5.15.0-1025-oracle version which is not happening in your system.

Let's see the output of command ```
apt list --installed | grep *nvidia
``` which may give more clues as to what is going on and should tell us hopefully the nvidia driver you're using if you are not already aware of the version.

---

### Post by janderson9er on 2023-01-22
Hi, thanks for you help! I want to say I was running 510, but I'm not positive.

Unfortunately, I am unable to get to a terminal anywhere to be able to run that command. All 4 of the kernel options I have in Grub are not booting, and I haven't been able to get to a terminal.

I think the drivers are a bit of a misdirect, in that the first step is I need to get to a terminal to be able to fix my kernel issues.

---

### Post by Bashing-om on 2023-01-22
janderson9er; Hello

Try the nomodeset boot parameter to isolate as a graphic's issue:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) <- How to set NOMODESET and other kernel boot options in grub2

If you can boot here we can look there.

[INDENT]there is a process
[/INDENT]

---

### Post by janderson9er on 2023-01-23
Thank you! That's exactly what I needed to hear. 

Is it safe for me to update the kernel version too? It's pointing to [COLOR=#000000]4.15.0-96-generic, but I probably need to boot into [/COLOR][COLOR=#000000]4.15.0-91-generic.[/COLOR]

---

### Post by Bashing-om on 2023-01-23
janderson9er; Hey -

Yeah:
> 
but I probably need to boot into 4.15.0-91-generic


When you boot to grub's boot menu there should be at least one other kernel that you may select to boot.

A good thought on your part to see what results when booting a different kernel version. Maybe like, that the graphic's driver failed to build on the newer kernel ?

[INDENT]gots to be a reason
[/INDENT]

---

### Post by MAFoElffen on 2023-01-24
If it still does not boot, I have a couple of ideas.

Option 1.) At the Grub boot menu, on a boot menu option, Press the <E> key to get into an edit mode, <Arrow-Down> to the line that starts with the word "linux"... <Arrow-Right> to after the word "ro" and before "quiet splash  ${vthandoff}:... Delete all that and enter append
```

--- nomodeset --verbose debug 3

```
Then <Cntrl><X> to boot those options.

That should not only try to boot, but also toggles it to boot into RC_LEVEL 3, which is text console. When that happens, it should not even try to use the graphics driver. (More of a chance) If it does not boot, it should show some kind of hint at that level of debug messaging.

Option 2.) Boot off an Ubuntu Live Install media and mount the installed OS, chroot into it, to remove the NVidida drivers and rebuild the initramfs image. More instructions can be provided if you need to do this.

---

### Post by janderson9er on 2023-01-28
> **MAFoElffen said:**
> If it still does not boot, I have a couple of ideas.

Option 1.) At the Grub boot menu, on a boot menu option, Press the <E> key to get into an edit mode, <Arrow-Down> to the line that starts with the word "linux"... <Arrow-Right> to after the word "ro" and before "quiet splash  ${vthandoff}:... Delete all that and enter append
```

--- nomodeset --verbose debug 3

```
Then <Cntrl><X> to boot those options.

That should not only try to boot, but also toggles it to boot into RC_LEVEL 3, which is text console. When that happens, it should not even try to use the graphics driver. (More of a chance) If it does not boot, it should show some kind of hint at that level of debug messaging.

Option 2.) Boot off an Ubuntu Live Install media and mount the installed OS, chroot into it, to remove the NVidida drivers and rebuild the initramfs image. More instructions can be provided if you need to do this.

Hi, thank you for your help!

I was able to get back to my machine today, and ran into some trouble.

I went through the following trouble-shooting steps:
- Update grub to boot to 91 instead of 96, stuck loading 18.04 Ubuntu for a while, booted to BusyBox v.1.27.2 "initramfs" blinking terminal that would not respond (no typing recognized, "help" + enter did nothing).
- Followed the advice from [COLOR=#000000]MAFoElffen and booted into v91 with [/COLOR][COLOR=#000000][FONT=&amp]--- nomodeset --verbose debug 3[/FONT][/COLOR][COLOR=#000000] , which booted into BusyBoxy 1.27.2 with the same unresponsive terminal.

I am able to decrypt the drives when I try to enter recovery mode, but I have not been asked to decrypt them by the time I get to the BusyBox prompt.

I really appreciate the help! It sounds like I may need option 2, or maybe something else to continue.


[/COLOR]

---

### Post by MAFoElffen on 2023-01-29
> **janderson9er said:**
> [COLOR=#000000]I am able to decrypt the drives when I try to enter recovery mode, but I have not been asked to decrypt them by the time I get to the BusyBox prompt.
[/COLOR]
How is it encrypted? Please describe. That will affect instructions for Option #2...

EDIT: LUKS? LVM? ZFS? Just the Home? ROOT? ETC...

---

### Post by janderson9er on 2023-01-30
> **MAFoElffen said:**
> How is it encrypted? Please describe. That will affect instructions for Option #2...

EDIT: LUKS? LVM? ZFS? Just the Home? ROOT? ETC...


Sorry, I did this a while ago and it was when I was new with Ubuntu, so I'm not sure.

It is full disk encryption (all drives) and would have been done through a GUI, but I can't remember exactly what I did. 

It asks me to decrypt on boot, decrypts all the drives with the same password but each drive is separate (not merged or split at all), if that helps any.

---

### Post by MAFoElffen on 2023-01-30
That open more questions. Please run the boot repait disk and submit a report...

---

### Post by janderson9er on 2023-02-02
I thought that might make it worse, lol. Appreciate your help! I'll be near that computer again in a few days and will post the report.

---

### Post by MAFoElffen on 2023-02-02
Thank you... Yes. Saying it is "encrypted" could mean LUKS (1 or 2), LVM2 Native encryption or ZFS Native encryption... And there are instructions for each, based on what it is...

---

### Post by MAFoElffen on 2023-02-02
For example, if it turns out that it is LVM, then:
```

# Boot the live (Desktop) CD and install lvm2 and cryptsetup.
sudo apt-get update && sudo apt-get install lvm2 cryptsetup

# Load the cryptsetup module.
sudo modprobe dm-crypt

# To find your root volume
sudo lsblk

# Decrypt your file system.
# Adjust this to where your root volume is...
sudo cryptsetup luksOpen /dev/sda1 crypt

# Get the live CD to recognize (activate) your LVM.
sudo vgscan --mknodes
sudo vgchange -ay

# Use this to ID where your root is in /dev/mapper
ls /dev/mapper

# You can now access / mount the crypt
# Adjust this to where your root is...
sudo mkdir /mnt/crypt_root
sudo mount /dev/mapper/root /mnt/crypt_root

sudo -i

# mount your boot partition in the chroot, if separate
# If you do not have a separate boot, skip this
mount /dev/sda2 /mnt/chroot_root/boot

# mount home, also if you have a separate home
# If you do not have a separate home, skip this
mount /dev/your_home_partition

cd /mnt/crypt_root
mount --bind /dev /mnt/crypt_root/dev
mount --bind /proc /mnt/crypt_root/proc
mount -o bind /run /mnt/crypt_root/run
chroot /mnt/crypt_root --login
mount -a

```
Then do what you need to do. When through, type "exit" to get out of the chroot.

---

### Post by janderson9er on 2023-02-11
> **MAFoElffen said:**
> That open more questions. Please run the boot repait disk and submit a report...

Hi, I have a [pastebin link]("https://pastebin.ubuntu.com/p/85TqmXvbY5/") with my boot repair report. It looks like I am using LUKS.

---

### Post by MAFoElffen on 2023-02-11
This i how I open LUKS encrytpted drives
```

ubuntu@ubuntu:~$ lsblk
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
loop0    7:0    0    2G  1 loop /rofs
loop1    7:1    0 55.4M  1 loop /snap/core18/2128
loop2    7:2    0  219M  1 loop /snap/gnome-3-34-1804/72
loop3    7:3    0 32.3M  1 loop /snap/snapd/12704
loop4    7:4    0 65.1M  1 loop /snap/gtk-common-themes/1515
loop5    7:5    0   51M  1 loop /snap/snap-store/547
sr0     11:0    1  2.9G  0 rom  /cdrom
vda    252:0    0   25G  0 disk 
&#9500;&#9472;vda1 252:1    0    2M  0 part 
&#9500;&#9472;vda2 252:2    0  128M  0 part 
&#9500;&#9472;vda3 252:3    0  768M  0 part 
&#9492;&#9472;vda5 252:5    0 24.1G  0 part 

ubuntu@ubuntu:~$ sudo -i

root@ubuntu:~# export DEV="/dev/vda"

root@ubuntu:~# export DM="${DEV##*/}"

root@ubuntu:~# export DEVP="${DEV}$( if [[ "$DEV" =~ "nvme" ]]; then echo "p"; fi )"

root@ubuntu:~# export DM="${DM}$( if [[ "$DM" =~ "nvme" ]]; then echo "p"; fi )"

root@ubuntu:~# sgdisk --print $DEV
Disk /dev/vda: 52428800 sectors, 25.0 GiB
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): F55FCB42-F356-4C7B-A747-5D046D7B8907
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 52428766
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048            6143   2.0 MiB     EF02  GRUB
   2            6144          268287   128.0 MiB   EF00  EFI-SP
   3          268288         1841151   768.0 MiB   8301  /boot
   5         1841152        52428766   24.1 GiB    8301  rootfs

root@ubuntu:~# ls /dev/mapper/
control  LUKS_BOOT  ubuntu--vg-root  ubuntu--vg-swap_1  vda5_crypt

root@ubuntu:~# cryptsetup open ${DEVP}3 LUKS_BOOT
Enter passphrase for /dev/vda3: 

root@ubuntu:~# cryptsetup open ${DEVP}5 ${DM}5_crypt
Enter passphrase for /dev/vda5:

```
Whereas yours is only encrypted on /dev/sda5, so change to sda and related...
Then I would change to mount that drive to /mnt and chroot into it to make your changes...

---

### Post by janderson9er on 2023-02-11
Thank you!

I'm back in the repair disk at the terminal, and working through this. I think I'm following ok, but I'm not seeing a LUKS_BOOT (or any boot or crypt) in my /dev/mapper/

```

root@lubuntu:~# export DEV="/dev/sda"
root@lubuntu:~# export DM="${DEV##*/}"
root@lubuntu:~# export DEVP="${DEV}$( if [[ "$DEV" =~ "nvme" ]]; then echo "p"; fi )"
root@lubuntu:~# export DM="${DM}$( if [[ "$DM" =~ "nvme" ]]; then echo "p"; fi )"
root@lubuntu:~# sgdisk --print $DEV

***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************

Disk /dev/sda: 1000215216 sectors, 476.9 GiB
Model: INTEL SSDSC2KW51
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): 83B56A1A-89A4-4732-B591-03A7035F0997
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 1000215182
Partitions will be aligned on 2048-sector boundaries
Total free space is 4717 sectors (2.3 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1499135   731.0 MiB   8300  Linux filesystem
   5         1501184      1000214527   476.2 GiB   8300  Linux filesystem

root@lubuntu:~# ls /dev/mapper/
control


```

Does that make sense?

The output from boot repair gives me command: sudo cryptsetup luksOpen /dev/sda5 myvolume , which worked last time I booted to repair disk.

---

### Post by MAFoElffen on 2023-02-12
And if you do that now, can you chroot into it to repiar it? (purge NVidia)

---

### Post by janderson9er on 2023-02-24
Thanks again for all your help, I really appreciate it. Sorry for delays, I'm back at my machine and will be for a few weeks at least.

Yes, I believe I was able to chroot in and purge things, but I don't think it helped. I restarted and was not able to boot into either of the kernel versions, including recovery modes.

Here's my console session in another [pastebin]("https://pastebin.ubuntu.com/p/FxMhkqKVw7/"), with the important parts highlighted below. I may have missed mounting something (I followed [another post]("https://feeding.cloud.geek.nz/posts/recovering-from-unbootable-ubuntu-encrypted-lvm-root-partition/") with similar problem), but I'mt nosre sure what.


[COLOR=#000080]**root@lubuntu:/#**[/COLOR] cryptsetup luksOpen /dev/sda5 sda5_crypt
[COLOR=#808080]Enter passphrase for /dev/sda5:[/COLOR]
[COLOR=#000080]**root@lubuntu:/#**[/COLOR] vgchange -ay
[COLOR=#808080]  2 logical volume(s) in volume group "ubuntu-vg" now active[/COLOR]
[COLOR=#000080]**root@lubuntu:/#**[/COLOR] mount /dev/mapper/ubuntu--vg-root /mnt
[COLOR=#000080]**root@lubuntu:/#**[/COLOR] mount /dev/sda1 /mnt/boot
[COLOR=#000080]**root@lubuntu:/#**[/COLOR] mount -t proc proc /mnt/proc
[COLOR=#000080]**root@lubuntu:/#**[/COLOR] mount -o [COLOR=#AA22FF]bind[/COLOR] /dev /mnt/dev
[COLOR=#000080]**root@lubuntu:/#**[/COLOR] less /etc/crypttab
[COLOR=#000080]**root@lubuntu:/#**[/COLOR] chroot /mnt

[COLOR=#000080]**root@lubuntu:/#**[/COLOR] sudo update-initramfs -k all -c
[COLOR=#808080]update-initramfs: Generating /boot/initrd.img-version[/COLOR]
[COLOR=#808080]WARNING: missing /lib/modules/version[/COLOR]
[COLOR=#808080]Ensure all necessary drivers are built into the linux image![/COLOR]
[COLOR=#808080]depmod: ERROR: Bad version passed version[/COLOR]
[COLOR=#808080]dpkg: warning: version 'version' has bad syntax: version number does not start with digit[/COLOR]
[COLOR=#808080]dpkg: warning: version 'version' has bad syntax: version number does not start with digit[/COLOR]
[COLOR=#808080]depmod: ERROR: Bad version passed version[/COLOR]
[COLOR=#808080]update-initramfs: Generating /boot/initrd.img-4.15.0-96-generic[/COLOR]

[COLOR=#808080]update-initramfs: Generating /boot/initrd.img-4.15.0-91-generic[/COLOR]

[COLOR=#000080]**root@lubuntu:/#**[/COLOR] sudo apt-get purge nvidia*

[COLOR=#808080]Reading package lists... Done[/COLOR]
[COLOR=#808080]Building dependency tree      [/COLOR]
[COLOR=#808080]Reading state information... Done[/COLOR]
[COLOR=#808080]The following packages were automatically installed and are no longer required:[/COLOR]
[COLOR=#808080]  libnvidia-cfg1-515 libnvidia-common-515 libnvidia-decode-515 libnvidia-decode-515:i386 libnvidia-encode-515 libnvidia-encode-515:i386 libnvidia-extra-515 libnvidia-fbc1-515 libnvidia-fbc1-515:i386 libnvidia-gl-515 libnvidia-gl-515:i386 screen-resolution-extra xserver-xorg-video-nvidia-515[/COLOR]
[COLOR=#808080]Use 'sudo apt autoremove' to remove them.[/COLOR]
[COLOR=#808080]The following packages will be REMOVED:[/COLOR]
[COLOR=#808080]  nvidia-compute-utils-515* nvidia-compute-utils-525* nvidia-dkms-515* nvidia-dkms-525* nvidia-driver-515* nvidia-kernel-common-515* nvidia-kernel-common-525* nvidia-kernel-source-515* nvidia-prime* nvidia-settings* nvidia-utils-515*[/COLOR]
[COLOR=#808080]0 upgraded, 0 newly installed, 11 to remove and 51 not upgraded.[/COLOR]
[COLOR=#808080]After this operation, 96.0 MB disk space will be freed.[/COLOR]
[COLOR=#808080]Do you want to continue? [Y/n] y[/COLOR]
[COLOR=#808080]E: Can not write log (Is /dev/pts mounted?) - posix_openpt (19: No such device)[/COLOR]
[COLOR=#808080](Reading database ... 336597 files and directories currently installed.)[/COLOR]
[COLOR=#808080]Removing nvidia-driver-515 (515.86.01-0ubuntu0.18.04.1) ...[/COLOR]
[COLOR=#808080]Removing nvidia-compute-utils-515 (515.86.01-0ubuntu0.18.04.1) ...[/COLOR]
[COLOR=#808080]Running in chroot, ignoring request: stop[/COLOR]
[COLOR=#808080]Removing nvidia-dkms-515 (515.86.01-0ubuntu0.18.04.1) ...[/COLOR]
[COLOR=#808080]Removing all DKMS Modules[/COLOR]
[COLOR=#808080]Done.[/COLOR]
[COLOR=#808080]INFO:Disable nvidia[/COLOR]
[COLOR=#808080]DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude[/COLOR]
[COLOR=#808080]DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here[/COLOR]
[COLOR=#808080]DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad[/COLOR]
[COLOR=#808080]update-initramfs: deferring update (trigger activated)[/COLOR]
[COLOR=#808080]Removing nvidia-kernel-common-515 (515.86.01-0ubuntu0.18.04.1) ...[/COLOR]
[COLOR=#808080]update-initramfs: deferring update (trigger activated)[/COLOR]
[COLOR=#808080]Removing nvidia-kernel-source-515 (515.86.01-0ubuntu0.18.04.1) ...[/COLOR]
[COLOR=#808080]Removing nvidia-prime (0.8.16~0.18.04.1) ...[/COLOR]
[COLOR=#808080]Removing nvidia-settings (470.57.01-0ubuntu0.18.04.1) ...[/COLOR]
[COLOR=#808080]Removing nvidia-utils-515 (515.86.01-0ubuntu0.18.04.1) ...[/COLOR]
[COLOR=#808080]Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...[/COLOR]
[COLOR=#808080]Processing triggers for initramfs-tools (0.130ubuntu3.13) ...[/COLOR]
[COLOR=#808080]update-initramfs: Generating /boot/initrd.img-version[/COLOR]
[COLOR=#808080]WARNING: missing /lib/modules/version[/COLOR]
[COLOR=#808080]Ensure all necessary drivers are built into the linux image![/COLOR]
[COLOR=#808080]depmod: ERROR: Bad version passed version[/COLOR]
[COLOR=#808080]dpkg: warning: version 'version' has bad syntax: version number does not start with digit[/COLOR]
[COLOR=#808080]dpkg: warning: version 'version' has bad syntax: version number does not start with digit[/COLOR]
[COLOR=#808080]depmod: ERROR: Bad version passed version[/COLOR]
[COLOR=#808080]Processing triggers for libc-bin (2.27-3ubuntu1.6) ...[/COLOR]
[COLOR=#808080]Processing triggers for man-db (2.8.3-2ubuntu0.1) ...[/COLOR]
[COLOR=#808080]Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...[/COLOR]
[COLOR=#808080]Processing triggers for mime-support (3.60ubuntu1) ...[/COLOR]
[COLOR=#808080](Reading database ... 336036 files and directories currently installed.)[/COLOR]
[COLOR=#808080]Purging configuration files for nvidia-prime (0.8.16~0.18.04.1) ...[/COLOR]
[COLOR=#808080]Purging configuration files for nvidia-settings (470.57.01-0ubuntu0.18.04.1) ...[/COLOR]
[COLOR=#808080]Purging configuration files for nvidia-kernel-common-525 (525.78.01-0ubuntu0.18.04.1) ...[/COLOR]
[COLOR=#808080]update-initramfs: deferring update (trigger activated)[/COLOR]
[COLOR=#808080]Purging configuration files for nvidia-kernel-common-515 (515.86.01-0ubuntu0.18.04.1) ...[/COLOR]
[COLOR=#808080]update-initramfs: deferring update (trigger activated)[/COLOR]
[COLOR=#808080]Purging configuration files for nvidia-compute-utils-525 (525.78.01-0ubuntu0.18.04.1) ...[/COLOR]
[COLOR=#808080]Purging configuration files for nvidia-dkms-515 (515.86.01-0ubuntu0.18.04.1) ...[/COLOR]
[COLOR=#808080]update-initramfs: deferring update (trigger activated)[/COLOR]
[COLOR=#808080]Purging configuration files for nvidia-compute-utils-515 (515.86.01-0ubuntu0.18.04.1) ...[/COLOR]
[COLOR=#808080]Purging configuration files for nvidia-dkms-525 (525.78.01-0ubuntu0.18.04.1) ...[/COLOR]
[COLOR=#808080]update-initramfs: deferring update (trigger activated)[/COLOR]
[COLOR=#808080]Processing triggers for initramfs-tools (0.130ubuntu3.13) ...[/COLOR]
[COLOR=#808080]update-initramfs: Generating /boot/initrd.img-version[/COLOR]
[COLOR=#808080]WARNING: missing /lib/modules/version[/COLOR]
[COLOR=#808080]Ensure all necessary drivers are built into the linux image![/COLOR]
[COLOR=#808080]depmod: ERROR: Bad version passed version[/COLOR]
[COLOR=#808080]dpkg: warning: version 'version' has bad syntax: version number does not start with digit[/COLOR]
[COLOR=#808080]dpkg: warning: version 'version' has bad syntax: version number does not start with digit[/COLOR]
[COLOR=#808080]depmod: ERROR: Bad version passed version
[/COLOR][COLOR=#808080]
[/COLOR]

---

### Post by janderson9er on 2023-02-24
Correction, I was able to get my machine back to booting again. Thank you so much for your help! I was able to chroot in, remove the nvidia drivers and the bad kernel files. Now I can boot the machine, but it's completely unusable again due to no graphics drivers.

The snippet got me most of the way there

**root@lubuntu:/# **[COLOR=#000000]sudo -i[/COLOR]
**root@lubuntu:/# **[COLOR=#000000]cryptsetup luksOpen /dev/sda5 sda5_crypt[/COLOR]
[COLOR=#808080]Enter passphrase for /dev/sda5:[/COLOR]
[COLOR=#000080]**root@lubuntu:/#**[/COLOR][COLOR=#000000] vgchange -ay[/COLOR]
[COLOR=#808080]2 logical volume(s) in volume group "ubuntu-vg" now active[/COLOR]
[COLOR=#000080]**root@lubuntu:/#**[/COLOR][COLOR=#000000] mount /dev/mapper/ubuntu--vg-root /mnt[/COLOR]
[COLOR=#000080]**root@lubuntu:/#**[/COLOR][COLOR=#000000] mount /dev/sda1 /mnt/boot[/COLOR]
[COLOR=#000080]**root@lubuntu:/#**[/COLOR][COLOR=#000000] mount -t proc proc /mnt/proc[/COLOR]
[COLOR=#000080]**root@lubuntu:/#**[/COLOR][COLOR=#000000] mount -o [/COLOR][COLOR=#AA22FF]bind[/COLOR][COLOR=#000000] /dev /mnt/dev[/COLOR]
[COLOR=#000080]**root@lubuntu:/#**[/COLOR][COLOR=#000000] chroot /mnt[/COLOR]


I just needed to run:
[COLOR=#000000]sudo update-initramfs -d -k version[/COLOR] to get rid of the errors.


Where do I go next? From what I've gathered I need to update my kernel and I definitely need to get nvidia drivers installed, but I'm not sure on order. Do I need create another for those questions, or is it appropriate to keep going here?

If it is, I think I can use driver version 470

[FONT=Arial]ubuntu-drivers devices[/FONT]
[FONT=Arial]WARNING:root:_pkg_get_support nvidia-driver-515: package has invalid Support PBheader, cannot determine support level[/FONT]
[FONT=Arial]WARNING:root:_pkg_get_support nvidia-driver-525: package has invalid Support PBheader, cannot determine support level[/FONT]
[FONT=Arial]WARNING:root:_pkg_get_support nvidia-driver-510: package has invalid Support PBheader, cannot determine support level[/FONT]
[FONT=Arial]WARNING:root:_pkg_get_support nvidia-driver-515: package has invalid Support PBheader, cannot determine support level[/FONT]
[FONT=Arial]WARNING:root:_pkg_get_support nvidia-driver-525: package has invalid Support PBheader, cannot determine support level[/FONT]
[FONT=Arial]WARNING:root:_pkg_get_support nvidia-driver-510: package has invalid Support PBheader, cannot determine support level[/FONT]
[FONT=Arial]== /sys/devices/pci0000:00/0000:[/FONT][FONT=Arial]00:01.1/0000:02:00.0 ==[/FONT]
[FONT=Arial]modalias : pci:[/FONT][FONT=Arial]v000010DEd00001F07sv00003842sd[/FONT][FONT=Arial]00002173bc03sc00i00[/FONT]
[FONT=Arial]vendor   : NVIDIA Corporation[/FONT]
[FONT=Arial]driver   : nvidia-driver-470 - third-party non-free recommended[/FONT]
[FONT=Arial]driver   : nvidia-driver-515 - third-party non-free[/FONT]
[FONT=Arial]driver   : nvidia-driver-525 - third-party non-free[/FONT]
[FONT=Arial]driver   : nvidia-driver-510 - third-party non-free[/FONT]
[FONT=Arial]driver   : xserver-xorg-video-nouveau - distro free builtin[/FONT]

Is the next step as easy as sudo apt install nvidia-470?

---

### Post by MAFoElffen on 2023-02-25
You could do it 3 different ways
1. Ubuntu Software and Updates > additional Drivers tab > choose the Nvidia 470 driver from the list. > Choose install

OR

2. 
```

sudo apt install nvidia-driver 470

```

OR

3. 
```

sudo ubuntu-drivers install nvidia:470

```

---

### Post by janderson9er on 2023-02-25
Thank you, that got me to the next step! It looks like the driver works (my login screen is in 4k resolution), but now when I try to login it goes to black screen briefly, and then kicks me back to the login screen.

I ran [COLOR=#111111][FONT=monospace]sudo apt install nvidia-driver-470[/FONT][/COLOR] and it appeared to work with no problems, [pastebin results here.]("https://pastebin.ubuntu.com/p/6tTvQ4rwqN/")

I was able to get to terminal again with [COLOR=#000000][FONT=&amp]--- nomodeset --verbose debug 3[/FONT][/COLOR], no errors there when it loaded besides it says I have 18 packages that I can update.

 nvidia-smi shows the error that it can't communicate with the NVIDIA driver. 

I probably need to nuke those drivers and install a different way or older version?

Thank you so much for your help so far!

---

### Post by MAFoElffen on 2023-02-25
Just to make sure you don't have other problems
```

mafoelffen@Mikes-ThinkPad-T520:~$ ls -lh ~/.Xauthority
-rw------- 1 mafoelffen mafoelffen 64 Feb 15 22:19 /home/mafoelffen/.Xauthority

```
Your's should be same permissions, owned by your userid

Just confirm that please. That way you are not chasing ghosts, by an additional problem.

---

### Post by janderson9er on 2023-02-25
Odd. That file does not exist.

---

### Post by janderson9er on 2023-02-25
Thanks as always! 

I created that file with touch, made sure permissions were set correctly (chmod 600, owned by me), and rebooted. I am seeing the same problem.

---

### Post by MAFoElffen on 2023-02-26
Xorg or Wayland?

---

### Post by janderson9er on 2023-02-26
I'm not sure.. I think Xorg.

cat /etc/X11/default-display-manager
/usr/sbin/gdm3

echo $WAYLAND_DISPLAY and echo $XDG_SESSION_TYPE are both empty. I'm not sure if that's because I am accessing terminal by adding the --- nomodeset bit to grub.

I didn't see another easy way to tell with just terminal access.

---

### Post by janderson9er on 2023-02-26
From the regular login screen "Ubuntu" is selected, and "Ubuntu on Wayland" is an option (but is not selected). I also see that I have [COLOR=#000000][FONT=Arial]driver : xserver-xorg-video-nouveau - distro free builtin[/FONT][/COLOR] as an option for drivers above, if that helps any.

I also see options to login with i3 and i3 (with debug log) too, though I don't use i3 and that can be nuked if we think it's a problem.

Update: Logging in with "Ubuntu on Wayland" worked. I'm at my desktop, the resolution is in 4k, and things look good.

I'm not sure what next, but I'm so glad to be back in!

---

### Post by janderson9er on 2023-02-27
Edit: fsck fixed errors I was seeing.

---

### Post by janderson9er on 2023-03-05
Edit: Not relevant, will update when I am stuck. Thanks!

---

### Post by janderson9er on 2023-03-05
I'm so sorry, I am back to being unable to boot again.

Since my last post, I was able to:
- upgrade to Ubuntu 20 (this had no problems - only had to remove postgis extension and stop postgres service). I don't have these commands saved, but it was more or less [this process]("https://cloudinfrastructureservices.co.uk/how-to-upgrade-ubuntu-18-04-to-20-04-command-line/").
- boot into my system normally, and work through multiple reboots with no issues.

Unfortunately, I am stuck again unable to boot into recovery or normal "Ubuntu" from the menu. The only symptom I noticed was I was getting strange read-only errors when I tried to do anything, and upon re-boot I can't get in to access anything. One thing I did do was update my [grub settings]("https://i.imgur.com/JFheBVD.jpg") to add a brightness control flag to try to fix a bug with Wayland I was running into where it would not wake up.

When I try to boot, I only have one kernel option when I try to boot ([see image]("https://i.imgur.com/bRC9ahi.jpg")), and it's odd that it's the same one (4.15.0.91) as before I upgraded my linux version.

I used Boot Repaid disk to chroot in again, and it looks like I have the wrong kernel in my grub and boot director.

```

[FONT=Arial]uname -r[/FONT]
[FONT=Arial]5.3.0-28-generic
[/FONT]
```

My boot directory does not have any references to the updated kernel, which is presumably why it won't boot?
```

[FONT=Arial]root@lubuntu:/boot# ls -l[/FONT]
[FONT=Arial]total 200384[/FONT]
[FONT=Arial]-rw------- 1 root root   4069388 Feb 28  2020 System.map-4.15.0-91-generic[/FONT]
[FONT=Arial]-rw-r--r-- 1 root root    217457 Feb 28  2020 config-4.15.0-91-generic[/FONT]
[FONT=Arial]drwxr-xr-x 5 root root      4096 Mar  4 13:35 grub[/FONT]
[FONT=Arial]-rw-r--r-- 1 root root 120343044 Mar  4 13:36 initrd.img-4.15.0-91-generic[/FONT]
[FONT=Arial]-rw-r--r-- 1 root root  71597056 Mar  5 11:23 initrd.img-4.15.0-91-generic.[/FONT][FONT=Arial]new[/FONT]
[FONT=Arial]drwx------ 2 root root     16384 Dec 25  2018 lost+found[/FONT]
[FONT=Arial]-rw-r--r-- 1 root root    182704 Aug 18  2020 memtest86+.bin[/FONT]
[FONT=Arial]-rw-r--r-- 1 root root    184380 Aug 18  2020 memtest86+.elf[/FONT]
[FONT=Arial]-rw-r--r-- 1 root root    184884 Aug 18  2020 memtest86+_multiboot.bin[/FONT]
[FONT=Arial]-rw------- 1 root root   8375960 Feb 28  2020 vmlinuz-4.15.0-91-generic
[/FONT]
```

I'm definitely running v20 and not 18.
```

[FONT=Arial]lsb_release -a[/FONT]
[FONT=Arial]No LSB modules are available.[/FONT]
[FONT=Arial]Distributor ID: Ubuntu[/FONT]
[FONT=Arial]Description: Ubuntu 20.04.5 LTS[/FONT]
[FONT=Arial]Release: 20.04[/FONT]
[FONT=Arial]Codename: focal
[/FONT]
```

Does it make sense to try to install a new version of kernel 5.3 or even 5.4 (since that appears to be still supported)? I'm very confused as to why the old kernel files are in my /boot directory.

---

### Post by MAFoElffen on 2023-03-05
Yes... It should be running a 5 series kernel (???),. What happens if you reinstall 'linux-image-generic'? Maybe first do
```

apt-cache show linux-image-generic

```
So we see what is going on, or what it thinks it should be(?)

---

### Post by janderson9er on 2023-03-05
Thank you so much for the quick reply. I'm chroot in Boot Repair, let me know if I should be running this from elsewhere.

```

root@lubuntu:/mnt# apt-cache show linux-image-generic
Package: linux-image-generic
Architecture: amd64
Version: 5.4.0.144.142
Priority: optional
Section: kernel
Source: linux-meta
Origin: Ubuntu
Maintainer: Ubuntu Kernel Team <[EMAIL="kernel-team@lists.ubuntu.com"]kernel-team@lists.ubuntu.com[/EMAIL]>
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Installed-Size: 19
Provides: virtualbox-guest-modules (= 6.1.38-dfsg-3~ubuntu1.20.04.1), wireguard-modules (= 1.0.20201112-1~20.04.1), zfs-modules (= 0.8.3-1ubuntu12.14)
Depends: linux-image-5.4.0-144-generic, linux-modules-extra-5.4.0-144-generic, linux-firmware, intel-microcode, amd64-microcode
Recommends: thermald
Filename: pool/main/l/linux-meta/linux-image-generic_5.4.0.144.142_amd64.deb
Size: 2484
MD5sum: 32406a7e83a779b9dfe637d281d993b7
SHA1: 690e0856c12c74d27b25cae0d3122571ffc06a06
SHA256: 6976ea365d4014a3d4bfcad01eb6364fbbd66dda7c15f42e897c9f6054840af2
SHA512: bb42fbff4da3e6f837aa4e4910ed5822ae45e9be4302475b84ed0216f5c9ccf114db754310d687e7b7d03224fbd15d4a1abce9eb0819cb97aa30a6d3d51b38cb
Description-en: Generic Linux kernel image
 This package will always depend on the latest generic kernel image
 available.
Description-md5: 6d632579c673704f44b290b16e7dbfd1

Package: linux-image-generic
Architecture: amd64
Version: 5.4.0.26.32
Priority: optional
Section: kernel
Source: linux-meta
Origin: Ubuntu
Maintainer: Ubuntu Kernel Team <[EMAIL="kernel-team@lists.ubuntu.com"]kernel-team@lists.ubuntu.com[/EMAIL]>
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Installed-Size: 17
Provides: virtualbox-guest-modules (= 6.1.6-dfsg-1), wireguard-modules (= 1.0.20200413-1), zfs-modules (= 0.8.3-1ubuntu12)
Depends: linux-image-5.4.0-26-generic, linux-modules-extra-5.4.0-26-generic, linux-firmware, intel-microcode, amd64-microcode
Recommends: thermald
Filename: pool/main/l/linux-meta/linux-image-generic_5.4.0.26.32_amd64.deb
Size: 2796
MD5sum: fd483ee4e46f33d24e2b36326fc98215
SHA1: d02ce212a52d92673731300b7dd7f30b1e6b258a
SHA256: aaafef0ec69631b7bf3e283626049598e8e48be8d48b189722e4788b7e9134c2
Description-en: Generic Linux kernel image
 This package will always depend on the latest generic kernel image
 available.
Description-md5: 6d632579c673704f44b290b16e7dbfd1

```

Also seeing:
```

[FONT=Arial]sudo update-grub[/FONT]
[FONT=Arial]Sourcing file `/etc/default/grub'[/FONT]
[FONT=Arial]Sourcing file `/etc/default/grub.d/init-[/FONT][FONT=Arial]select.cfg'[/FONT]
[FONT=Arial]Generating grub configuration file ...[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda2": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda2": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda2": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda2": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda2": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda2": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]  Failed to find sysfs mount point[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda2": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]  Failed to find sysfs mount point[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Found linux image: /boot/vmlinuz-4.15.0-91-[/FONT][FONT=Arial]generic[/FONT]
[FONT=Arial]Found initrd image: /boot/initrd.img-4.15.0-91-[/FONT][FONT=Arial]generic[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda2": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda2": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda2": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda2": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]  Failed to find sysfs mount point[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda2": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]  Failed to find sysfs mount point[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda2": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda2": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda2": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda2": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda5": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Unknown device "/dev/sda1": No such device[/FONT]
[FONT=Arial]Found memtest86+ image: /memtest86+.elf[/FONT]
[FONT=Arial]Found memtest86+ image: /memtest86+.bin[/FONT]
[FONT=Arial]Cannot find list of partitions!  (Try mounting /sys.)[/FONT]
[FONT=Arial]done
[/FONT]
```

---

### Post by MAFoElffen on 2023-03-05
Then try 
```

sudo apt install --reinstall linux-image-generic
sudo update-initramfs -c -k all

```
Then get out of the chroot and try to reboot. Crossing fingers.

---

### Post by janderson9er on 2023-03-05
We're further along, at least. I see 5.4.0-144 generic as an option in Grub boot menu, but it boots me to BusyBox / initramfs prompt. 

I had to re-do my mount and include /sys, but those commands works (with the exception of complaining about /pts not mounted, but that was for logs I believe). 
No errors when I ran those commands.

Booting 5.4.0-144 generic in recovery mode hangs after attaching drives, never getting to encrypt my drive or any prompt.

---

### Post by janderson9er on 2023-03-05
You are the best! Do you have a bitcoin address, paypal, or favorite charity I can donate to on your behalf?

When I booted to 5.4.0-144 initramfs prompt and tried to exit, it finally gave me a useful error related to problems with [COLOR=#000000]/dev/mapper/ubuntu--vg-root.[/COLOR] 

I booted with the repair disk, decrypted that drive and ran [COLOR=#000000]vgchange -ay, [/COLOR] and ran fsck on it and I am back in.

Is there anything I should do now to get rid of that old kernel? I have no idea how I ran into trouble in the first place, but this is the second time I ran into a read-only issue that required fsck to fix it.

---

### Post by MAFoElffen on 2023-03-06
LOL. You can PM me...

To find and get rid of that kernel and it's associated packages: 
```

dpkg --list | egrep -i --color '4.15.0-91-generic' | awk '{ print $2 }'
# then uninstall those packages via
sudo apt remove --purge <package_name>

```

---

