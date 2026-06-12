---
title: "Installer gets to 99% and fails at GRUB installation"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by panfist on 2008-07-21
In short, GRUB fails to install every time on my system. The installer gets to 99% and then says "grub failed to install. fatal error." Before I install I can uncheck "install grub" from an advanced dialog and the installation works fine but then I can never boot into it.

I have tried to install GRUB manually but no matter what I choose for the device, be it sda, sda1, sda2, sda3, or sda4, I get the following:

```
ubuntu@ubuntu:/var/log/installer$ sudo grub-install /dev/sda
Could not find device for /boot: Not found or not a block device.
```

I have also tried from within GRUB. No matter what I try to "find" in the GRUB shell, it can't be found. No matter what I set as root, the partition can't be mounted. No matter what device I try to "setup", the partition can't be mounted. Here's a sample of the frustration I have been running into:

```
grub> find /boot
find /boot

Error 15: File not found

grub> setup (hd0)
setup (hd0)

Error 17: Cannot mount selected partition
grub> setup (hd0,0)
setup (hd0,0)

Error 17: Cannot mount selected partition
grub> setup (hd0,3)
setup (hd0,3)

Error 17: Cannot mount selected partition
grub> setup (hd0,4)
setup (hd0,4)

Error 17: Cannot mount selected partition
grub> setup (hd0,1)
setup (hd0,1)

Error 17: Cannot mount selected partition
grub> find /boot
find /boot

Error 15: File not found
```

Here's the installer log:

```
ubuntu@ubuntu:/var/log/installer$ cat debug
Ubiquity 1.8.12
QSocketNotifier: Invalid socket 17 and type 'Read', disabling...
QSocketNotifier: Invalid socket 17 and type 'Exception', disabling...
QSocketNotifier: Invalid socket 17 and type 'Write', disabling...
QSocketNotifier: Invalid socket 17 and type 'Write', disabling...
QSocketNotifier: Invalid socket 17 and type 'Read', disabling...
QSocketNotifier: Invalid socket 17 and type 'Read', disabling...
QSocketNotifier: Invalid socket 17 and type 'Exception', disabling...
QSocketNotifier: Invalid socket 17 and type 'Exception', disabling...
QSocketNotifier: Invalid socket 17 and type 'Read', disabling...
QSocketNotifier: Invalid socket 17 and type 'Exception', disabling...
QSocketNotifier: Invalid socket 17 and type 'Write', disabling...
QSocketNotifier: Invalid socket 17 and type 'Read', disabling...
QSocketNotifier: Invalid socket 17 and type 'Exception', disabling...
Ubiquity 1.8.12
QSocketNotifier: Invalid socket 17 and type 'Read', disabling...
QSocketNotifier: Invalid socket 17 and type 'Exception', disabling...
QSocketNotifier: Invalid socket 17 and type 'Write', disabling...
QSocketNotifier: Invalid socket 17 and type 'Write', disabling...
QSocketNotifier: Invalid socket 17 and type 'Read', disabling...
QSocketNotifier: Invalid socket 17 and type 'Read', disabling...
QSocketNotifier: Invalid socket 17 and type 'Exception', disabling...
WARNING: unknown widget: partition_edit_dialog
QSocketNotifier: Invalid socket 17 and type 'Exception', disabling...
QSocketNotifier: Invalid socket 17 and type 'Read', disabling...
QSocketNotifier: Invalid socket 17 and type 'Exception', disabling...
QSocketNotifier: Invalid socket 17 and type 'Write', disabling...
QSocketNotifier: Invalid socket 17 and type 'Read', disabling...
QSocketNotifier: Invalid socket 17 and type 'Exception', disabling...
QSocketNotifier: Invalid socket 17 and type 'Write', disabling...
QSocketNotifier: Invalid socket 17 and type 'Read', disabling...
QSocketNotifier: Invalid socket 17 and type 'Exception', disabling...
Exception in KDE frontend (invoking crash handler):
Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 229, in <module>
    main()
  File "/usr/lib/ubiquity/bin/ubiquity", line 224, in main
    install(args[0])
  File "/usr/lib/ubiquity/bin/ubiquity", line 68, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/kde_ui.py", line 406, in run
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/kde_ui.py", line 708, in progress_loop
    (ret, realtb))
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 1913, in <module>
    install.run()
  File "/usr/share/ubiquity/install.py", line 419, in run
    self.configure_bootloader()
  File "/usr/share/ubiquity/install.py", line 1422, in configure_bootloader
    "GrubInstaller failed with code %d" % ret)
InstallStepError: GrubInstaller failed with code 1



Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 229, in <module>
    main()
  File "/usr/lib/ubiquity/bin/ubiquity", line 224, in main
    install(args[0])
  File "/usr/lib/ubiquity/bin/ubiquity", line 68, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/kde_ui.py", line 406, in run
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/kde_ui.py", line 708, in progress_loop
    (ret, realtb))
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 1913, in <module>
    install.run()
  File "/usr/share/ubiquity/install.py", line 419, in run
    self.configure_bootloader()
  File "/usr/share/ubiquity/install.py", line 1422, in configure_bootloader
    "GrubInstaller failed with code %d" % ret)
InstallStepError: GrubInstaller failed with code 1
```

