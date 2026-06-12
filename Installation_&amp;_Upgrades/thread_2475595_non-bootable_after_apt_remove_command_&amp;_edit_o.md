---
title: "non-bootable after apt remove command &amp; edit of .css file (change login background)"
date: 2022-06-01
forum: Installation &amp; Upgrades
---

### Post by kumazenko on 2022-06-01
Hi, recently gave Linux another look, and have to say I've been impressed with how far it has come - enough so to set about a pilot project to prepare for converting our systems over to a new Ubuntu standard, however I hit a frustrating wall.

Setup:
OS: Ubuntu (22.04 LTS, 5.5.0-25)
Disk: nvme01n1
Partitioning: ZFS rpool (w/ auto snap-shots configured)

Context:
Two actions were performed...

A)
After noticing that the GUI uninstall of the Evolution mail client left running services still in play apt list evolution* was performed, and clearly there were many evolution services still running. So, an apt remove evolution* was performed.

After running this it was noticed that many services were being removed having to do with much more than Evolution mail, ie items relating to Wayland. This was concerning, so I reverted back to the last snapshot. All seeContextmed fine after the snapshot restore, so this was ignored.

B)
Next a manual edit of the gnome theme css file was performed (replacing the URL to the default background to a custom image).
After rebooting 

Troubleshooting attempts:
While deeply frustrated that A) attempting to remove an unneeded app could be so involved, B) that such simple intentions such as an app removal / background customization could lead to such a mess, I figured just roll up your sleeves & boot from the install media to either retrieve needed data & rebuild, or preferably to do a refresh of any mangled configs. Well, this has gotten less confidence inspiring.

Reviewing insights from others who needed to repair their ZFS boot volume I found guides to mounting a ZFS volume in such a way (via an emergency USB boot).

However the instructions relating to exporting / mounting the ZFS pool didn't help, still no accessible rpool, and lol now rpool is labeled Restore.

So, I'm stopping the troubleshooting to ask for help. In hindsight, it seems that it would have been advisable to implement [https://zfsbootmenu.org/](https://zfsbootmenu.org/) - so I recognize this could have been perhaps much less frustrating with that in play; #hindsight...

Anyway, I remain excited to continue this journey of transition from Windows to Linux, and am super grateful for your insights into how to proceed.

Thank you!

---

### Post by MAFoElffen on 2022-06-01
To mount and chroot into ZFS-on-root system from a LiveCD, this is what I do...

To summarize:
- Boot from the LiveCD and open a terminal session.
- Do fdisk to check for and identify 'Solaris boot' and 'Solaris root'.
- Do lsblk to identify the rpool name under 'Label'. Keep that rpool name for later.
- Become root.
- Update the apt cache
- Install what is required for ZFS Utils to the LiveCD ENV.
- do a zpool list to show any dataset pools. If none fine. Else export the rpool.
- Do a ZFS List to show if any datasets. If none fine. Else export rpool.
- Import the rpool to the /mnt dierectory
- Do a zfs list to see if it was successful
- Do a ZFS mount of the root to mount the filesystem
- Do a ZFS mount all
- Mount dev, proc, and sys
- Chroot into the installed system
- Remount the mounts oin the target systems fstab
- check the mounts for /boot/efi and /boot/grub
- Do my repairs...
- Before turning powering down the machine, gracefully shutdown the ZFS filesystem
- Unmount the target system's mounts.
- Reboot the system and check the repairs.

