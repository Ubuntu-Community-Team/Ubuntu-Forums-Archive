---
title: "I need help to increase the /boot partition, please"
date: 2022-01-31
forum: Installation &amp; Upgrades
---

### Post by Paddy Landau on 2022-01-31
Going to update my Ubuntu 20.04 today, Software Updater greets me with this message:
> **Not enough free disk space**
The upgrade needs a total of 235 M free space on disk '/boot'. Please free at least an additional 29.4 M of disk space on '/boot'. You can remove old kernels using 'sudo apt autoremove', and you could also set COMPRESS=xz in /etc/initramfs-tools/initramfs.conf to reduce the size of your initramfs.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289932&stc=1[/IMG]

I've already removed old kernels with sudo apt autoremove.

So, I changed COMPRESS=lz4 to COMPRESS=xz in initramfs.conf as recommended. I followed this by rebuilding Grub with sudo update-grub

I restarted the machine, and unfortunately, Software Updater is still giving me this error message.

My only solution is to increase the size of /boot. I understand that /boot should be a minimum of 500 Mb. Mine is already 732 Mb.

**[SIZE=3]Background[/SIZE]**

When I installed Ubuntu, I used the full-disk encryption method. So, Ubuntu created and sized the partitions for me.

The following shows the output from parted.

```
$ sudo parted --list /dev/nvme0n1
Disk /dev/mapper/vgubuntu-root: 510GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End    Size   File system  Flags
 1      0.00B  510GB  510GB  ext4


Error: /dev/mapper/nvme0n1p3_crypt: unrecognised disk label
Model: Linux device-mapper (crypt) (dm)                                   
Disk /dev/mapper/nvme0n1p3_crypt: 511GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 


Model: PM981a NVMe Samsung 512GB (nvme)
Disk /dev/nvme0n1: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size   File system  Name                  Flags
 1      1049kB  538MB   537MB  fat32        EFI System Partition  boot, esp
 2      538MB   1305MB  768MB  ext4         Boot
 3      1305MB  512GB   511GB               System

```
The free space on the first two partitions is:
1: 471 Mb
2: 206 Mb

The "System" partition contains my encrypted disk, as follows.
/dev/nvme0n1p3: LUKS-encrypted disk
/dev/mapper/nvme0n1p3_crypt: LVM partition, containing / (root).

There is no complication to the structure; it's just a single LVM logical partition within LUKS, with no separate /home or other partition.

I have plenty of free space (297 Gb) on my root folder.

**[SIZE=3]My question[/SIZE]**

How do I reduce the size of the LVM-LUKS partition without losing my data, so that I can increase the size of /boot, please? I'm happy to start from a Live USB if that's necessary.

**Side comment:**

As my machine was set up the default way, aren't there many complaints from other Ubuntu users? If not, why do I have this problem? I haven't messed around with /boot.

---

### Post by oldfred on 2022-01-31
It used to be a regular issue when /boot was small.
You have a generous /boot.
I have desktop without LVM and my boot folder is about 200MB, you have a /boot of 768MB.
So question is what is in /boot besides the normal 2 kernels?

---

### Post by Paddy Landau on 2022-01-31
> **oldfred said:**
> question is what is in /boot besides the normal 2 kernels?
Good question!

Here are the folder sizes:
```
$ sudo du --total --human-readable --one-file-system /boot
4.0K    /boot/grub/themes
3.4M    /boot/grub/x86_64-efi
2.3M    /boot/grub/fonts
8.5M    /boot/grub
16K    /boot/lost+found
456M    /boot
456M    total
```
I see that I have several kernels, as follows.

[LIST]
[*]5.8.0-63
[*]5.11.0-46
[*]5.13.0-25
[*]5.13.0-27
[/LIST]
The system wants to install 5.13.0-28.

Removing 5.8.0-63 is pointless, because it will be replaced with 5.8.0-63-unsigned.
I can remove 5.11.0-46.

Bearing in mind that the upgrade needs 235 Mb, that makes &#8531; of the partition, for just one image. That means that space is tight. /boot should surely be larger than 3×image size.

I'm going to remove 5.11.0-46, restart, and see what happens. I'll report back here.