mount -l and fdisk -l

```
ubuntu@ubuntu:~$ sudo mount -l
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sda4 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal) []
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4f96acbc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         510     4096543+   7  HPFS/NTFS
/dev/sda2             511        2422    15358140    7  HPFS/NTFS
/dev/sda3            2423       58889   453571177+   7  HPFS/NTFS
/dev/sda4           58890       60801    15358140    7  HPFS/NTFS
```

And here's some background:

I'm trying to install kubuntu 8.04 64-bit and I am having trouble installing GRUB. I would like to have triple boot set up with XP, Vista, and Ubuntu but I can't get Ubuntu to install successfully. I have tried from scratch twice now and I'm ready to give up.

I know I just revealed that I'm actually trying to install kubuntu but if I'm having a problem with GRUB doesn't that pertain to ubuntu in general?

I have the hard disk partitioned into 4 primary partitions, 3x NTFS and 1x Ext3. I installed XP on sda1, the Vista on sda2, I have data as an NTFS partition on sda3 and now I'm trying to install on sda4.

99% of the how-tos I have found don't work for me because they are assuming that you already have GRUB installed and you just need to fix it. I need to install it in the first place. I found a couple of how-tos involving chrooting into the almost-done installation and installing GRUB from there, but I think I followed the instructions correctly and I still had the same problems in GRUB, i.e. "find" didn't work and no partitions could be mounted.

Interestingly I found that if I ran "fdisk -l" it tells me I have 4x NTFS partitions when everything else indicates that I do indeed have 3x NTFS and 1x Ext3. I don't know if this is part of the problem.

---

### Post by Sef on 2008-07-21
> Interestingly I found that if I ran "fdisk -l" it tells me I have 4x NTFS partitions when everything else indicates that I do indeed have 3x NTFS and 1x Ext3. I don't know if this is part of the problem.


Could you paste a copy of fdisk -l in a new post here.  If you do have 4 NTFS, then that would likely be the problem.

---

### Post by TenPlus1 on 2008-07-21
YOu could try installing Ubuntu through the Wubi.exe installed on the actual CD...  This as far as I know installs Ubuntu on your Windows partition and adds a selection to the boot menu...  Saves the hassle of making partitions if XP/Vista is messing with installation...

---

### Post by panfist on 2008-07-21
> **TenPlus1 said:**
> YOu could try installing Ubuntu through the Wubi.exe installed on the actual CD...  This as far as I know installs Ubuntu on your Windows partition and adds a selection to the boot menu...  Saves the hassle of making partitions if XP/Vista is messing with installation...

I suppose this is an option, but if possible I would like ubuntu on its own ext3 partition.

also I have edited the first post to include the output of "fdisk -l" and "mount -l"

---

### Post by toobaz on 2008-11-20
I had the same identical problem, but with more partitions:

I had sda1, sda2, sda3... sda10, and was trying to install Ubuntu on newly created sda11, but I always would get this error. Then, I removed sda10, a previous Intrepid installation, and tried to install in newly created sda10... still the same error. Finally, I removed sda9 (swap) and tried to install in newly created sda9... and all went fine.

I can't find a moral to this story... I thought "grub is so stupid, it can't install if a partition is in the form sda** instead sda**", but
- you reported the same problem, without having 10 partitions
- actually, when I made an installation of Kubuntu, I made it on - if I remember correctly - sda10

Pietro

---

### Post by Coreigh on 2008-11-20
So I may be over simplifying this but can you boot the LiveCD, open a terminal and change the partition type *before* starting the install?

sudo fdisk /dev/sda

t - change partition type
4 - partition number
83 - ext3 partition
w - write changes and exit

then fdisk -l to verify it reports an ext3 partition
then start installation.

:-k ?

---

### Post by user481516 on 2008-11-20
Why is there not a clear way to just put in the liveCD and install GRUB on any partition or hard drive you want?  It should be easy to do this.  I shake my finger at the ubuntu community for not resolving this issue yet.

---

### Post by caljohnsmith on 2008-11-20
How about first running Ubuntu's Partition Editor:
```
gksudo gparted
```
And use that to format one of your NTFS partitions into ext3 to use with Kubuntu. I don't see how you could have installed Kubuntu if you have all NTFS partitions, unless you were doing a Wubi install inside Windows. I can help you install Grub after your installation is successful, if you tell the installer not to install Grub. But first post the "sudo fdisk -l" after the installation is successful, and we can work from there if you want.

---

