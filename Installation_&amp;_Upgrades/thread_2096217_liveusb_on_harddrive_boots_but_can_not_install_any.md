---
title: "liveusb on harddrive boots but can not install anything"
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by sdowney717 on 2012-12-19
I tried to install cinammon and then gnome3 and get all sorts of errors
This is the Live USB 12.04 on a hard drive

> ```
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Fetched 57.5 kB in 2s (25.5 kB/s)
Reading package lists... Done
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/ precise/main i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.1%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120823.1)_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/ precise/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.1%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120823.1)_dists_precise_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
ubuntu@ubuntu:~$ sudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnome-shell is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gnome-shell' has no installation candidate
ubuntu@ubuntu:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'synaptic' has no installation candidate
ubuntu@ubuntu:~$ 

```

---

### Post by sdowney717 on 2012-12-19
tried this but then it says I have broken packages
so what to do?

```
ubuntu@ubuntu:~$ sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stableYou are about to add the following PPA to your system:
 This PPA contains the stable releases of cinnamon for Oneiric and Precise. Oneiric will not get any new updates.

Cinnamon website : http://cinnamon.linuxmint.com/
 More info: https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.wfmBVSRNjW --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 109C2938F84496D6ACB6D805A777609328949509
gpg: requesting key 28949509 from hkp server keyserver.ubuntu.com
gpg: key 28949509: public key "Launchpad Gwendal Le Bihan" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Release
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Release
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Packages/DiffIndex
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Packages/DiffIndex
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Translation-en
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Translation-en
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/main TranslationIndex
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/restricted TranslationIndex
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/main Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/main Translation-en
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/restricted Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/restricted Translation-en
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://archive.ubuntu.com precise InRelease                                
Ign http://archive.ubuntu.com precise-updates InRelease
Ign http://ppa.launchpad.net precise InRelease 
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Hit http://archive.ubuntu.com precise Release.gpg                              
Get:2 http://ppa.launchpad.net precise Release.gpg [316 B]
Get:3 http://security.ubuntu.com precise-security Release [49.6 kB]            
Get:4 http://archive.ubuntu.com precise-updates Release.gpg [198 B]          
Get:5 http://ppa.launchpad.net precise Release [11.9 kB]                       
Hit http://archive.ubuntu.com precise Release                                  
Get:6 http://archive.ubuntu.com precise-updates Release [49.6 kB]              
Get:7 http://ppa.launchpad.net precise/main Sources [3,232 B]                  
Get:8 http://security.ubuntu.com precise-security/main amd64 Packages [214 kB] 
Get:9 http://ppa.launchpad.net precise/main amd64 Packages [5,566 B]           
Get:10 http://ppa.launchpad.net precise/main i386 Packages [5,580 B]           
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://archive.ubuntu.com precise/main amd64 Packages                      
Hit http://archive.ubuntu.com precise/restricted amd64 Packages                
Hit http://archive.ubuntu.com precise/main i386 Packages 
Hit http://archive.ubuntu.com precise/restricted i386 Packages
Hit http://archive.ubuntu.com precise/main TranslationIndex
Hit http://archive.ubuntu.com precise/restricted TranslationIndex
Get:11 http://archive.ubuntu.com precise-updates/main amd64 Packages [445 kB]  
Get:12 http://security.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]
Get:13 http://security.ubuntu.com precise-security/main i386 Packages [221 kB] 
Get:14 http://archive.ubuntu.com precise-updates/restricted amd64 Packages [8,366 B]
Get:15 http://archive.ubuntu.com precise-updates/main i386 Packages [453 kB]   
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Get:16 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:17 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]
Get:18 http://security.ubuntu.com precise-security/restricted TranslationIndex [71 B]
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:19 http://security.ubuntu.com precise-security/main Translation-en [104 kB]
Get:20 http://archive.ubuntu.com precise-updates/restricted i386 Packages [8,374 B]
Get:21 http://archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:22 http://archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Hit http://archive.ubuntu.com precise/main Translation-en                      
Hit http://archive.ubuntu.com precise/restricted Translation-en
Get:23 http://security.ubuntu.com precise-security/restricted Translation-en [978 B]
Get:24 http://archive.ubuntu.com precise-updates/main Translation-en [218 kB]  
Get:25 http://archive.ubuntu.com precise-updates/restricted Translation-en [2,082 B]
Fetched 1,815 kB in 2s (737 kB/s)                                    
Reading package lists... Done
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/ precise/main i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.1%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120823.1)_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/ precise/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.1%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120823.1)_dists_precise_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
ubuntu@ubuntu:~$ sudo apti-get install cinnamon
sudo: apti-get: command not found
ubuntu@ubuntu:~$ sudo apt-get install cinnamon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cinnamon : Depends: gjs (>= 1.29.18) but it is not installable
            Depends: libgjs0- but it is not installable
            Depends: libgjs0c (>= 1.32.0) but it is not installable
            Depends: libmozjs185-1.0 (>= 1.8.5-1.0.0) but it is not installable
            Depends: caribou but it is not installable
            Depends: cups-pk-helper but it is not installable
            Depends: mesa-utils but it is not installable
            Recommends: gnome-themes-standard but it is not installable
            Recommends: gnome-session-fallback but it is not installable
            Recommends: nemo but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
ubuntu@ubuntu:~$ 


```