---

### Post by Paddy Landau on 2022-01-31
Well, that worked! Thank you, @oldfred, for asking the right question!

In the end, it only needed 121 Mb of the partition, so I don't know why Software Updater thought that it would need 235 Mb. My /boot partition is now 45% full (leaving 372 Mb free), according to System Monitor. That's still tight, in my opinion, but should be OK at least until I install 22.04.

As you have only 200 Mb on your /boot partition, and presumably only a small portion of that free, it seems that you won't be able to update your Linux kernel?

---

### Post by Paddy Landau on 2022-01-31
I'd still like to know how to increase the /boot partition, in case this problem recurs in the future.

---

### Post by ubfan1 on 2022-01-31
My uncompressed initrd kernels take about 70GB, so 200GB is tight for keeping three kernels, but you could purge the backup kernel before updates and never have three.  Also look around for any leftover initrds from deleted kernels, sometimes they get left around and take up a lot of room.  The askubuntu site has many /boot too small answers, but your logical volume might be an additional tweak.  If the disk reorg is too messy, consider just booting off another device, like a USB, no room problems, no disk reorg, and maybe even an additional security feature (remove the USB). ;^)

---

### Post by Paddy Landau on 2022-01-31
> **ubfan1 said:**
> … you could purge the backup kernel before updates and never have three.
The way Ubuntu works, it automatically removes old kernels apart from the latest two. That way, there's always a working backup if the newest one fails to boot.