Now for details.
Here is a draft script I wrote for my Ama-Gi Project: [https://ubuntuforums.org/showthread....2#post14075362](https://ubuntuforums.org/showthread....2#post14075362)

Here is a terminal log, where I demonstrate how to mount and chrooted into a ZFS-On-Root System, and reinstall grub:

```

ubuntu@ubuntu:~$ sudo fdisk -l 2>&1 | sed '/\/dev\/loop/,+3 d' 2> /dev/null | uniq

Disk /dev/vda: 20 GiB, 21474836480 bytes, 41943040 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 4BD32A91-14FF-40C9-8092-0277030D90F5

Device       Start      End  Sectors  Size Type
/dev/vda1     2048  1050623  1048576  512M EFI System
/dev/vda2  1050624  2940927  1890304  923M Linux swap
/dev/vda3  2940928  4984831  2043904  998M Solaris boot
/dev/vda4  4984832 41943006 36958175 17.6G Solaris root

ubuntu@ubuntu:~$ lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL | grep -v '/snap/'
NAME    SIZE FSTYPE     LABEL                    MOUNTPOINT                   MODEL
loop0     2G squashfs                            /rofs                        
sr0     2.9G iso9660    Ubuntu 20.04.3 LTS amd64 /cdrom                       QEMU_DVD-ROM
vda      20G zfs_member tmprpool                                              
&#9500;&#9472;vda1  512M vfat                                                             
&#9500;&#9472;vda2  923M swap                                [SWAP]                       
&#9500;&#9472;vda3  998M zfs_member tmpbpool                                              
&#9492;&#9472;vda4 17.6G zfs_member tmprpool                                              

ubuntu@ubuntu:~$ sudo -i

root@ubuntu:~# apt update
Ign:1 cdrom://Ubuntu 20.04.3 LTS _Focal Fossa_ - Release amd64 (20210819) focal InRelease
Hit:2 cdrom://Ubuntu 20.04.3 LTS _Focal Fossa_ - Release amd64 (20210819) focal Release
Hit:4 http://security.ubuntu.com/ubuntu focal-security InRelease         
Hit:5 http://archive.ubuntu.com/ubuntu focal InRelease                   
Hit:6 http://archive.ubuntu.com/ubuntu focal-updates InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
265 packages can be upgraded. Run 'apt list --upgradable' to see them.

root@ubuntu:~# apt install --yes zfs-initramfs
# appropriare output for the package install

root@ubuntu:~# zpool list
no pools available

root@ubuntu:~# zfs list
no datasets available

root@ubuntu:~# zpool import -N -R /mnt tmprpool
# Note that this will be either tmprpool or rpool... The specific name is in the 'lsblk' output.

root@ubuntu:~# zfs list
NAME                                                  USED  AVAIL     REFER  MOUNTPOINT
tmprpool                                             7.81G  9.15G       96K  /mnt/mnt/boot-sav/zfs
tmprpool/ROOT                                        7.78G  9.15G       96K  none
tmprpool/ROOT/ubuntu_64fs0l                          7.78G  9.15G     3.52G  /mnt
tmprpool/ROOT/ubuntu_64fs0l/srv                       152K  9.15G       96K  /mnt/srv
tmprpool/ROOT/ubuntu_64fs0l/usr                       408K  9.15G       96K  /mnt/usr
tmprpool/ROOT/ubuntu_64fs0l/usr/local                 312K  9.15G      128K  /mnt/usr/local
tmprpool/ROOT/ubuntu_64fs0l/var                      1.81G  9.15G       96K  /mnt/var
tmprpool/ROOT/ubuntu_64fs0l/var/games                 152K  9.15G       96K  /mnt/var/games
tmprpool/ROOT/ubuntu_64fs0l/var/lib                  1.78G  9.15G     1.57G  /mnt/var/lib
tmprpool/ROOT/ubuntu_64fs0l/var/lib/AccountsService   352K  9.15G      104K  /mnt/var/lib/AccountsService
tmprpool/ROOT/ubuntu_64fs0l/var/lib/NetworkManager    588K  9.15G      132K  /mnt/var/lib/NetworkManager
tmprpool/ROOT/ubuntu_64fs0l/var/lib/apt               106M  9.15G     83.8M  /mnt/var/lib/apt
tmprpool/ROOT/ubuntu_64fs0l/var/lib/dpkg             61.2M  9.15G     36.4M  /mnt/var/lib/dpkg
tmprpool/ROOT/ubuntu_64fs0l/var/log                  21.0M  9.15G     7.55M  /mnt/var/log
tmprpool/ROOT/ubuntu_64fs0l/var/mail                  152K  9.15G       96K  /mnt/var/mail
tmprpool/ROOT/ubuntu_64fs0l/var/snap                 1.12M  9.15G      904K  /mnt/var/snap
tmprpool/ROOT/ubuntu_64fs0l/var/spool                 360K  9.15G      112K  /mnt/var/spool
tmprpool/ROOT/ubuntu_64fs0l/var/www                   152K  9.15G       96K  /mnt/var/www
tmprpool/USERDATA                                    12.0M  9.15G       96K  /mnt
tmprpool/USERDATA/mafoelffen_7vzpaq                  11.4M  9.15G     3.82M  /mnt/home/mafoelffen
tmprpool/USERDATA/root_7vzpaq
                         492K  9.15G      160K  /mnt/root
root@ubuntu:~# zfs mount tmprpool/ROOT/ubuntu_64fs0l

root@ubuntu:~# zfs mount tmprpool/ROOT/ubuntu_64fs0l

root@ubuntu:~# zfs mount -a

root@ubuntu:~# mount --rbind /dev  /mnt/dev

root@ubuntu:~# mount --rbind /proc /mnt/proc

root@ubuntu:~# mount --rbind /sys  /mnt/sys

root@ubuntu:~# chroot /mnt /bin/bash --login

root@ubuntu:/# ls
bin   cdrom  etc   lib    lib64   media  opt   root  sbin  srv  tmp  var
boot  dev    home  lib32  libx32  mnt    proc  run   snap  sys  usr

root@ubuntu:/# ls /boot/efi
ls: cannot access '/boot/efi': No such file or directory

root@ubuntu:/# ls /boot

root@ubuntu:/# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# /boot/efi was on /dev/vda1 during installation
UUID=FF71-A6FE  /boot/efi       vfat    umask=0022,fmask=0022,dmask=0022      0       1
/boot/efi/grub    /boot/grub    none    defaults,bind    0    0
UUID=1d4f42f7-d8fe-4536-92f0-1dcf1422d394    none    swap    discard    0    0

root@ubuntu:/# mkdir /boot/efi

root@ubuntu:/# mkdir /boot/grub

root@ubuntu:/# mount -a

root@ubuntu:/# mount
tmprpool/ROOT/ubuntu_64fs0l on / type zfs (rw,relatime,xattr,posixacl)
tmprpool/USERDATA/mafoelffen_7vzpaq on /home/mafoelffen type zfs (rw,relatime,xattr,posixacl)
tmprpool/ROOT/ubuntu_64fs0l/srv on /srv type zfs (rw,relatime,xattr,posixacl)
tmprpool/ROOT/ubuntu_64fs0l/var/log on /var/log type zfs (rw,relatime,xattr,posixacl)
tmprpool/ROOT/ubuntu_64fs0l/var/games on /var/games type zfs (rw,relatime,xattr,posixacl)
tmprpool/ROOT/ubuntu_64fs0l/var/mail on /var/mail type zfs (rw,relatime,xattr,posixacl)
tmprpool/ROOT/ubuntu_64fs0l/var/snap on /var/snap type zfs (rw,relatime,xattr,posixacl)
tmprpool/USERDATA/root_7vzpaq on /root type zfs (rw,relatime,xattr,posixacl)
tmprpool/ROOT/ubuntu_64fs0l/var/lib on /var/lib type zfs (rw,relatime,xattr,posixacl)
tmprpool/ROOT/ubuntu_64fs0l/var/www on /var/www type zfs (rw,relatime,xattr,posixacl)
tmprpool/ROOT/ubuntu_64fs0l/var/spool on /var/spool type zfs (rw,relatime,xattr,posixacl)
tmprpool/ROOT/ubuntu_64fs0l/var/lib/apt on /var/lib/apt type zfs (rw,relatime,xattr,posixacl)
tmprpool/ROOT/ubuntu_64fs0l/var/lib/AccountsService on /var/lib/AccountsService type zfs (rw,relatime,xattr,posixacl)
tmprpool/ROOT/ubuntu_64fs0l/usr/local on /usr/local type zfs (rw,relatime,xattr,posixacl)
tmprpool/ROOT/ubuntu_64fs0l/var/lib/dpkg on /var/lib/dpkg type zfs (rw,relatime,xattr,posixacl)
tmprpool/ROOT/ubuntu_64fs0l/var/lib/NetworkManager on /var/lib/NetworkManager type zfs (rw,relatime,xattr,posixacl)
udev on /dev type devtmpfs (rw,nosuid,noexec,relatime,size=1953388k,nr_inodes=488347,mode=755,inode64)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev,inode64)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
mqueue on /dev/mqueue type mqueue (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=28,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=14759)
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755,inode64)
cgroup2 on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
none on /sys/fs/bpf type bpf (rw,nosuid,nodev,noexec,relatime,mode=700)
debugfs on /sys/kernel/debug type debugfs (rw,nosuid,nodev,noexec,relatime)
tracefs on /sys/kernel/tracing type tracefs (rw,nosuid,nodev,noexec,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,nosuid,nodev,noexec,relatime)
configfs on /sys/kernel/config type configfs (rw,nosuid,nodev,noexec,relatime)
/dev/vda1 on /boot/efi type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/vda1 on /boot/grub type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)

root@ubuntu:/# mount | grep /boot/grub
/dev/vda1 on /boot/grub type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)

root@ubuntu:/# grub-install --target=x86_64-efi --efi-directory=/boot/efi \
>     --bootloader-id=ubuntu --recheck --no-floppy
Installing for x86_64-efi platform.
Installation finished. No error reported.

root@ubuntu:/# exit
logout

# After exiting chroot, shutdown ZFS filesystems cleanly, unmount all ZFS pools, unmount all mounts and reboot
ubuntu@ubuntu:~$ sudo zfs umount tmprpool/ROOT/ubuntu_64fs0l

ubuntu@ubuntu:~$ sudo zpool export tmprpool

ubuntu@ubuntu:~$ sudo umount /mnt

ubuntu@ubuntu:~$ sudo reboot

```
The reason I included all those, is that it is dynamic and changes per the system, so you have to adjust for that...

---

### Post by MAFoElffen on 2022-06-01
I forgot to mention...

In Ubuntu 20.04 and newer, the login screen (DM) theme is within a greresource binary file. So to edit themes, you have to use the greresource utilty to extract, edit the css file(s), then recompile the changes for it to work... And the location of the css file for the Login Screen depends on which DM you use, for instance default is GDM, but if you use LightDM or SDDM, the path for that is different...

---

### Post by kumazenko on 2022-06-03
**MAFoElffen... my sincere thanks!** I* really appreciate the lucid outline, not to mention the detailed log to review.* So I carefully proceeded through the process and reached a viable chroot. Regarding repairs, what do you think of my logic?

Being that it seems the grub boot system is fine (I am presented with a  menu, and can choose options that lead into a boot, it's just that the  system fails hard when attempting to start some services. My intuition  is that this traces back to the errant apt remove (evolution*) which  like mentioned, went wild and removed lots of system services.

If there's curiosity, the symptoms of attempting to boot the failed O/S:
[FONT=courier new]"Bluetooth: hcio: Failed to send  firmware data, sending frame failed (-19), Failed to read MSFT supported  features (-110), command 0xfc1e tx timeout[/FONT]


Anyway, my thought at the moment is perhaps the snapshot restore  attempted didn't rollback enough, so I have effectively a partially  destroyed group of essential boot services.

There's a small part of me which wishes this to be over with, and so  thinks of proceeding with rolling back an earlier snap - but, I see this  as a great oportunity to learn more Linux troubleshooting chops : )

So, I have 3 ideas, in loose order of preference:

**A)** Perhaps there is a known good set of perimeters to  utilize some combination of apt update / repair / reinstall to replace  all missing deletions.*

**B) **3rd party utility to perform such a repair? I've Googled a bit, but not finding a trail..