---

### Post by sudodus on 2012-12-19
What do you mean by 'liveusb on harddrive'?

---

### Post by sdowney717 on 2012-12-19
It is a liveusb made from USB creator and installed into a usb 2.0 IDE hard drive. It is a Dynex black case that holds an IDE drive with a usb 2,0 interface

Boots quick compared to a thumb drive

---

### Post by churchy d on 2012-12-19
did you try running apt-get update and then apt-get upgrade first?

---

### Post by sudodus on 2012-12-19
> **sdowney717 said:**
> It is a liveusb made from USB creator and installed into a usb 2.0 IDE hard drive. It is a Dynex black case that holds an IDE drive with a usb 2,0 interface

Boots quick compared to a thumb drive
I think that there is nothing bad with your liveusb HDD as such. I have done similar things, and it works.

But what about the persistence? If you want to install things and keep them, you need a casper-rw file or partition for persistence. Could it be that there is not space enough in your live file system for the installation?

Gnome-shell and Synaptic should be available in 12.04 (they are there for me).

And +1 for the tip about update/upgrade at first :-)

---

### Post by sdowney717 on 2012-12-19
apt-get upgrade is doing some work
I set persistance to 4gb

> Get:245 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main xdiagnose all 2.5.2ubuntu0.1 [59.1 kB]
Get:246 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main xul-ext-ubufox all 2.6-0ubuntu0.12.04.1 [58.5 kB]
Fetched 167 MB in 1min 29s (1,865 kB/s)                                        
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-modules_5.14.2-6ubuntu2.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-modules_5.14.2-6ubuntu2.2_all.deb)  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
ubuntu@ubuntu:~$ 


still at end gave error

now doing the fix missing seems to be progressing!

---

### Post by sdowney717 on 2012-12-19
The partition space is 20gb.
What exactly is the 4gb persistance? User files seaprate from os files?

I found that for Live USB on a harddrive, it needs to be installed on the first partition. When I tried on a second, it would not boot.
It took many hours to move the 300gb partition to the right to free up 20 gb on the front of the partition space.

---

### Post by sdowney717 on 2012-12-19
I do see this error coming up as it is processing the upgrade command.
It eventually skips past it.

> ```
Processing triggers for ureadahead ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab

```

---

### Post by sudodus on 2012-12-19
> **sdowney717 said:**
> The partition space is 20gb.
What exactly is the 4gb persistance? User files seaprate from os files?

I found that for Live USB on a harddrive, it needs to be installed on the first partition. When I tried on a second, it would not boot.
It took many hours to move the 300gb partition to the right to free up 20 gb on the front of the partition space.
4 GB persistence probably means that there is a 4 GB file with a file system inside, that is loop mounted and files in it are added to the live file system from the compressed file to make the root file system. This should work, but sometimes it is corrupted. One common reason for curruption is that you shut off the computer before the live file system is completely saved. In such cases it is best to make a new file for persistence.

I often boot live systems from the second partition (leaving the first one for data available also for Windows). Use boot and lba flags on the partition for booting live sessions!

---

### Post by sudodus on 2012-12-19
If you want to install major packages to a USB system, I suggest that you make a real installation (but to USB instead of an internal drive). This is easier to do, if you disconnect the internal drive.

---

### Post by sdowney717 on 2012-12-19
oh, I tried that on this drive and it did not work. Then I read gparted  needed to start on cylinder so I redid that second partition and still did not work. So then used gparted to do the resize move and now it does boot.

On the other question about that error, here is bug report with a workaround?
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/932663](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/932663)