However, there's a third very old one (5.8.0-63) that's required from some dependency (I don't know why). All that I can do with it is replace it with an unsigned copy, which is pointless.

So, I have to have three.

> **ubfan1 said:**
> … look around for any leftover initrds from deleted kernels…
I don't know what they might be, but I suspect that you mean files initrd.img*. Here are all the files in /boot:
```
drwx------ 3 root root      4096 1970-01-01 01:00:00 efi
drwxr-xr-x 5 root root      4096 2022-01-31 15:47:35 grub
drwx------ 2 root root     16384 2020-09-05 15:32:17 lost+found
-rw------- 1 root root   5958177 2022-01-13 23:11:18 System.map-5.13.0-27-generic
-rw------- 1 root root   5959931 2022-01-19 11:16:34 System.map-5.13.0-28-generic
-rw------- 1 root root   5534491 2021-07-15 14:51:00 System.map-5.8.0-63-generic
-rw-r--r-- 1 root root    257683 2022-01-13 23:11:18 config-5.13.0-27-generic
-rw-r--r-- 1 root root    257734 2022-01-19 11:16:34 config-5.13.0-28-generic
-rw-r--r-- 1 root root    248322 2021-07-15 14:51:00 config-5.8.0-63-generic
lrwxrwxrwx 1 root root        28 2022-01-31 15:46:33 initrd.img -> initrd.img-5.13.0-28-generic
-rw-r--r-- 1 root root 103807648 2022-01-18 20:34:06 initrd.img-5.13.0-27-generic
-rw-r--r-- 1 root root  57788104 2022-01-31 15:46:55 initrd.img-5.13.0-28-generic
-rw-r--r-- 1 root root  92076769 2022-01-13 15:53:57 initrd.img-5.8.0-63-generic
lrwxrwxrwx 1 root root        28 2022-01-31 15:46:33 initrd.img.old -> initrd.img-5.13.0-27-generic
-rw-r--r-- 1 root root    182704 2020-08-18 11:46:05 memtest86+.bin
-rw-r--r-- 1 root root    184380 2020-08-18 11:46:05 memtest86+.elf
-rw-r--r-- 1 root root    184884 2020-08-18 11:46:05 memtest86+_multiboot.bin
lrwxrwxrwx 1 root root        25 2022-01-31 15:46:33 vmlinuz -> vmlinuz-5.13.0-28-generic
-rw------- 1 root root  10161824 2022-01-13 23:50:26 vmlinuz-5.13.0-27-generic
-rw------- 1 root root  10170592 2022-01-19 13:43:11 vmlinuz-5.13.0-28-generic
-rw------- 1 root root   9800288 2021-07-15 15:06:49 vmlinuz-5.8.0-63-generic
lrwxrwxrwx 1 root root        25 2022-01-31 15:46:33 vmlinuz.old -> vmlinuz-5.13.0-27-generic
```
As far as I can tell (with my admittedly limited knowledge), that looks correct.

---

### Post by rsteinmetz70112 on 2022-01-31
If you run ```
apt autoremove  -s
``` to simulate the autoremove what does it want to remove?
Running ```
apt autoremove --purge 
``` will remove any old configuration files related to the kernels.

In order to enlarge the /boot partition you need to create space to enlarge it. 
Since you have lvm installed you will need to adjust the size of the volume groups before you decrease the size of the physical volume and partition. Then enlarge the /boot partition.
Please post the results of```
 lsblk
``` which will show all of the devices.

---

### Post by TheFu on 2022-01-31
> **Paddy Landau said:**
> I'd still like to know how to increase the /boot partition, in case this problem recurs in the future.

It is non-trivial to resize the encrypted partition, PV, VG and LVs inside it and involves byte-math in may stages. In the end, I was less and less generous in my rounding off of numbers as I worked from the partition size to the PV size to the VG size to the LV sizes and I went out of my way NOT to ever fully allocate the VG - think it is about 50% used even today.
If the system is already setup (not install time), then you'll definitely need to do this from alternate boot media.

If you can, during the install, after the partitions are written, but before anything is copied or created, change to a different TTY and use sgdisk to get the sizes you want.  I've been doing this for non-encrypted installs for the last 8-ish months. Don't know if it is possible with LUKS, since none of the PV, VG, LVs can be created prior to the LUKS container being created.

You know, if might be possible to to work some LVM magic, by using 2 HDDs.  Install to a very small disk and let the installer do what it does.  Then pull that disk out and put in the normal-sized disk, create the partitions of the sizes you want, in the same order as the first disk (need th partition numbers to match, with some spacing after the boot and efi partitions which can be expanded into, and clone the partition that is the LUKS stuff with LVM inside to the larger storage.  

Say you have:```

DEV=/dev/sda
# Part  mount           part_type       fs_type size
1       /boot/efi       EFI             fat32   50MB (dual+boot needs more)
2       /boot           LINUX           ext2    600MB
3       LVM             LVM             na      Remaining storage
 root   /               LV              ext4    35GB
 home   /home           LV              ext4    40GB
 var    /var            LV              ext4    1GB 
 swap   swap            LV/SWAP         swap    4.1GB 
```
on the "small disk"
And setup 
```
DEV=/dev/sda
# Part  mount           part_type       fs_type size
1       /boot/efi       EFI             fat32   50MB (dual+boot needs more)
[COLOR="#FF0000"]4       empty                                   50MB
[/COLOR]2       /boot           LINUX           ext2    600MB
[COLOR="#FF0000"]5       empty                                   250MB[/COLOR]
3       LVM             LVM             na      [COLOR="#FF0000"]old storage sized[/COLOR]
 root   /               LV              ext4    35GB
 home   /home           LV              ext4    40GB
 var    /var            LV              ext4    1GB
 swap   swap            LV/SWAP         swap    4.1GB
[COLOR="#FF0000"]6       LVM             LVM             na      Remaining storage[/COLOR]
```
on the new, larger, disk.

Does that make sense?

Then you can add partition 6 of whatever size, put a LUKS container inside, then PV, and add that PV to the existing VG and it will be available as extended storage for the existing root, home, var and swap LVs already there.  The /etc/crypttab will need both LUKS containers inside it and you'll need to ensure that both of those containers have the same slots used for unlocking.  I've never done this, BTW.
Also, the fstab will need to be modified for the UUIDs or whatever symlink you use to mount storage (I like to use LABEL=) and grub-install/update-grub will need to be run.

[https://unix.stackexchange.com/questions/320957/extend-a-luks-encrypted-partition-to-fill-disk](https://unix.stackexchange.com/questions/320957/extend-a-luks-encrypted-partition-to-fill-disk) has steps. I didn't see it until after I'd written everything else. The solution in the link assumes swaping in a new storage device too.

There appears to be a Qt tool, partitionmanager which can handle LUKS stuff. Might be worth having an LXQt boot flash just for this stuff. I don't know and don't have time to check it out tonight.

---

### Post by Paddy Landau on 2022-02-01
> **rsteinmetz70112 said:**
> If you run apt autoremove  -s…
Ubuntu automatically runs autoremove when starting Software Updater after installing a new kernel. I also do it manually when I uninstall packages. So, there's nothing to autoremove at this point. I didn't know about --purge, though.

Here are the results of lsblk, with all the snap loops removed.
```
NAME                MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
|-nvme0n1p1         259:1    0   512M  0 part  /boot/efi
|-nvme0n1p2         259:2    0   732M  0 part  /boot
`-nvme0n1p3         259:3    0 475.7G  0 part  
  `-nvme0n1p3_crypt 253:0    0 475.7G  0 crypt 
    `-vgubuntu-root 253:1    0 474.8G  0 lvm   /
```
> **TheFu said:**
> It is non-trivial to resize the encrypted partition, PV, VG and LVs inside it and involves byte-math in may stages…
Thank you for all of the information and the link. I'll have a closer look later today when I have some time.

---

### Post by KBar on 2022-02-01
> **Paddy Landau said:**
> I didn't know about --purge, though.

Sorry, not related to the thread but there is also [FONT=courier new]apt autopurge[/FONT]. I'm a bit surprised that **apt**(8) doesn't mention it.

---

### Post by Paddy Landau on 2022-02-01
> **KBar said:**
> … there is also [FONT=courier new]apt autopurge[/FONT]. I'm a bit surprised that **apt**(8) doesn't mention it.
That's interesting. Looking it up, I see that there is an [FONT=courier new]autoclean[/FONT], also not mentioned in the manual.

The manual for [FONT=courier new]apt-get[/FONT] mentions [FONT=courier new]autoclean[/FONT] but not [FONT=courier new]autopurge[/FONT].

I know that you can use [FONT=courier new]apt-get[/FONT] commands with [FONT=courier new]apt[/FONT], so you can use [FONT=courier new]autoclean[/FONT].

I wonder if [FONT=courier new]autopurge[/FONT] has been deprecated?

---

### Post by KBar on 2022-02-01
> **Paddy Landau said:**
> I wonder if [FONT=courier new]autopurge[/FONT] has been deprecated?

It could be but there hasn't been such discussion  in the deity mailing list and it's still in[SUP][[/SUP][SUP][1]("https://salsa.debian.org/apt-team/apt/-/blob/main/cmdline/apt.cc#L70")][/SUP] the[SUP][[2]("https://salsa.debian.org/apt-team/apt/-/blob/main/completions/bash/apt#L42")][/SUP] code[SUP][[3]("https://salsa.debian.org/apt-team/apt/-/blob/main/cmdline/apt-get.cc#L415")][/SUP]. One of the maintainers [acknowledged]("https://lists.debian.org/deity/2019/07/msg00044.html") their existence as "convenience shortcuts".

---

### Post by TheFu on 2022-02-01
These work:
```
sudo apt remove --purge {package names or list}
sudo apt autoremove --purge

```
For example:
```
sudo apt remove --purge nano
```

Every few months, I'll run a dpkg+awk command to purge all removed packages .. not just kernels from the system. I have to look up the command every time.  
```
::::::::::::::
purge-linux-pkgs
::::::::::::::

dpkg -l | awk '/^rc/{print $2}'
```
Feed that into xargs with sudo apt purge ... bam, all cleaned.  I like to look through the package list first to see what is being purged. They've already been "removed", so the dangers isn't very high at all:

```
$ dpkg -l | awk '/^rc/{print $2}'
cockpit-ws
containerd
dnsmasq-base
fluid-soundfont-gs
libpwquality-common
linux-image-5.4.0-89-generic
linux-modules-5.4.0-89-generic
linux-modules-extra-5.4.0-89-generic
modemmanager
pptp-linux
systemd-timesyncd
usb-modeswitch
```
Just some stuff I played with, an old kernel and a useless-to-me systemd time module. I use chronyd instead on my network. Whenever I have a problem with a systemd abomination, I replace it with the best of breed solution.  Most of the systemd addons is adequate only, not best of breed, IMHO.

For snaps, I don't want any extra copies of the same packages:

```
snap-remove-disabled
::::::::::::::
#!/bin/sh
set -eu

snap list --all | awk '/disabled/{print $1, $3}' |
    while read snapname revision; do
    echo   /usr/bin/sudo  /usr/bin/snap  remove "$snapname" --revision="$revision"
    done

```
Two different methods to deal with a list of stuff and do some more processing.

---

### Post by Paddy Landau on 2022-02-01
Thanks, @TheFu. I've already removed the unused kernels, so now it's just a matter of expanding my /boot partition.

I've run out of time today, so I'll look tomorrow.

---

### Post by TheFu on 2022-02-01
I find this alias for lsblk very useful:
```
alias lsblkt='lsblk -e 7 -o name,size,type,fstype,mountpoint'
```
Junk removed. Stuff we need included.

---

### Post by MAFoElffen on 2022-02-01
Since you are running 5.11 through 5.13.x, that means it got updated to  the HWE series of kernels and 5.8.x are not a kernel series you are even  using anymore. The older 5.11 kernel can go also.

The extra  space taken in your /boot tree is being taken up by Grub theming and  fonts... I used to do that in the past, with my own tweaked themed Grub  Boot menus. So yes, I recognize the extra directories there.  ...along  with animated boot splashes, my own lock screen backgrounds and such...  and other things that I used to spend time on to make my installation  "mine".

You can adjust your boot partition easily with a GParted  LiveCD... It is separate from root, on it's own, but you may need to  move the root or shrink it a bit to grow your /boot partition, so it  needs to be "offline" to grow it.  I would increase it to 1G. That's  what I do, and what I have done (when I do create a separate /boot  partition) for about a decade. Average default size is usually 550MB.

Yes, you have extra's, but you have old outdated and unneeded stuff there that is not necessary also.

---

### Post by Paddy Landau on 2022-02-02
> **TheFu said:**
> I find this alias for lsblk very useful…
That is useful, thank you. I've put this into my documentation for future reference.
> **MAFoElffen said:**
> Since you are running 5.11 through 5.13.x, that means it got updated to  the HWE series of kernels and 5.8.x are not a kernel series you are even  using anymore. The older 5.11 kernel can go also.
Thanks. I can't remove 5.8, but I have removed 5.11.
> **MAFoElffen said:**
> The extra  space taken in your /boot tree is being taken up by Grub theming and  fonts...
Interesting! The only theming that I've done is to add a background image. The file is a mere 450 Kb. I've nothing else with theming; apart from the image, it's all default.
> **MAFoElffen said:**
> … along  with animated boot splashes, my own lock screen backgrounds and such…
I hadn't realised that this was possible!
> **MAFoElffen said:**
> You can adjust your boot partition easily with a GParted  LiveCD...
Thanks. That's good to know. I'll take a full backup first, of course.
 > **MAFoElffen said:**
> It is separate from root, on it's own…
Yes, I realise that. The problem is that I need to shrink root, and I'm not sure how to do so given that root is on a LVM logical drive within a LUKS-encrypted  partition. That's where I'm struggling.
> **MAFoElffen said:**
> I would increase it to 1G. … Average default size is usually 550MB.
I've seen the recommended size of 500 MiB, and I agree with you that's it's much too small. Your size of 1 Gb seems like a good suggestion.

---

### Post by TheFu on 2022-02-02
> **Paddy Landau said:**
> 
I've seen the recommended size of 500 MiB, and I agree with you that's it's much too small. Your size of 1 Gb seems like a good suggestion.

500MB can be much too large for some people. A few different systems:
```
$ dft
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/sdb1                         ext2  720M  [COLOR="#FF0000"]168M[/COLOR]  516M  25% /boot
```

```
$ dft
/dev/sda2                                   ext2  237M  [COLOR="#FF0000"]195M[/COLOR]   30M  87% /boot
```

```
$ dft
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sdc1      ext4   20G   13G  6.1G  67% /

```No /boot partition on this install.

```
$ dft
Filesystem                 Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu--root ext4   19G   13G  5.2G  71% /
/dev/vda1                  vfat  511M  [COLOR="#FF0000"]7.1M[/COLOR]  504M   2% /boot/efi
```
no /boot partition on this install either.

All these installs were upgrades from at least 1 prior LTS. One was upgraded from 10.04 --> LTS --> LTS --> LTS.
Perhaps I'm just good at cleaning up old kernels after having an issue around 2011-ish? [https://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt](https://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt) is when I created an inferior script that worked, but was overly complex. Now I just use:
```
sudo apt autoremove
sudo apt autoclean
dpkg -l 'linux*' | awk '/^rc/{print $2}' | xargs sudo apt-get purge -y

```
to get old kernels, modules and headers that are already removed, just not purged to go away.

Setup a boot background image on one of my systems. It usually doesn't work and I don't really reboot systems all that often, but when it does work, it is a nice surprise ... and the images makes reading all the screen text nearly impossible. ;)  For me, the boot image was worth 10 minutes of effort, once, but not any more effort. Certainly not worth trying to fix and I won't down load a boot customizer, since my systems are all single-boot. I mostly use VMs.

---

### Post by him610 on 2022-02-02
> **Paddy Landau said:**
> That's interesting. Looking it up, I see that there is an [FONT=courier new]autoclean[/FONT], also not mentioned in the manual.

The manual for [FONT=courier new]apt-get[/FONT] mentions [FONT=courier new]autoclean[/FONT] but not [FONT=courier new]autopurge[/FONT].

I know that you can use [FONT=courier new]apt-get[/FONT] commands with [FONT=courier new]apt[/FONT], so you can use [FONT=courier new]autoclean[/FONT].

I wonder if [FONT=courier new]autopurge[/FONT] has been deprecated?

extract from *man apt* ....
```

 install, reinstall, remove, ***purge*** (apt-get(8))
           Performs the requested action on one or more packages specified via regex(7), glob(7) or exact match. The
           requested action can be overridden for specific packages by appending a plus (+) to the package name to
           install this package or a minus (-) to remove it.

           A specific version of a package can be selected for installation by following the package name with an
           equals (=) and the version of the package to select. Alternatively the version from a specific release
           can be selected by following the package name with a forward slash (/) and codename (buster, bullseye,
           sid ...) or suite name (stable, testing, unstable). This will also select versions from this release for
           dependencies of this package if needed to satisfy the request.

           Removing a package removes all packaged data, but leaves usually small (modified) user configuration
           files behind, in case the remove was an accident. Just issuing an installation request for the
           accidentally removed package will restore its function as before in that case. On the other hand you can
           get rid of these leftovers by calling purge even on already removed packages. Note that this does not
           affect any data or configuration stored in your home directory.

```

---

### Post by Paddy Landau on 2022-02-03
> **TheFu said:**
> 500MB can be much too large for some people…
I see what you mean! I don't know what dft is, though; maybe it's an alias that you use?
> **TheFu said:**
> ```
dpkg -l 'linux*' | awk '/^rc/{print $2}' | xargs sudo apt-get purge -y
```
Ah, so that's what *rc* means! I finally figured it out, thanks to you :)

One small idea: When I query *dpkg*, I usually use *dpkg-query* on the presumption that I'm less likely to accidentally make a change. *dpkg --list* and *dpkg-query --list* provide identical results.

I ran your command followed by *sudo update-grub*. According to System Monitor, /boot reduced from 313.0 Mb to… 313.0 Mb. So, no apparent difference!

I'm curious as to you how get your /boot to be so small.
> **TheFu said:**
> Setup a boot background image on one of my systems. It usually doesn't work and I don't really reboot systems all that often, but when it does work, it is a nice surprise ... and the images makes reading all the screen text nearly impossible. ;)  For me, the boot image was worth 10 minutes of effort, once, but not any more effort. Certainly not worth trying to fix and I won't down load a boot customizer, since my systems are all single-boot. I mostly use VMs.
I'm a bit unsure of what you're trying to say there. Why would a reboot be surprising when it works? I don't use a boot customizer (I did look at Grub Customizer, but instead I simply manually added a background image).

Using VMs is the best idea wherever possible. I use VirtualBox for my Windows, which I hardly ever use, and for occasional Linux tests.

---

### Post by Paddy Landau on 2022-02-03
> **him610 said:**
> extract from *man apt*…
Thanks; I do know about these. I was wondering about *autopurge* specifically.

---

### Post by TheFu on 2022-02-03
```
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
```

It shows the stuff we want and removes all the junk that is useless.

I don't put extra junk in /boot/. Besides that, nothing special.
Here's what is in a /boot on a system with LVM:
```
$ ls -F
config-5.4.0-94-generic      initrd.img-5.4.0-96-generic  vmlinuz-5.4.0-94-generic
config-5.4.0-96-generic      lost+found/                  vmlinuz-5.4.0-96-generic
grub/                        System.map-5.4.0-94-generic
initrd.img-5.4.0-94-generic  System.map-5.4.0-96-generic

$ df .
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1       720M  [COLOR="#FF0000"]168M[/COLOR]  516M  25% /boot

```

I do NOT dual boot - ever.

---

### Post by Paddy Landau on 2022-02-03
> **TheFu said:**
> ```
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
```
Thank you
> **TheFu said:**
> Here's what is in a /boot on a system with LVM:
It's still half the size of mine.
> **TheFu said:**
> I do NOT dual boot - ever.
Yes, I've also gone that route. When I bought my latest computer, I got an Ubuntu one from Dell with enough RAM to cope with a VM, and installed Windows onto VirtualBox. It's just so much easier that way — and when Windows does its occasional nonsense, reverting to a snapshot does the trick!

---

### Post by MAFoElffen on 2022-02-04
> **Paddy Landau said:**
> Here are the folder sizes:
```
$ sudo du --total --human-readable --one-file-system /boot
4.0K    [COLOR=#ff0000]/boot/grub/**themes**[/COLOR]
3.4M    [COLOR=#008000]/boot/grub/x86_64-efi[/COLOR]
2.3M    [COLOR=#ff0000]/boot/grub/**fonts**[/COLOR]
8.5M    [COLOR=#008000]/boot/grub
16K    /boot/lost+found
456M    /boot[/COLOR]
456M    total
```

Key:
[COLOR=#008000]Green[/COLOR]=Default/installed by system
[COLOR=#ff0000]Red[/COLOR]=Installed manually by User

---

### Post by Paddy Landau on 2022-02-04
> **MAFoElffen said:**
> [COLOR=#008000]Green[/COLOR]=Default/installed by system
[COLOR=#ff0000]Red[/COLOR]=Installed manually by User
Thank you for this.

The themes folder is empty. I don't know why it's there, as I have no recollection of adding it. It's empty, so I don't think that I need to concern myself with it.

The fonts folder contains a file called unicode.pf2 with size 2.3 Mb. Looking on the internet, it seems that many people with different distributions have had a problem where Grub complains about not finding file unicode.pf2, so it looks as though it should be there.

I've compared this to a test installation of Lubuntu 20.04 that I hold on a VM. I most definitely haven't played with its Grub. It doesn't have a themes folder, but it has fonts/unicode.pf2.

As an experiment, I deleted that file on my VM. Grub still worked, but the display was messy. See the attached screenshot.

So, fonts/unicode.pf2 appears to be installed by default, at least on some distributions. Which distribution do you have?

As their total space is a mere 2.3 Mb, I'm not going to worry about them.

---

### Post by KBar on 2022-02-04
On Xubuntu 20.04, I also have the *fonts* directory in */boot/grub* and it contains *unicode.pf2.* However, this file is present in the parent *grub* directory as well. 

Removing this file probably messes up the text mode support.

---

### Post by Paddy Landau on 2022-02-04
> **KBar said:**
> … this file is present in the parent *grub* directory as well.
I missed that. The same is true for me on both Ubuntu 20.04 and Lubuntu 20.04. All four files are all identical.
> **KBar said:**
> Removing this file probably messes up the text mode support.
Indeed it does; see the screenshot in my previous post. Not just the border but also the instructions.

---