**C)** Reinstall Ubuntu right over the existing install

**D)** Simply backup the user data & start fresh


*
After my first successful chroot, I did attempt an apt update &  apt-get update --fix-missing, and I did see some services coming back,  but the system hard locked up (reverted to the Lenovo x Ubuntu logo, but  hitting ESC revealed no activity, frozen).

Again, my appreciation for the sharing of this wisdom. Cheers!

---

### Post by grahammechanical on 2022-06-03
I am running Ubuntu 22.04 and Evolution is not installed by default and has not been installed by default in Ubuntu for many years. On the other hand there are packages/libraries that added functionality to Evolution and some of them are installed in Ubuntu because they are useful to other programs. An example of this is Evolution Data Server. This is how it is described:

> The Evolution Data Server package **provides a unified backend for programs that work with contacts, tasks, and calendar information**. It was originally developed for Evolution (hence the name), but is now used by other packages as well.

Remove that package and you might lose Gnome Calendar and Thunderbird might lose the ability to have an address book. One of the many good things about Linux is that programs are made up of packages and not one single compiled application. And because the code is Free and Open Source these dependent packages (dependencies) can be used by any other program that can make use of them.

When we install Ubuntu 22.04 we get the option to have a normal install or a minimal install that installs a web browser and basic utilities. Maybe a minimal install is the better option for your needs then you can install applications of your choice and you will not be concerned at the dependencies that are installed with those applications.

