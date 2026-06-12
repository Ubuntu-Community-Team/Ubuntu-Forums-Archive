---
title: "Boot Repair for a VM (XCP-ng to VMware Conversion)"
date: 2022-11-18
forum: Installation &amp; Upgrades
---

### Post by inayamat on 2022-11-18
Hello,

So I am working on migrating an Ubuntu 18 server from XCP-ng to VMware.  The VM Converter ran about 98% then crashed, and the Disks were cloned to vCenter.  The only problem is that the Server does not boot.

I ran boot-repair from a Live Ubuntu Desktop CD and here is the summary.

The VM is on BIOS mode, but I can change to EFI if necessary.

What should be my next steps?

Thank you,
Tadashi


[https://pastebin.ubuntu.com/p/VZd4hPBXBd/](https://pastebin.ubuntu.com/p/VZd4hPBXBd/)



```
boot-repair-4ppa200                                              [20221119_0024]


============================== Boot Info Summary ===============================


 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       BIOS Boot partition
    Boot sector type:  -
    Boot sector info: 


sdb1: __________________________________________________________________________


    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 




================================ 1 OS detected =================================


OS#1:   Ubuntu 18.04.6 LTS on mapper/ubuntu--vg-ubuntu--lv


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: SVGA II Adapter from VMware
Live-session OS is Ubuntu 64-bit (Ubuntu 18.04.6 LTS, bionic, x86_64)


===================================== UEFI =====================================


BIOS/UEFI firmware: 6.00 from Phoenix Technologies LTD
This live-session is in Legacy/BIOS/CSM mode (not in EFI mode).






============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sda    : is-GPT,    hasBIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


mapper/ubuntu--vg-ubuntu--lv    : is-os,    64, apt-get,    grub1 ,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far


Partitions info (2/3): _________________________________________________________


mapper/ubuntu--vg-ubuntu--lv    : isnotESP,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot


Partitions info (3/3): _________________________________________________________


mapper/ubuntu--vg-ubuntu--lv    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    no--grub.d,    sda


fdisk -l (filtered): ___________________________________________________________


Disk sdb: 24.5 GiB, 26311917568 bytes, 51390464 sectors
Disk identifier: FA4D5D71-19C7-4E2D-717A-1B42859A6F1E
      Start      End  Sectors  Size Type
sdb1    128 51388543 51388416 24.5G Linux LVM
Disk sda: 1 GiB, 1074790400 bytes, 2099200 sectors
Disk identifier: C60BAA05-9918-49E3-81A3-099DBC313B44
      Start     End Sectors  Size Type
sda1   2048 2097151 2095104 1023M BIOS boot
Disk mapper/ubuntu--vg-ubuntu--lv: 24.5 GiB, 26306674688 bytes, 51380224 sectors


parted -lm (filtered): _________________________________________________________


sda:1075MB:scsi:512:512:gpt:VMware Virtual disk:;
1:1049kB:1074MB:1073MB:ext4::bios_grub;
sdb:26.3GB:scsi:512:512:gpt:VMware Virtual disk:;
1:65.5kB:26.3GB:26.3GB::Linux Lvm:lvm;
mapper/ubuntu--vg-ubuntu--lv:26.3GB:dm:512:512:loop:Linux device-mapper (linear):;
1:0.00B:26.3GB:26.3GB:ext4::;


blkid (filtered): ______________________________________________________________


NAME                      FSTYPE      UUID                                   PARTUUID                             LABEL                    PARTLABEL
sda                                                                                                                                        
&#9492;&#9472;sda1                    ext4        235a6a82-aca0-44ee-bea1-49c375928a7b   78f9fb10-ea38-4f73-9f0f-18958e196e90                          
sdb                                                                                                                                        
&#9492;&#9472;sdb1                    LVM2_member XGY0TS-hyEU-h8Fl-d3jo-Pgdl-uGvl-GqsOD0 92c24a3b-7467-431c-643b-93fbc7defcf6                          Linux Lvm
  &#9492;&#9472;ubuntu--vg-ubuntu--lv ext4        19c9c770-ee37-42bf-8792-0930fb5cd64c                                                                 


Mount points (filtered): _______________________________________________________


                                   Avail Use% Mounted on
/dev/mapper/ubuntu--vg-ubuntu--lv  16.9G  25% /mnt/boot-sav/mapper/ubuntu--vg-ubuntu--lv


Mount options (filtered): ______________________________________________________


/dev/mapper/ubuntu--vg-ubuntu--lv ext4            rw,relatime


============================== ls -R /dev/mapper/ ==============================


/dev/mapper:
control
ubuntu--vg-ubuntu--lv


================================= User choice ==================================


Is there RAID on this computer? no




==================== blkid (filtered) before lvm activation ====================


/dev/mapper/ubuntu--vg-ubuntu--lv: UUID="19c9c770-ee37-42bf-8792-0930fb5cd64c" TYPE="ext4"
/dev/sda1: UUID="235a6a82-aca0-44ee-bea1-49c375928a7b" TYPE="ext4" PARTUUID="78f9fb10-ea38-4f73-9f0f-18958e196e90"
/dev/sr0: UUID="2021-09-15-20-41-59-00" LABEL="Ubuntu 18.04.6 LTS amd64" TYPE="iso9660" PTUUID="4c050c47" PTTYPE="dos"
/dev/sdb1: UUID="XGY0TS-hyEU-h8Fl-d3jo-Pgdl-uGvl-GqsOD0" TYPE="LVM2_member" PARTLABEL="Linux Lvm" PARTUUID="92c24a3b-7467-431c-643b-93fbc7defcf6"




================================ LVM activation ================================


modprobe dm-mod  
vgscan --mknodes
  Reading volume groups from cache.
  Found volume group "ubuntu-vg" using metadata type lvm2
vgchange -ay
  1 logical volume(s) in volume group "ubuntu-vg" now active
lvscan
  ACTIVE            '/dev/ubuntu-vg/ubuntu-lv' [24.50 GiB] inherit
blkid -g






Suggested repair: ______________________________________________________________


The default repair of the Boot-Repair utility would purge (in order to fix packages) and reinstall the grub2 of
mapper/ubuntu--vg-ubuntu--lv into the MBR of sda.
Grub-efi would not be selected by default because no ESP detected.
Additional repair would be performed: unhide-bootmenu-10s
```

---

### Post by oldfred on 2022-11-18
Please use Code Tags for any text or terminal output to maintain formatting. 
How to use Code tags, # in Forum's advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

But with Boot-Repair the link is all that is really required.

because you have gpt and bios_grub, you just need grub installed to gpt's protective MBR. It will automatically use the bios_grub for additional grub code (core.img).

Did you run the recommended repair. Often easiest.
Other option is full chroot & reinstall of grub from that.

---

### Post by inayamat on 2022-11-18
Hello.  Thanks for the response.

So I did try out the recommended repair.  But when I tried the first script, it looked like there some issue with not finding /boot/grub but it looks like /boot/grub already exists.  

Here was the recommendation:

```

[FONT=Arial]sudo chroot "/mnt/boot-sav/mapper/ubuntu--[/FONT][FONT=Arial]vg-ubuntu--lv" dpkg --configure -a[/FONT]
[FONT=Arial]sudo chroot "/mnt/boot-sav/mapper/ubuntu--[/FONT][FONT=Arial]vg-ubuntu--lv" apt-get install -fy[/FONT]
[FONT=Arial]sudo chroot "/mnt/boot-sav/mapper/ubuntu--[/FONT][FONT=Arial]vg-ubuntu--lv" apt-get install -y lvm2[/FONT]
[FONT=Arial]sudo chroot "/mnt/boot-sav/mapper/ubuntu--[/FONT][FONT=Arial]vg-ubuntu--lv" apt-get install -y grub-pc[/FONT]

```


Here is the output from the first script:

[https://pastebin.ubuntu.com/p/ScmJmP7jrg/](https://pastebin.ubuntu.com/p/ScmJmP7jrg/)

Also, what does full chroot mean in this context?  

Thank you in advance,
Tadashi

---

### Post by oldfred on 2022-11-19
Have not used Boot-Repair to reinstall grub. But it walks you thru a minimal mount/chroot.

If not UEFI, you would not need the mount of the ESP.
chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

---

### Post by inayamat on 2022-11-19
Hello.  Thank you for the response, appreciate your help.

I am trying to go through the steps laid out by boot-repair.

First command it wanted me to run was:

[FONT=Arial]sudo chroot "/mnt/boot-sav/mapper/ubuntu--[/FONT][FONT=Arial]vg-ubuntu--lv" dpkg --configure -a[/FONT]


```


[FONT=Arial]ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/mapper/ubuntu--[/FONT][FONT=Arial]vg-ubuntu--lv" dpkg --configure -a[/FONT]
[FONT=Arial]Setting up linux-image-4.15.0-197-generic (4.15.0-197.208) ...[/FONT]
[FONT=Arial]Processing triggers for linux-image-4.15.0-197-generic (4.15.0-197.208) ...[/FONT]
[FONT=Arial]/etc/kernel/postinst.d/[/FONT][FONT=Arial]initramfs-tools:[/FONT]
[FONT=Arial]update-initramfs: Generating /boot/initrd.img-4.15.0-197-[/FONT][FONT=Arial]generic[/FONT]
[FONT=Arial]Warning: couldn't identify filesystem type for fsck hook, ignoring.[/FONT]
[FONT=Arial]/etc/kernel/postinst.d/x-grub-[/FONT][FONT=Arial]legacy-ec2:[/FONT]
[FONT=Arial]Searching for GRUB installation directory ...[/FONT]
[FONT=Arial]No GRUB directory found.[/FONT]
[FONT=Arial] To create a template run 'mkdir /boot/grub' first.[/FONT]
[FONT=Arial] To install grub, install it manually or try the 'grub-install' command.[/FONT]
[FONT=Arial] ### Warning, grub-install is used to change your MBR. ###[/FONT]

[FONT=Arial]run-parts: /etc/kernel/postinst.d/x-grub-[/FONT][FONT=Arial]legacy-ec2 exited with return code 1[/FONT]
[FONT=Arial]dpkg: error processing package linux-image-4.15.0-197-generic (--configure):[/FONT]
[FONT=Arial] installed linux-image-4.15.0-197-generic package post-installation script subprocess returned error exit status 1[/FONT]
[FONT=Arial]Errors were encountered while processing:[/FONT]
[FONT=Arial] linux-image-4.15.0-197-[/FONT][FONT=Arial]generic[/FONT]


```


but /boot/grub already exists

```

[FONT=Arial]ubuntu@ubuntu:~$ sudo mkdir /boot/grub[/FONT]
[FONT=Arial]mkdir: cannot create directory ‘/boot/grub’: File exists

```

Is there something else wrong that is preventing me from running the first command?

Thank you,
Tadashi[/FONT]

---

### Post by oldfred on 2022-11-20
What does this show?
#To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short 

[https://askubuntu.com/questions/458572/how-do-i-prevent-one-of-my-partitions-messing-with-lubuntu-grub-entries/458582#458582](https://askubuntu.com/questions/458572/how-do-i-prevent-one-of-my-partitions-messing-with-lubuntu-grub-entries/458582#458582)

Recently saw another user with the output from debconf-show install device was not correct.

---

### Post by inayamat on 2022-11-20
Hello.  Here are the outputs:

```


[FONT=Arial]ubuntu@ubuntu:~$ sudo debconf-show grub-pc[/FONT]
[FONT=Arial]  grub-pc/partition_description:[/FONT]
[FONT=Arial]  grub-pc/postrm_purge_boot_[/FONT][FONT=Arial]grub: false[/FONT]
[FONT=Arial]  grub-pc/hidden_timeout: true[/FONT]
[FONT=Arial]  grub2/unsigned_kernels_title:[/FONT]
[FONT=Arial]  grub-pc/disk_description:[/FONT]
[FONT=Arial]  grub2/update_nvram: true[/FONT]
[FONT=Arial]  grub-pc/install_devices_[/FONT][FONT=Arial]failed_upgrade: true[/FONT]
[FONT=Arial]  grub2/device_map_regenerated:[/FONT]
[FONT=Arial]  grub-pc/install_devices:[/FONT]
[FONT=Arial]  grub2/kfreebsd_cmdline_[/FONT][FONT=Arial]default: quiet splash[/FONT]
[FONT=Arial]  grub2/linux_cmdline:[/FONT]
[FONT=Arial]  grub2/unsigned_kernels:[/FONT]
[FONT=Arial]  grub-pc/install_devices_[/FONT][FONT=Arial]failed: false[/FONT]
[FONT=Arial]  grub-pc/install_devices_disks_[/FONT][FONT=Arial]changed:[/FONT]
[FONT=Arial]  grub-pc/chainload_from_menu.[/FONT][FONT=Arial]lst: true[/FONT]
[FONT=Arial]  grub-pc/mixed_legacy_and_[/FONT][FONT=Arial]grub2: true[/FONT]
[FONT=Arial]  grub2/no_efi_extra_removable: false[/FONT]
[FONT=Arial]  grub-pc/install_devices_empty: false[/FONT]
[FONT=Arial]  grub-pc/kopt_extracted: false[/FONT]
[FONT=Arial]  grub-pc/timeout: 0[/FONT]
[FONT=Arial]  grub2/linux_cmdline_default: quiet splash[/FONT]
[FONT=Arial]  grub2/kfreebsd_cmdline:

[/FONT]
```

```

[FONT=Arial]ubuntu@ubuntu:~$ sudo lshw -C Disk -short[/FONT]
[FONT=Arial]H/W path           Device      Class      Description[/FONT]
[FONT=Arial]==============================[/FONT][FONT=Arial]=======================[/FONT]
[FONT=Arial]/0/100/10/0.0.0    /dev/sda    disk       1074MB Virtual disk[/FONT]
[FONT=Arial]/0/100/10/0.1.0    /dev/sdb    disk       26GB Virtual disk[/FONT]
[FONT=Arial]/0/46/0.0.0        /dev/cdrom  disk       VMware SATA CD00[/FONT]
[FONT=Arial]/0/46/0.0.0/0      /dev/cdrom  disk  [/FONT]

```

---

### Post by oldfred on 2022-11-20
It is showing a blank for the install devices line.
Do not know if that is then correctly filled in with Virtual disks & LVM volumes.

But then it is not a conflict and reinstall of grub should work.
I do not know LVM, but know that chroot must mount /boot (if separate partition) as well as / volume. Boot-Repair normally finds & mounts those.
The link to chroot shows mounting all the partitions.

Reviewed your errors again and did not notice before that it mentions grub legacy.
You should not be installing grub which now is grub legacy, but grub-pc which is for CSM/BIOS/legacy boot. 
There are other versions of grub2 for UEFI, and other hardware systems.

On my system when I do sudo grub-install, it knows I have UEFI (from fstab?) and reinstalls grub-efi-amd64.
I thought that the debconf might show something. 
But you should not have old grub legacy installed which may be confusing things.

I might purge all versions of grub and then reinstall. From inside the chroot, either Boot-Repairs or a full chroot.

I have seen this for LVM install, yours should be [FONT=Arial]ubuntu--[/FONT][FONT=Arial]vg-ubuntu--lv[/FONT] :
Also some installs do not have separate /boot partition as now grub can read LVM. 
sudo apt-get install lvm2
sudo vgchange -ay /dev/mapper/ubuntu--vg-root
sudo mount /dev/mapper/ubuntu--vg-root /mnt
sudo mount /dev/sda1 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sda

Full set of commands to purge & reinstall, example is sda, you need to use your volume.
# purge old and reinstall new to sda (BIOS version)
Make sure repositories are updated
sudo apt update
sudo apt upgrade
sudo apt purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt install grub-pc grub-common
sudo grub-install --recheck /dev/sda
sudo update-grub
sudo update-initramfs -u -k

---

### Post by inayamat on 2022-11-20
Hello.  Those are good leads, thank you very much.  

It will come back in a few days, but I will try them out and see how it goes.

Best,
Tadashi

---

### Post by inayamat on 2022-11-23
Hello.  So I got to running:

[COLOR=#000000]sudo apt purge grub grub-pc grub-common

but I get this error:

```

[/COLOR][FONT=Arial]ubuntu@ubuntu:/boot/grub$ sudo apt purge grub grub-pc grub-common[/FONT]
[FONT=Arial]Reading package lists... Done[/FONT]
[FONT=Arial]Building dependency tree      [/FONT]
[FONT=Arial]Reading state information... Done[/FONT]
[FONT=Arial]Package 'grub' is not installed, so not removed[/FONT]
[FONT=Arial]You might want to run 'apt --fix-broken install' to correct these.[/FONT]
[FONT=Arial]The following packages have unmet dependencies:[/FONT]
[FONT=Arial] grub-gfxpayload-lists : Depends: grub-pc (>= 1.99~20101210-1ubuntu2) but it is not going to be installed[/FONT]
[FONT=Arial] grub-pc-bin : Depends: grub-common (= 2.02-2ubuntu8.23) but it is not going to be installed[/FONT]
[FONT=Arial] grub2-common : Depends: grub-common (= 2.02-2ubuntu8.23) but it is not going to be installed[/FONT]
[FONT=Arial] libc6-dbg : Depends: libc6 (= 2.27-3ubuntu1.6) but 2.27-3ubuntu1.4 is to be installed[/FONT]
[FONT=Arial] os-prober : Depends: grub-common but it is not going to be installed[/FONT]
[FONT=Arial] ubiquity : Depends: grub-common but it is not going to be installed[/FONT]
[FONT=Arial]            Recommends: grub-pc but it is not going to be installed or[/FONT]
[FONT=Arial]                        grub but it is not installable or[/FONT]
[FONT=Arial]                        grub-efi-amd64 but it is not going to be installed[/FONT]
[FONT=Arial]E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).[/FONT][COLOR=#888888][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000]
```

And when I run 'sudo apt --fix-broken install' I get:

```

[/COLOR][FONT=Arial]ubuntu@ubuntu:/boot/grub$ sudo apt --fix-broken install[/FONT]
[FONT=Arial]Reading package lists... Done[/FONT]
[FONT=Arial]Building dependency tree      [/FONT]
[FONT=Arial]Reading state information... Done[/FONT]
[FONT=Arial]Correcting dependencies... Done[/FONT]
[FONT=Arial]The following additional packages will be installed:[/FONT]
[FONT=Arial]  libc6[/FONT]
[FONT=Arial]Suggested packages:[/FONT]
[FONT=Arial]  glibc-doc[/FONT]
[FONT=Arial]The following packages will be upgraded:[/FONT]
[FONT=Arial]  libc6[/FONT]
[FONT=Arial]1 upgraded, 0 newly installed, 0 to remove and 297 not upgraded.[/FONT]
[FONT=Arial]1 not fully installed or removed.[/FONT]
[FONT=Arial]Need to get 0 B/2,831 kB of archives.[/FONT]
[FONT=Arial]After this operation, 1,024 B of additional disk space will be used.[/FONT]
[FONT=Arial]Do you want to continue? [Y/n] Y[/FONT]
[FONT=Arial]debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable[/FONT]
[FONT=Arial](Reading database ... 146038 files and directories currently installed.)[/FONT]
[FONT=Arial]Preparing to unpack .../libc6_2.27-3ubuntu1.6_[/FONT][FONT=Arial]amd64.deb ...[/FONT]
[FONT=Arial]debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable[/FONT]
[FONT=Arial]dpkg: error processing archive /var/cache/apt/archives/libc6_[/FONT][FONT=Arial]2.27-3ubuntu1.6_amd64.deb (--unpack):[/FONT]
[FONT=Arial] new libc6:amd64 package pre-installation script subprocess returned error exit status 1[/FONT]
[FONT=Arial]Errors were encountered while processing:[/FONT]
[FONT=Arial] /var/cache/apt/archives/[/FONT][FONT=Arial]libc6_2.27-3ubuntu1.6_amd64.[/FONT][FONT=Arial]deb[/FONT]
[FONT=Arial]E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT][COLOR=#000000]

```

```



```[/COLOR]

---

### Post by inayamat on 2022-11-23
Hello.  

I got to running '[FONT=Arial]sudo apt purge grub grub-pc grub-common[/FONT]', then I got these errors:

```

[FONT=Arial]ubuntu@ubuntu:/boot/grub$ sudo apt purge grub grub-pc grub-common[/FONT]
[FONT=Arial]Reading package lists... Done[/FONT]
[FONT=Arial]Building dependency tree      [/FONT]
[FONT=Arial]Reading state information... Done[/FONT]
[FONT=Arial]Package 'grub' is not installed, so not removed[/FONT]
[FONT=Arial]You might want to run 'apt --fix-broken install' to correct these.[/FONT]
[FONT=Arial]The following packages have unmet dependencies:[/FONT]
[FONT=Arial] grub-gfxpayload-lists : Depends: grub-pc (>= 1.99~20101210-1ubuntu2) but it is not going to be installed[/FONT]
[FONT=Arial] grub-pc-bin : Depends: grub-common (= 2.02-2ubuntu8.23) but it is not going to be installed[/FONT]
[FONT=Arial] grub2-common : Depends: grub-common (= 2.02-2ubuntu8.23) but it is not going to be installed[/FONT]
[FONT=Arial] libc6-dbg : Depends: libc6 (= 2.27-3ubuntu1.6) but 2.27-3ubuntu1.4 is to be installed[/FONT]
[FONT=Arial] os-prober : Depends: grub-common but it is not going to be installed[/FONT]
[FONT=Arial] ubiquity : Depends: grub-common but it is not going to be installed[/FONT]
[FONT=Arial]            Recommends: grub-pc but it is not going to be installed or[/FONT]
[FONT=Arial]                        grub but it is not installable or[/FONT]
[FONT=Arial]                        grub-efi-amd64 but it is not going to be installed[/FONT]
[FONT=Arial]E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution)[/FONT]

```

When I ran '[FONT=Arial]sudo apt --fix-broken install[/FONT]', I got:

```

[FONT=Arial]ubuntu@ubuntu:/boot/grub$ sudo apt --fix-broken install[/FONT]
[FONT=Arial]Reading package lists... Done[/FONT]
[FONT=Arial]Building dependency tree      [/FONT]
[FONT=Arial]Reading state information... Done[/FONT]
[FONT=Arial]Correcting dependencies... Done[/FONT]
[FONT=Arial]The following additional packages will be installed:[/FONT]
[FONT=Arial]  libc6[/FONT]
[FONT=Arial]Suggested packages:[/FONT]
[FONT=Arial]  glibc-doc[/FONT]
[FONT=Arial]The following packages will be upgraded:[/FONT]
[FONT=Arial]  libc6[/FONT]
[FONT=Arial]1 upgraded, 0 newly installed, 0 to remove and 297 not upgraded.[/FONT]
[FONT=Arial]1 not fully installed or removed.[/FONT]
[FONT=Arial]Need to get 0 B/2,831 kB of archives.[/FONT]
[FONT=Arial]After this operation, 1,024 B of additional disk space will be used.[/FONT]
[FONT=Arial]Do you want to continue? [Y/n] Y[/FONT]
[FONT=Arial]debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable[/FONT]
[FONT=Arial](Reading database ... 146038 files and directories currently installed.)[/FONT]
[FONT=Arial]Preparing to unpack .../libc6_2.27-3ubuntu1.6_[/FONT][FONT=Arial]amd64.deb ...[/FONT]
[FONT=Arial]debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable[/FONT]
[FONT=Arial]dpkg: error processing archive /var/cache/apt/archives/libc6_[/FONT][FONT=Arial]2.27-3ubuntu1.6_amd64.deb (--unpack):[/FONT]
[FONT=Arial] new libc6:amd64 package pre-installation script subprocess returned error exit status 1[/FONT]
[FONT=Arial]Errors were encountered while processing:[/FONT]
[FONT=Arial] /var/cache/apt/archives/[/FONT][FONT=Arial]libc6_2.27-3ubuntu1.6_amd64.[/FONT][FONT=Arial]deb[/FONT]
[FONT=Arial]E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT]

```

Thank you,
Tadashi

---

### Post by oldfred on 2022-11-23
Locked by another process often is from having another update process running or you shutdown and left the file that says it is running.
I often do that if I open synaptic to see something, but then try to do an install from the terminal.

If you have uninstalled all of grub, you have to reinstall grub-pc or you will not be able to boot.
I expect a reboot may clear error if you do not have two update processes running.
Otherwise we have to try to find the status file, probably hidden that is the problem.

---

### Post by inayamat on 2022-11-23
Hello.

So I got an error: 

```

[FONT=Arial]ubuntu@ubuntu:~$ sudo grub-install --recheck /dev/sda[/FONT]
[FONT=Arial]Installing for i386-pc platform.[/FONT]
[FONT=Arial]grub-install: error: failed to get canonical path of `/cow'.[/FONT]

```

Here are my last few commands:

```

[FONT=Arial]ubuntu@ubuntu:~$ mv /boot/grub /boot/grub_backup[/FONT]
[FONT=Arial]mv: cannot stat '/boot/grub': No such file or directory[/FONT]
[FONT=Arial]ubuntu@ubuntu:~$ sudo mv /boot/grub /boot/grub_backup[/FONT]
[FONT=Arial]mv: cannot stat '/boot/grub': No such file or directory[/FONT]
[FONT=Arial]ubuntu@ubuntu:~$ sudo mkdir /boot/grub[/FONT]
[FONT=Arial]ubuntu@ubuntu:~$ sudo apt install grub-pc grub-common[/FONT]
[FONT=Arial]Reading package lists... Done[/FONT]
[FONT=Arial]Building dependency tree      [/FONT]
[FONT=Arial]Reading state information... Done[/FONT]
[FONT=Arial]The following additional packages will be installed:[/FONT]
[FONT=Arial]  grub-gfxpayload-lists grub-pc-bin grub2-common os-prober[/FONT]
[FONT=Arial]Suggested packages:[/FONT]
[FONT=Arial]  multiboot-doc grub-emu xorriso desktop-base[/FONT]
[FONT=Arial]The following NEW packages will be installed:[/FONT]
[FONT=Arial]  grub-common grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common[/FONT]
[FONT=Arial]  os-prober[/FONT]
[FONT=Arial]0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.[/FONT]
[FONT=Arial]Need to get 3,368 kB of archives.[/FONT]
[FONT=Arial]After this operation, 17.3 MB of additional disk space will be used.[/FONT]
[FONT=Arial]Do you want to continue? [Y/n] Y[/FONT]
[FONT=Arial]Get:1 [/FONT][http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)[FONT=Arial] bionic-security/main amd64 grub-common amd64 2.02-2ubuntu8.23 [1,772 kB][/FONT]
[FONT=Arial]Get:2 [/FONT][http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)[FONT=Arial] bionic/main amd64 grub-gfxpayload-lists amd64 0.7 [3,658 B][/FONT]
[FONT=Arial]Get:3 [/FONT][http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)[FONT=Arial] bionic/main amd64 os-prober amd64 1.74ubuntu1 [19.8 kB][/FONT]
[FONT=Arial]Get:4 [/FONT][http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)[FONT=Arial] bionic-security/main amd64 grub2-common amd64 2.02-2ubuntu8.23 [534 kB][/FONT]
[FONT=Arial]Get:5 [/FONT][http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)[FONT=Arial] bionic-security/main amd64 grub-pc-bin amd64 2.02-2ubuntu8.23 [901 kB][/FONT]
[FONT=Arial]Get:6 [/FONT][http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)[FONT=Arial] bionic-security/main amd64 grub-pc amd64 2.02-2ubuntu8.23 [138 kB][/FONT]
[FONT=Arial]Fetched 3,368 kB in 2s (2,020 kB/s)[/FONT]
[FONT=Arial]Preconfiguring packages ...[/FONT]
[FONT=Arial]Selecting previously unselected package grub-common.[/FONT]
[FONT=Arial](Reading database ... 181074 files and directories currently installed.)[/FONT]
[FONT=Arial]Preparing to unpack .../0-grub-common_2.02-[/FONT][FONT=Arial]2ubuntu8.23_amd64.deb ...[/FONT]
[FONT=Arial]Unpacking grub-common (2.02-2ubuntu8.23) ...[/FONT]
[FONT=Arial]Selecting previously unselected package grub2-common.[/FONT]
[FONT=Arial]Preparing to unpack .../1-grub2-common_2.02-[/FONT][FONT=Arial]2ubuntu8.23_amd64.deb ...[/FONT]
[FONT=Arial]Unpacking grub2-common (2.02-2ubuntu8.23) ...[/FONT]
[FONT=Arial]Selecting previously unselected package grub-pc-bin.[/FONT]
[FONT=Arial]Preparing to unpack .../2-grub-pc-bin_2.02-[/FONT][FONT=Arial]2ubuntu8.23_amd64.deb ...[/FONT]
[FONT=Arial]Unpacking grub-pc-bin (2.02-2ubuntu8.23) ...[/FONT]
[FONT=Arial]Selecting previously unselected package grub-pc.[/FONT]
[FONT=Arial]Preparing to unpack .../3-grub-pc_2.02-2ubuntu8.[/FONT][FONT=Arial]23_amd64.deb ...[/FONT]
[FONT=Arial]Unpacking grub-pc (2.02-2ubuntu8.23) ...[/FONT]
[FONT=Arial]Selecting previously unselected package grub-gfxpayload-lists.[/FONT]
[FONT=Arial]Preparing to unpack .../4-grub-gfxpayload-lists_0.[/FONT][FONT=Arial]7_amd64.deb ...[/FONT]
[FONT=Arial]Unpacking grub-gfxpayload-lists (0.7) ...[/FONT]
[FONT=Arial]Selecting previously unselected package os-prober.[/FONT]
[FONT=Arial]Preparing to unpack .../5-os-prober_1.74ubuntu1_[/FONT][FONT=Arial]amd64.deb ...[/FONT]
[FONT=Arial]Unpacking os-prober (1.74ubuntu1) ...[/FONT]
[FONT=Arial]Setting up grub-common (2.02-2ubuntu8.23) ...[/FONT]
[FONT=Arial]update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults[/FONT]
[FONT=Arial]Setting up grub-pc-bin (2.02-2ubuntu8.23) ...[/FONT]
[FONT=Arial]Setting up grub2-common (2.02-2ubuntu8.23) ...[/FONT]
[FONT=Arial]Setting up os-prober (1.74ubuntu1) ...[/FONT]
[FONT=Arial]Setting up grub-pc (2.02-2ubuntu8.23) ...[/FONT]

[FONT=Arial]Creating config file /etc/default/grub with new version[/FONT]
[FONT=Arial]Setting up grub-gfxpayload-lists (0.7) ...[/FONT]
[FONT=Arial]Processing triggers for systemd (237-3ubuntu10.56) ...[/FONT]
[FONT=Arial]Processing triggers for man-db (2.8.3-2ubuntu0.1) ...[/FONT]
[FONT=Arial]Processing triggers for ureadahead (0.100.0-21) ...[/FONT]
[FONT=Arial]Processing triggers for install-info (6.5.0.dfsg.1-2) ...[/FONT]
[FONT=Arial]ubuntu@ubuntu:~$ sudo grub-install --recheck /dev/sda[/FONT]
[FONT=Arial]Installing for i386-pc platform.[/FONT]
[FONT=Arial]grub-install: error: failed to get canonical path of `/cow'.[/FONT][COLOR=#888888][FONT=Arial]
[/FONT][/COLOR]
```

Thank you,
Tadashi

---

### Post by inayamat on 2022-11-23
Sorry, so I rebooted back into the Live CD before running the (above )commands again.  Thx, Tadashi

---

### Post by oldfred on 2022-11-23
/cow is copy on write or the live installer.
The commands do not work on live installer directly.

---

### Post by inayamat on 2022-11-23
Sorry.  So if the server does not boot and the commands do not work on the live CD directly, what are my options?

Thank you,
Tadashi

---

### Post by oldfred on 2022-11-23
Boot-Repair or full chroot from live installer.
Not sure now if server version is live installer. Several versions ago they changed it.

You can use Ubuntu desktop of server is not live, underlying system is all the same.
Or Boot-Repair in live system, or Boot-Repair ISO which may not be quite as up to date as ppa download.

---

### Post by inayamat on 2022-11-24
Hello.  Ok, so running commands from Live CD does not work and the commands suggested by Boot-Repair did not run either from Live CD.  So I will try full chroot.

Just to step back a little bit, how can I verify that the MBR is set up correctly?

Thank you,
Tadashi

---

### Post by oldfred on 2022-11-24
The Boot-Repair report shows what is in MBR.

---

### Post by inayamat on 2022-11-28
Hello.

The contents of the boot-repair report is at:

[https://pastebin.ubuntu.com/p/6KKBwxBg57/](https://pastebin.ubuntu.com/p/6KKBwxBg57/)

Is the mbr in a good state to move forward to install grub?

Thank you,
Tadashi

---

### Post by oldfred on 2022-11-28
Normally it does not matter what is in MBR when reinstalling grub, it totally overwrites it.

I know now that LVM installs do not require the /boot partition. But grub has to have the .mod file to load the LVM.
I think several posts have mentioned issues and it may be related to grub not added the driver/.mod file required for grub to load the LVM directly.

---

