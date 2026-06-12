---
title: "grub-rescue cannot see btrfs root content after latest dist-upgrade"
date: 2017-12-11
forum: Installation &amp; Upgrades
---

### Post by jacklh on 2017-12-11
**tl;dr: **Why is grub v2 suddenly unable to see ANY files in root after reboot following 'sudo apt-get update && sudo dist-upgrade'?
```

[COLOR=#b22222]**error: file '/@/boot/grub/i386-pc/normal.mod' not found.**[/COLOR]
```

```
[B]grub rescue> ls (hd0,msdos1)/@
[/B]
```[blank line printed]

yet data can be seen on the drive outside the btrfs @ subvolume:

```
**grub rescue> ls (hd0,msdos1)/**
```
[prints all the apt-snapshot btrfs snapshots, etc, including @; see attached pics]

**DETAILS:**
Here's my setup. I run Lubuntu 16.04 as a guest VM on ESXi 6.5.0 with an unencrypted btrfs root partition on RAID5 (physical, NOT using btrfs RAID). After performing this week's dist-upgrade (which I've performed just fine for many weeks on end)....

```
sudo apt-get update && sudo dist-upgrade

```
...and having it auto install a new kernel and [I assume it] performing grub-updates, etc, then on reboot I get the grub-rescue prompt following this error: 

```
[COLOR=#b22222][B]error: file '/@/boot/grub/i386-pc/normal.mod' not found.
[/B][/COLOR]Entering rescue mode...

```
When I perform an 'ls' where the root data should be, it's blank!!! 

```
**grub rescue> ls (hd0,msdos1)/@**

```[blank line printed]

But I can clearly see other data on the RAID logical drive just fine.
```
**grub rescue> ls (hd0,msdos1)/**

```[prints all the apt-snapshot btrfs snapshots, etc, including @; see attached pics below]

But if I boot into my Lubuntu rescue CD and mount the RAID drive (e.g. mount -t btrfs -o compress=lzo [/dev/sda]("https://ubuntuforums.org/dev/sda")[/mnt/rootfs),]("https://ubuntuforums.org/mnt/rootfs),") I can clearly see the same aforementioned data (from ls (hd0,msdos1)), INCLUDING the root contents of [/mnt/rootfs/@,]("https://ubuntuforums.org/mnt/rootfs/@,")[/mnt/rootfs/@/boot]("https://ubuntuforums.org/mnt/rootfs/@/boot") and [/mnt/rootfs/@/boot/grub.]("https://ubuntuforums.org/mnt/rootfs/@/boot/grub.") The data is all there and permissions look normal.

How is grub just not seeing this?

I can even perform the following just fine and grub has no issues reading the data and performing this successfully:
```
sudo grub&#8208;install &#8208;&#8208;root&#8208;directory=/mnt/rootfs/@ [/dev/sda]("https://ubuntuforums.org/dev/sda")
```

Result is the same on reboot.

If I recover @ by replacing with a snapshot from the previous apt-snapshot prior to the latest dist-upgrade, I can boot back fine into my guest Lubuntu VM. If I then re-attempt the dist-upgrade, the same situation arises. I've done dist-upgrade dozens of times (once per week), so I don't know what's different other than maybe a goof on the distribution end and I should just wait until next week or weeks for possible auto-fix getting pushed. Anyone else seeing this? Any ideas on things to try. Am I rebooting too soon? I always see "processing triggers". How would I know when safe to reboot following dist-upgrade completing? ("ps -ef | grep apt"?)

```
> uname -a
Linux <removed-hostname> 4.10.0-40-generic #44~16.04.1-Ubuntu SMP Thu Nov 9 15:37:44 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

> sudo apt-get update && sudo apt-get dist-upgrade 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]                                         
Hit:3 [http://ppa.launchpad.net/x2go/stable/ubuntu](http://ppa.launchpad.net/x2go/stable/ubuntu) xenial InRelease                                                            
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]                                                    
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]                                        
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [678 kB]                              
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [637 kB]   
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [565 kB]
Ign:9 [http://www.scootersoftware.com](http://www.scootersoftware.com) bcompare4 InRelease                      
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [529 kB]
Hit:11 [http://www.scootersoftware.com](http://www.scootersoftware.com) bcompare4 Release                        
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe Translation-en [229 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 Packages [16.2 kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse i386 Packages [15.3 kB]
Fetched 2,975 kB in 1s (1,870 kB/s)                                                    
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  libgtkmm-3.0-1v5 linux-headers-4.10.0-42 linux-headers-4.10.0-42-generic linux-image-4.10.0-42-generic linux-image-extra-4.10.0-42-generic pavucontrol
The following packages will be upgraded:
  apport apport-gtk libnm-glib4 libnm-util2 libnm0 libpulse-mainloop-glib0 libpulse0 libpulsedsp libxml2 libxml2-utils linux-firmware linux-generic-hwe-16.04
  linux-headers-generic-hwe-16.04 linux-image-generic-hwe-16.04 linux-libc-dev lubuntu-core lubuntu-desktop lxd lxd-client lxd-tools network-manager pulseaudio
  pulseaudio-module-x11 pulseaudio-utils python3-apport python3-problem-report rsync
27 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/119 MB of archives.
After this operation, 315 MB of additional disk space will be used.

...[SNIP]...

Preparing to unpack .../linux-firmware_1.157.14_all.deb ...
Unpacking linux-firmware (1.157.14) over (1.157.13) ...
Selecting previously unselected package linux-image-4.10.0-42-generic.
Preparing to unpack .../linux-image-4.10.0-42-generic_4.10.0-42.46~16.04.1_amd64.deb ...
Examining [/etc/kernel/preinst.d/]("https://ubuntuforums.org/etc/kernel/preinst.d/")
run-parts: executing [/etc/kernel/preinst.d/intel-microcode]("https://ubuntuforums.org/etc/kernel/preinst.d/intel-microcode") 4.10.0-42-generic [/boot/vmlinuz-4.10.0-42-generic]("https://ubuntuforums.org/boot/vmlinuz-4.10.0-42-generic")
Done.
Unpacking linux-image-4.10.0-42-generic (4.10.0-42.46~16.04.1) ...
Selecting previously unselected package linux-image-extra-4.10.0-42-generic.
Preparing to unpack .../linux-image-extra-4.10.0-42-generic_4.10.0-42.46~16.04.1_amd64.deb ...
Unpacking linux-image-extra-4.10.0-42-generic (4.10.0-42.46~16.04.1) ...
Preparing to unpack .../linux-generic-hwe-16.04_4.10.0.42.44_amd64.deb ...
Unpacking linux-generic-hwe-16.04 (4.10.0.42.44) over (4.10.0.40.42) ...
Preparing to unpack .../linux-image-generic-hwe-16.04_4.10.0.42.44_amd64.deb ...
Unpacking linux-image-generic-hwe-16.04 (4.10.0.42.44) over (4.10.0.40.42) ...
Selecting previously unselected package linux-headers-4.10.0-42.
Preparing to unpack .../linux-headers-4.10.0-42_4.10.0-42.46~16.04.1_all.deb ...
Unpacking linux-headers-4.10.0-42 (4.10.0-42.46~16.04.1) ...
Selecting previously unselected package linux-headers-4.10.0-42-generic.
Preparing to unpack .../linux-headers-4.10.0-42-generic_4.10.0-42.46~16.04.1_amd64.deb ...
Unpacking linux-headers-4.10.0-42-generic (4.10.0-42.46~16.04.1) ...
Preparing to unpack .../linux-headers-generic-hwe-16.04_4.10.0.42.44_amd64.deb ...
Unpacking linux-headers-generic-hwe-16.04 (4.10.0.42.44) over (4.10.0.40.42) ...
Preparing to unpack .../linux-libc-dev_4.4.0-103.126_amd64.deb ...
Unpacking linux-libc-dev:amd64 (4.4.0-103.126) over (4.4.0-101.124) ...
Preparing to unpack .../lubuntu-core_0.65.3_amd64.deb ...
Unpacking lubuntu-core (0.65.3) over (0.65.2) ...
Selecting previously unselected package pavucontrol.
Preparing to unpack .../pavucontrol_3.0-3build1_amd64.deb ...
Unpacking pavucontrol (3.0-3build1) ...
Preparing to unpack .../lubuntu-desktop_0.65.3_amd64.deb ...
Unpacking lubuntu-desktop (0.65.3) over (0.65.2) ...

...[SNIP]...

Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.10.0-42-generic
Found initrd image: /boot/initrd.img-4.10.0-42-generic
Found linux image: /boot/vmlinuz-4.10.0-40-generic
Found initrd image: /boot/initrd.img-4.10.0-40-generic
Found linux image: /boot/vmlinuz-4.10.0-38-generic
Found initrd image: /boot/initrd.img-4.10.0-38-generic
Found memtest86+ image: /@/boot/memtest86+.elf
Found memtest86+ image: /@/boot/memtest86+.bin
done
Setting up linux-image-extra-4.10.0-42-generic (4.10.0-42.46~16.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.10.0-42-generic /boot/vmlinuz-4.10.0-42-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.10.0-42-generic /boot/vmlinuz-4.10.0-42-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.10.0-42-generic /boot/vmlinuz-4.10.0-42-generic
update-initramfs: Generating /boot/initrd.img-4.10.0-42-generic
cryptsetup: WARNING: failed to detect canonical device of /dev/sda1
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.10.0-42-generic /boot/vmlinuz-4.10.0-42-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.10.0-42-generic /boot/vmlinuz-4.10.0-42-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.10.0-42-generic /boot/vmlinuz-4.10.0-42-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.10.0-42-generic
Found initrd image: /boot/initrd.img-4.10.0-42-generic
Found linux image: /boot/vmlinuz-4.10.0-40-generic
Found initrd image: /boot/initrd.img-4.10.0-40-generic
Found linux image: /boot/vmlinuz-4.10.0-38-generic
Found initrd image: /boot/initrd.img-4.10.0-38-generic
Found memtest86+ image: /@/boot/memtest86+.elf
Found memtest86+ image: /@/boot/memtest86+.bin
done
Setting up linux-image-generic-hwe-16.04 (4.10.0.42.44) ...
Setting up linux-headers-4.10.0-42 (4.10.0-42.46~16.04.1) ...
Setting up linux-headers-4.10.0-42-generic (4.10.0-42.46~16.04.1) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.10.0-42-generic /boot/vmlinuz-4.10.0-42-generic
Setting up linux-headers-generic-hwe-16.04 (4.10.0.42.44) ...
Setting up linux-generic-hwe-16.04 (4.10.0.42.44) ...
Setting up linux-libc-dev:amd64 (4.4.0-103.126) ...
Setting up lubuntu-core (0.65.3) ...
Setting up pavucontrol (3.0-3build1) ...
Setting up lubuntu-desktop (0.65.3) ...
Setting up lxd-tools (2.0.11-0ubuntu1~16.04.4) ...
Setting up network-manager (1.2.6-0ubuntu0.16.04.2) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...



```

Grub error and data listing:
[ATTACH=CONFIG]277802[/ATTACH]

Mounting btrfs partition in rescue CD clearly showing the data that grub is failing to see:
[ATTACH=CONFIG]277807[/ATTACH]

Showing permissions on @ are normal:
[ATTACH=CONFIG]277804[/ATTACH]

Showing that grub-install works fine:
[ATTACH=CONFIG]277801[/ATTACH]

Reverting back to last good btrfs snapshot after two failed dist-upgrade attempts on 12/10 and 12/11:
[ATTACH=CONFIG]277805[/ATTACH]

---

### Post by jacklh on 2017-12-11
Well, it's SOLVED and working now and confirmed with multiple reboots/halts.

I attribute this to one of the following:

[LIST=1]
[*]ENOUGH TIME ELAPSED: Having performed apt update and dist-upgrade for a third time just now, perhaps something was recently fixed upstream.
[*]POSSIBLE RACE-CONDITION: Between my hardware detecting the RAID5 array, ESXi and Lubuntu. Perhaps I got lucky on this reboot.
[*]LINUX ELVES UNDER MY DESK (I believe this the most likely scenario.)
[*]EXPLICITLY PERFORMED GRUB UPDATE AND INSTALL:
I did the following immediately after my third dist-upgrade attempt, confirmed no apt processes still running in background and then rebooted:
[/LIST]

```
> sudo -i
> update-grub
Generating grub configuration file ...
Found linux image: [/boot/vmlinuz-4.10.0-42-generic]("https://ubuntuforums.org/boot/vmlinuz-4.10.0-42-generic")
Found initrd image: [/boot/initrd.img-4.10.0-42-generic]("https://ubuntuforums.org/boot/initrd.img-4.10.0-42-generic")
Found linux image: [/boot/vmlinuz-4.10.0-40-generic]("https://ubuntuforums.org/boot/vmlinuz-4.10.0-40-generic")
Found initrd image: [/boot/initrd.img-4.10.0-40-generic]("https://ubuntuforums.org/boot/initrd.img-4.10.0-40-generic")
Found linux image: [/boot/vmlinuz-4.10.0-38-generic]("https://ubuntuforums.org/boot/vmlinuz-4.10.0-38-generic")
Found initrd image: [/boot/initrd.img-4.10.0-38-generic]("https://ubuntuforums.org/boot/initrd.img-4.10.0-38-generic")
Found memtest86+ image: [/@/boot/memtest86+.elf]("https://ubuntuforums.org/@/boot/memtest86+.elf")
Found memtest86+ image: [/@/boot/memtest86+.bin]("https://ubuntuforums.org/@/boot/memtest86+.bin")
done
> grub-install [/dev/sda]("https://ubuntuforums.org/dev/sda")
Installing for i386-pc platform.
Installation finished. No error reported.
>ps -ef | grep apt | grep -v grep
> shutdown -r now

```

...[REBOOTED]...

```
> uname -a
Linux <hostname-removed> 4.10.0-42-generic #46~16.04.1-Ubuntu SMP Mon Dec 4 15:57:59 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by oldos2er on 2017-12-11
Would you please mark your thread Solved using Thread Tools at the top of the page? Thanks.

---