Regards

---

### Post by tea for one on 2022-06-04
Following the good advice from grahammechanical about a minimal install, there is also a solution to change the log-in background.

[https://www.omgubuntu.co.uk/2022/01/change-ubuntu-login-screen-background](https://www.omgubuntu.co.uk/2022/01/change-ubuntu-login-screen-background)
[https://github.com/PRATAP-KUMAR/ubuntu-gdm-set-background](https://github.com/PRATAP-KUMAR/ubuntu-gdm-set-background)
I do not have the knowledge to check if the code is untrustworthy, so I used it on an unimportant testing PC.
It was installed approx 2 months ago when 22.04 was in development and, after upgrading to the final release, no observable problems emerged.

---

### Post by MAFoElffen on 2022-06-05
Well yes and no on a few things...


Evolution, as a standalone default installed application has not been that for over 10 years now in Ubuntu. The functionality of that was replaced by Thunderbird... 

But that didn't mean that underlying hooks for Evolution went away. Evolution was from Gnome, and was replaced because it was not being maintained. Beause it IS from Gnome, pieces are still there IN Gnome... So removing it broke other things that were/are present in Gnome. if you do a default, Vanilla, install and do an apt list filtered on 'evolution', and you see those many underlying pieces still there...

My recommends on the easiest way: C or D. Run the 'system-info script from my sig line and snip out the section on User Installed packages to help you get back to where you are now with it. That and a good backup of your user data and config files.

My recommends on ZFS, if you are are doing 22.04... Between Release 20.04 and 22.04, as it relates to ZFS-On_Root... In 20.04, there was a push in Ubutnu on ZSys, to try to make ZFS integration easier for normal (skilled) users. It was a good idea. One of the things it did was to turn on auto ZFS --system snapshots, and added a "History' menu in the Grub2 boot menu, which gave users the ability to roll-back to an earlier ZFS snapshot.

ZSys is not installed by default in the initial release of 22.04, so that recovery feature is not there, unless you install it manually. ZSys did have an associated problem... It's default was to take 20 snapshots, then roll off the older snapshots... This setting was set in the compiled config (not to be reset by a user easily). That is too many. What happens is that with the default size of the bpool, it was filling the bpool space and would become unbootable, or no longer have space for updates in bpool (intramfs errors) until you zapped the older bpool snapshots... I have a script that does that for users in my Ama-Gi Project...

You can also do all that manually without ZSys...

I'm a contributor to Yann on the 'boot-info' and 'boot-repair' scripts, especially on adding interrogation to them for ZFS and LUKS boot problems and repairs. I'm teaching others how to access, mount, and chroot into those for diagnostics and repairs on those system.

---

### Post by kumazenko on 2022-06-06
100%. Yes I would agree (minimal install), it's just that in this case I was evaluating the full install to get a sense of what to keep / pare down.

---

### Post by kumazenko on 2022-06-06
[**[COLOR=#DD4814][B]MAFoElffen**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1044547"): Lol, yes I have hard won clarity now as to the error of my uninstall ways re: those packages. Fine with that as a small price to pay for this fun deep dive into Linux : )

Also **I definitely** am incorporating the two points you shared re: snapshots / boot menu.

Regarding possible path C:
*Any special tricks to that? I incorrectly presumed it would be as easy as booting the Ubuntu install media & confirming the ZFS partitions as where to reinstall to, however no dice - Ubuntu thus far will only offer an option to wipe everything and start fresh.*

Continued thanks everyone for the sharing of wisdom, & my apologies for the late replies between answers... fitting this R&D work into spare time.

_Cheers, and again my gratitude..._

---

### Post by MAFoElffen on 2022-06-06
Before you do ANYTHING... Get a good backup. MeaningL: mount the ZFS filesystem (Pools activated) so eveything can be read correctly...

Before making any changes, explore just a bit more to ensure that there are not snapshots that you might be able to rollback manually, that were previous to your issue:
```

zfs list -t snapshot
zfs list -o space

```

For an outside perspective/reference, read this: [https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2022.04%20Root%20on%20ZFS.html](https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2022.04%20Root%20on%20ZFS.html)

While reading it, take it with a grain of salt... Knowing that there are many errors caused by old information and some misconceptions... Since before 18.04, you didn't have to install debootstrap, nor gdisk. gdisk is already there as a default app, and debootstrap dos not add anything related to ZFS...And for option C... You would not instrall fresh, by destroying the partition tables and erasing everything.

Also note this quote:
> 
 **[Ubuntu Installer]("https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2022.04%20Root%20on%20ZFS.html#id2")[&#61633;]("https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2022.04%20Root%20on%20ZFS.html#ubuntu-installer")**

 The Ubuntu installer still has ZFS support, but [it was almost removed for 22.04]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1966773") and [it no longer installs zsys]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1968150").  At the moment, this HOWTO still uses zsys, but that will be probably be removed in the near future.
 


Important NOT to use those instructions. If you are going to try Option C. Those will overwrite everything and take over a complete disk. Just for refr3nce to see what kinds of things are involved and come into play. What it uses, and what to modify from, to something else. (In fact, for a fresh install, those instructions have some errors.)

The process of installing over an OS to recover it, is that you use the LiveCD, proceed with the install, and when it asks you if you want to Erase all and install...... Instead you choose Do Something Else... Where it takes you to the Partitioner... Then when it the Partitioner, you select the existing partitions, then unselct the format boxes on them... When the installer will then install over the existing files.

This becomes a lot more complex, when you add ZFS, and the ZFS Filesystem, form a LiveCD which, when it starts fresh, does not haev zfsutils-linux installed yet. So the precept is that you need to use "try" before starting the installer, to add then toolset, and thel;l the installer wehat to do, before you start the installer... Takes some work, and time, to make the install environment aware.

Option D is a lot easier. But instead of thinking of it as a lone, fresh install, think of it as a migration. Bedfore chaging anything on your system... Make sure you have backed up your data, a list of programs you have installed beyond the original installations, and the config files that you had changed... To do a fresh install, then restore what was changed, that you want back...

I take that "user Installed list" and create a Post Installation script, to reinstall the packages on that list, onto the fresh install. Then restore the config files and the user data.

---