If I let this upgrade finish and try reboot is it going to be hosed if I dont do this
> Workaround: remove /etc/kernel/*/zz-update-grub before touching kernel packages in the live session.

Also since I have already touched the kernel does this mean I will have to start over?

---

### Post by sdowney717 on 2012-12-19
> **sudodus said:**
> If you want to install major packages to a USB system, I suggest that you make a real installation (but to USB instead of an internal drive). This is easier to do, if you disconnect the internal drive.

yes I was going to ask that too.
If I leave the internal drive connected, then do a real install to an removeable external USB drive, will that affect my current ubuntu 12.04 install in any way?
Would the system become unbootable?

---

### Post by sdowney717 on 2012-12-19
finished with this error
If I follow the bug fix commands it mentionsdist-upgrade? I dont want to goto 12.10!

```
Setting up libqt4-svg (4:4.8.1-0ubuntu4.3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for resolvconf ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
ubuntu@ubuntu:~$ 

```

> Colin Watson (cjwatson) wrote on 2012-02-15: 	#3

Workaround: remove /etc/kernel/*/zz-update-grub before touching kernel packages in the live session.


then somesays this
> winnie666 (winnie666) wrote on 2012-05-04: 	#6

I can confirm that Colin Watson's workaround worked. I just did "sudo rm /etc/kernel/*/zz-update-grub" and "sudo apt-get dist-upgrade" worked with a couple of warnings about missing scripts!


---

### Post by sdowney717 on 2012-12-19
I took a chance and tried it, loooks ok?
```
ubuntu@ubuntu:~$ sudo rm /etc/kernel/*/zz-update-grub
ubuntu@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  totem-plugins
The following NEW packages will be installed:
  gcr libclutter-1.0-0 libclutter-1.0-common libclutter-gst-1.0-0
  libclutter-gtk-1.0-0 libcogl-common libcogl-pango0 libcogl9 libframe6
  libgeis1 libgrail5 libmusicbrainz5-0 libnatpmp1 librhythmbox-core6
  libudisks2-0 linux-headers-3.2.0-35 linux-headers-3.2.0-35-generic
  linux-image-3.2.0-35-generic udisks2
The following packages have been kept back:
  aisleriot gir1.2-totem-1.0 libtotem0 totem totem-common totem-mozilla
The following packages will be upgraded:
  ginn gir1.2-rb-3.0 gnome-disk-utility gnome-keyring libgck-1-0 libgcr-3-1
  libgrip0 librhythmbox-core5 libunity-2d-private0 libunity-core-5.0-5
  linux-generic linux-headers-generic linux-image-generic rhythmbox
  rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder
  rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins
  seahorse transmission-common transmission-gtk unity unity-2d-common
  unity-2d-panel unity-2d-shell unity-2d-spread unity-common unity-services
30 upgraded, 19 newly installed, 1 to remove and 6 not upgraded.
Need to get 73.2 MB of archives.
After this operation, 247 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://security.ubuntu.com/ubuntu/ precise-security/main linux-image-3.2.0-35-generic amd64 3.2.0-35.55 [38.5 MB]
Get:2 http://archive.ubuntu.com/ubuntu/ precise/main libcogl9 amd64 1.10.0-0ubuntu2 [257 kB]

```

---

### Post by sudodus on 2012-12-19
> **sdowney717 said:**
> yes I was going to ask that too.
If I leave the internal drive connected, then do a real install to an removeable external USB drive, will that affect my current ubuntu 12.04 install in any way?
Would the system become unbootable?
It is possible to get it right, but it might be hard to identify where to write things. You must write the root file system *and* the MBR to the right places.

Then you won't touch the internal drive, but a reference to it will be found and it will be added to the grub menu of the USB drive, which is not dangerous but may cause confusion. Also you might find and add a reference to an internal swap partition, which is not found when the USB drive is attached to another computer. You might need to delete a line in /etc/fstab to fix that (unless you will always run in the same computer).

Anyway, disconnecting the internal drive makes things much easier.

---

### Post by sdowney717 on 2012-12-19
The upgrade finished with no errors. However gnome shell and cinammon still will not install
```
ubuntu@ubuntu:~$ sudo add-apt-repository ppa:gnome3-team/gnome3
You are about to add the following PPA to your system:
 Before upgrading your system to a new Ubuntu release (i.e. from Ubuntu 11.10 to 12.10), you should probably run ppa-purge ppa:gnome3-team/gnome3 first.

=== Ubuntu 12.10 (Quantal) ===
Parts of GNOME 3.6 that didn't make it into the normal Ubuntu 12.10 repositories.

=== Ubuntu 12.04 (Precise) ===
Parts of GNOME 3.4 that didn't make it into the normal Ubuntu 12.04 repositories.

=== Ubuntu 11.10 (Oneiric) ===
Parts of GNOME 3.2 that didn't make it into the normal Ubuntu 11.10 repositories.

There are no further updates for Oneiric/11.10!
 More info: https://launchpad.net/~gnome3-team/+archive/gnome3
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmp3PEhTy/secring.gpg' created
gpg: keyring `/tmp/tmp3PEhTy/pubring.gpg' created
gpg: requesting key 3B1510FD from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp3PEhTy/trustdb.gpg: trustdb created
gpg: key 3B1510FD: public key "Launchpad PPA for GNOME3 Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
You are about to add the following PPA to your system:
 This PPA contains the stable releases of cinnamon for Oneiric and Precise. Oneiric will not get any new updates.

Cinnamon website : http://cinnamon.linuxmint.com/
 More info: https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmptVFnrT/secring.gpg' created
gpg: keyring `/tmp/tmptVFnrT/pubring.gpg' created
gpg: requesting key 28949509 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmptVFnrT/trustdb.gpg: trustdb created
gpg: key 28949509: public key "Launchpad Gwendal Le Bihan" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
ubuntu@ubuntu:~$ sudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnome-shell is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

W: Duplicate sources.list entry cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/ precise/main i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.1%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120823.1)_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/ precise/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.1%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120823.1)_dists_precise_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Package 'gnome-shell' has no installation candidate
ubuntu@ubuntu:~$ sudo apt-get install cinnamon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cinnamon : Depends: gjs (>= 1.29.18) but it is not installable
            Depends: libgjs0- but it is not installable
            Depends: libgjs0c (>= 1.32.0) but it is not installable
            Depends: libmozjs185-1.0 (>= 1.8.5-1.0.0) but it is not installable
            Depends: caribou but it is not installable
            Depends: cups-pk-helper but it is not installable
            Depends: mesa-utils but it is not installable
            Recommends: gnome-themes-standard but it is not installable
            Recommends: gnome-session-fallback but it is not going to be installed
            Recommends: nemo but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
ubuntu@ubuntu:~$ 

```

---

### Post by sdowney717 on 2012-12-19
I get an error duplicate sources, so here is the list.
What should be removed?
```
# /etc/apt/sources.list

deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/

deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/

deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted

deb http://archive.ubuntu.com/ubuntu/ precise main restricted
deb http://security.ubuntu.com/ubuntu/ precise-security main restricted
deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted

```

I commented out all the cdrom sources and update error went away.

---

### Post by sdowney717 on 2012-12-19
I think I got cinammon and gnome3 shell installed. Problem was universe and multiverse repositories needed enabling. the software center has no link to edit sources?
So I installed synaptic from software center, then in synaptic edited the software cources and was able to select the repositories.

gnome3 stuff here
[http://www.upubuntu.com/2012/04/how-to-enable-and-install-gnome-shell.html](http://www.upubuntu.com/2012/04/how-to-enable-and-install-gnome-shell.html)

---

### Post by sudodus on 2012-12-19
Congratulations!

I think you solved your problems without much relevant help: It was a problem with repositories, that needed enabling.

I learned as much as much as you from this thread ;-)

---

### Post by sdowney717 on 2012-12-20
Yes, it is all working. I am able to install anything including Eclipse.

However, I am bumping up against a space issue. Down to 437mb free.
Still it is quite usable as it is.


Is there a way to increase the available liveusb space? A thumb drive could be much greater than 4 or 8gb.

---

### Post by sdowney717 on 2012-12-20
[http://ubuntuforums.org/showthread.php?t=1448929](http://ubuntuforums.org/showthread.php?t=1448929)

I did find this. He talks about increasing the size of the casper rw file.
Is that file limiting my space?
The fat 32 partition holding the liveusb is 20gb in size.

Down to 200mb free. I think I will wipe this out and just do an install to the USB hard drive.

---

### Post by sudodus on 2012-12-20
If you use a casper-rw ***partition*** you will not be limited by the 4GB max file size in FAT32.

There is more info at this link[[COLOR="Red"]https://help.ubuntu.com/community/LiveCD/Persistence[/COLOR]]("https://help.ubuntu.com/community/LiveCD/Persistence")

I suggest using gparted to create the partitions on your USB drive

---

