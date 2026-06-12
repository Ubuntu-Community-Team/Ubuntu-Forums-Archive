---
title: "Grub2 Update Stops UEFI Dual Boot"
date: 2020-08-05
forum: Installation &amp; Upgrades
---

### Post by mgrindle on 2020-08-05
Two days ago, I did a system update from CLI on my ACER laptop running Kubuntu 18.04 x86-64 on an SSD. It dual boots with Windows 10 on a HD using UEFI boot. Upon rebooting the system, when I try to run Kubuntu, I get the following messages during boot:

 
 
 error: /vmlinux-5.4.0-42-generic has invalid signature

 error: you need to load the kernel first.
 Press any key to continue

 
 
 It takes me back to the boot options menu. If I select the Advanced Options and pick a previously working kernel, I get the same messages only the kernel # matches the one I selected. So I can not boot into any kernel. Booting into linux fails under UEFI.

 
 
 The computer will boot successfully into Windows 10.

 
 
 I next attempt to correct the invalid signature error by booting from a USB thumbdrive with Kubuntu 18.04.4 and another thumbdrive with 18.04.3 so I can chroot into the SSD installation to correct the error. I can't boot with either thumbdrive. The boot fails with the following messages:

 
 
 Failed to open \EFI\BOOT\mmx64.efi – Not Found.

 Failed to load image \EFI\BOOT\mmx64.efi – Not Found
 Failed to start MokManager: Not Found

 Something has gone seriously wrong: import_mok_state() failed: Not Found
 
 
 Then the machine powers down.

 
 
 I then attempt boots with: a Kubuntu 18.04.3 LiveDVD, a CentOS 7 install DVD and a Gparted 1.0.0.5 USB thumbdrive. All these have worked in the past. None of these will boot under UEFI. I get the same messages as with the Kubuntu 18.04 thumbdrives. I can not boot anything when UEFI boot is active.

 
 
 I can switch to the Legacy boot and all is well with the LiveCDs and DVDs. When I try to boot Kubuntu from the SSD install using Legacy boot, there is no entry in GRUB2. So it still will not boot.

 
 
 How do I fix the Kubuntu SSD install to work under UEFI boot (the invalid signature problem)? And how do you fix the problem where no LiveCDs and DVDs will not boot under UEFI?

---

### Post by CatKiller on 2020-08-05
Your short-term fix is probably to turn off Secure Boot.

I couldn't say whether your inability to boot from your live images is because you've removed the Secure Boot keys yourself, they've got removed during a UEFI update, or if they've been invalidated as part of the BootHole mitigations.

Whatever the reason, turning off Secure Boot means that you won't attempt to use any keys. Then you can look into enrolling valid keys at some future point.

---

### Post by mgrindle on 2020-08-05
CatKiller, thanks for the reply.

I'm no expert on UEFI but I don't believe I did anything to 'remove' the Secure Boot keys. I've not yet attempted to validate the signature of the vmlinux kernel with my own signature.

I can't/haven't attempted to run the SSD Kubuntu install under the Legacy boot.

I did switch back to UEFI boot and set-up the boot option for Kubuntu and it will not boot.

---

### Post by oldfred on 2020-08-05
UEFI updates may reset UEFI to defaults. UEFI does remember some settings. Back with BIOS, all settings were reverted to defaults and you had to redo them.
With my UEFI system I have 5 or 7 settings I change, some required & some optional and I review them after every UEFI update.

---

### Post by mgrindle on 2020-08-05
oldfred -

That is quite the post on UEFI! It will take some time to digest and find a solution to try. Thanks. I'll update this post when I've completed my work.

---

### Post by pbear42 on 2020-08-05
> **mgrindle said:**
> 
 Failed to open \EFI\BOOT\mmx64.efi &#8211; Not Found.

 Failed to load image \EFI\BOOT\mmx64.efi &#8211; Not Found
 Failed to start MokManager: Not Found

 Something has gone seriously wrong: import_mok_state() failed: Not Found
This happens on my HP laptop (Insyde F.49 UEFI) if I run the installer with secure boot enabled and select *install third party apps*.  Once it happens, there is no solution except to reflash the firmware.  Not even turning off secure boot works.  The bug has many forms, [for example]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171"), and different solutions works for different users.  See, e.g., [askubuntu]("https://askubuntu.com/questions/1085550/cant-install-ubuntu-18-10-on-xps-15-efi-boot-mmx64-efi-not-found") and [STechnical]("https://smarttechnicalworld.com/cant-install-ubuntu-efibootmmx64-efi-not-found/").

---

### Post by oldfred on 2020-08-05
You only need mmx64.efi, to set your own key to install proprietary drivers when UEFI Secure Boot is on.
Ubuntu cannot verify that a proprietary driver is certified, but a user can if he believes it is or developed it himself.

Many just copy shimx64.efi and rename it to mmx64.efi.
After install, you will have a valid mmx64.efi in the install in the ESP system partition even with Secure Boot off. 

I have Secure Boot off.

```
fred@z97-focal-kubuntu:~$ ll /boot/efi/EFI/ubuntu
total 4204
drwxr-xr-x 2 root root    4096 Jun 21 16:22 ./
drwxr-xr-x 6 root root    4096 Jun 18 09:25 ../
-rwxr-xr-x 1 root root     108 Aug  1 08:14 BOOTX64.CSV*
-rwxr-xr-x 1 root root     126 Aug  1 08:14 grub.cfg*
-rwxr-xr-x 1 root root 1681280 Aug  1 08:14 grubx64.efi*
-rwxr-xr-x 1 root root 1269496 Aug  1 08:14 mmx64.efi*
-rwxr-xr-x 1 root root 1334816 Aug  1 08:14 shimx64.efi*

```

---

### Post by mgrindle on 2020-08-08
Still have not gotten my system fixed due to the system update that bricked my Kubuntu install on a dual boot Acer laptop. I've been down so many rabbit holes trying to solve this. Now I finally run across a link from Ubuntu on the botched attempt to fix the BootHole vulnerability and a proposed fix to the fix. Here is the link to that article:  [https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/GRUB2SecureBootBypass?WUwbDVmRWk5RCtJZ2IyNUU2SyJ9#Recovery](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/GRUB2SecureBootBypass?WUwbDVmRWk5RCtJZ2IyNUU2SyJ9#Recovery) .

I have not tried it yet. Basically you are rolling back the botched fix. Good luck. I'll report back when I've attempted this 'fix'.

---

### Post by mgrindle on 2020-08-09
Well, finally some success in resolving the muck-up in the fix of BootHole vulnerability I applied thru system update on Monday, August 3, 2020.  As indicated in my post above, I found an Ubuntu Wiki article (last update 2020-08-05) where they admitted they messed up and how to reverse the damage but not fix the BootHole issue.

There is still a minor problem after completing this process but my system will now UEFI SecureBoot boot Kubuntu 18.04 installed on a SSD in a dual boot system, with Windows 10.

From the Wiki post, this is the process I followed to Fix the Botched GRUB2 BootHole Problem. NOTE: This only reverses the updates and removes the bad fix.

- First, you have to create a LiveCD USB of the latest Ubuntu/Kubuntu 20.04 distro. Older vresions of the OS or another OS do not boot for me. I had to use Kubuntu 20.04 to get around the ‘mmx65.efi missing error’ on older versions of the OS. You will need internet access later in this process!

- Boot computer with LiveCD USB. 

- Open Terminal session

- Mount the root filesystem and components for your installed OS. You also need to mount specific directories for the chroot environment to be used later. My Kubuntu root  is installed on a SSD, on the 3[SUP]rd[/SUP] partition. You need to determine what is correct for the root partition on your installation.

```
   sudo mount /dev/nvme0n1p3 /mnt
   
   for i in /sys /proc /run /dev /dev/pts ; do sudo mount --bind "$i" "/mnt$i"; done

   sudo mv /mnt/etc/resolv.conf /mnt/etc/resolv.conf.bak

   sudo cp -L /etc/resolv.conf /mnt/etc/
```
   
- I have a separate partition for /boot so I need to mount it as well:

```
   sudo mount /dev/nvme0n1p1 /mnt/boot
```
   
- Now CHROOT into the SSD filesystem:

```
   sudo chroot /mnt
```
   
- Find installed kernels on SSD:

```
   dpkg -l | grep linux-image
```

- You likely can skip this step. I messed up part of the kernel boot files during other attempts to fix this problem. If you do this step, BE SURE to determine the correct kernel version number/name. So I had to reinstall latest kernel ontothe SSD install:

```
    sudo apt-get install --reinstall linux-image-5.4.0-42-generic
```
    
- Mount the /boot/efi directory 

```
   mount /boot/efi
```
   
- From the instructions on the Wiki page now, Download and Install a previous 'working' version of grub2/grub2-signed. It is imperative that you determine from the Wiki page the correct grub2 version to downgrade to for this process to work. You have to do this with .deb packages. This worked for me YMMV.

   GRUB2_VERSION=2.02-2ubuntu8.15

   GRUB2_LP_URL=[https://launchpad.net/ubuntu/+source/grub2/$GRUB2_VERSION/+build/18831561/+files](https://launchpad.net/ubuntu/+source/grub2/$GRUB2_VERSION/+build/18831561/+files)

   GRUB2_SIGNED_VERSION=1.93.16

   GRUB2_SIGNED_LP_URL=[https://launchpad.net/ubuntu/+source/grub2-signed/$GRUB2_SIGNED_VERSION/+build/18831639/+files](https://launchpad.net/ubuntu/+source/grub2-signed/$GRUB2_SIGNED_VERSION/+build/18831639/+files)

```
   cd /tmp

   for i in grub-common grub-efi grub-efi-amd64 grub-efi-amd64-bin grub2-common ; do wget $GRUB2_LP_URL/${i}_${GRUB2_VERSION}_amd64.deb ; done

   wget $GRUB2_SIGNED_LP_URL/grub-efi-amd64-signed_${GRUB2_SIGNED_VERSION}+${GRUB2_VERSION}_amd64.deb

   dpkg -i ./grub*.deb
```
   
   
- Notice the output below shows an error when running the last command. I decide because it is a conflict in dependencies not to do anything about it now.

```
root@kubuntu:/tmp# dpkg -i ./grub*.deb
dpkg: warning: downgrading grub2-common from 2.02-2ubuntu8.17 to 2.02-2ubuntu8.15
(Reading database ... 445158 files and directories currently installed.)
Preparing to unpack .../grub2-common_2.02-2ubuntu8.15_amd64.deb ...
Unpacking grub2-common (2.02-2ubuntu8.15) over (2.02-2ubuntu8.17) ...
dpkg: warning: downgrading grub-common from 2.02-2ubuntu8.17 to 2.02-2ubuntu8.15
Preparing to unpack .../grub-common_2.02-2ubuntu8.15_amd64.deb ...
Running in chroot, ignoring request.
Running in chroot, ignoring request: daemon-reload
Running in chroot, ignoring request: is-active
Running in chroot, ignoring request: stop
Unpacking grub-common (2.02-2ubuntu8.15) over (2.02-2ubuntu8.17) ...
Running in chroot, ignoring request: daemon-reload
Selecting previously unselected package grub-efi.
Preparing to unpack .../grub-efi_2.02-2ubuntu8.15_amd64.deb ...
Unpacking grub-efi (2.02-2ubuntu8.15) ...
Selecting previously unselected package grub-efi-amd64.
dpkg: considering removing grub-pc in favour of grub-efi-amd64 ...
dpkg: no, cannot proceed with removal of grub-pc (--auto-deconfigure will help):
 grub-gfxpayload-lists depends on grub-pc (>= 1.99~20101210-1ubuntu2)
  grub-pc is to be removed.

dpkg: regarding .../grub-efi-amd64_2.02-2ubuntu8.15_amd64.deb containing grub-efi-amd64:
 grub-efi-amd64 conflicts with grub-pc
  grub-pc (version 2.02-2ubuntu8.17) is present and installed.

dpkg: error processing archive ./grub-efi-amd64_2.02-2ubuntu8.15_amd64.deb (--install):
 conflicting packages - not installing grub-efi-amd64
dpkg: warning: downgrading grub-efi-amd64-bin from 2.02-2ubuntu8.17 to 2.02-2ubuntu8.15
Preparing to unpack .../grub-efi-amd64-bin_2.02-2ubuntu8.15_amd64.deb ...
Unpacking grub-efi-amd64-bin (2.02-2ubuntu8.15) over (2.02-2ubuntu8.17) ...
dpkg: warning: downgrading grub-efi-amd64-signed from 1.93.19+2.02-2ubuntu8.17 to 1.93.16+2.02-2ubuntu8.15
Preparing to unpack .../grub-efi-amd64-signed_1.93.16+2.02-2ubuntu8.15_amd64.deb ...
Unpacking grub-efi-amd64-signed (1.93.16+2.02-2ubuntu8.15) over (1.93.19+2.02-2ubuntu8.17) ...
Setting up grub-common (2.02-2ubuntu8.15) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Running in chroot, ignoring request: daemon-reload
Running in chroot, ignoring request.
Running in chroot, ignoring request: daemon-reload
Running in chroot, ignoring request: is-active
Running in chroot, ignoring request: start
dpkg: dependency problems prevent configuration of grub-efi:
 grub-efi depends on grub-efi-amd64 (= 2.02-2ubuntu8.15); however:
  Package grub-efi-amd64 is not installed.

dpkg: error processing package grub-efi (--install):
 dependency problems - leaving unconfigured
Setting up grub-efi-amd64-bin (2.02-2ubuntu8.15) ...
Setting up grub-efi-amd64-signed (1.93.16+2.02-2ubuntu8.15) ...
Installing for x86_64-efi platform.
Installation finished. No error reported.
Setting up grub2-common (2.02-2ubuntu8.15) ...
Processing triggers for install-info (6.5.0.dfsg.1-2) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for systemd (237-3ubuntu10.41) ...
Running in chroot, ignoring request: daemon-reload
Processing triggers for ureadahead (0.100.0-21) ...
Errors were encountered while processing:
 ./grub-efi-amd64_2.02-2ubuntu8.15_amd64.deb
 grub-efi
root@kubuntu:/tmp# 


```
- Finishing steps of the Wiki process:
```

   cp -df /etc/resolv.conf.bak /etc/resolv.conf
```
   
- Unmount
   
```
   umount /boot/efi
```
      
- Exit chroot environment

```
   exit
```
   
- Unmount the SSD filesystem:

```
   sudo umount /mnt/boot    # Says: ‘Target is busy??’ I ignored this because it’s
                                    in the LiveCD environment.
    
   sudo umount /mnt/sys
   sudo umount /mnt/run
   sudo umount /mnt/dev/pts
   sudo umount /mnt/dev
   sudo umount /mnt/proc
   
 - Reboot like normal (with UEFI and SecureBoot) into the installed Kubuntu OS. IT WORKS!
   
****** After Successful UEFI Reboot into Kubuntu 18.04 on installed system SSD drive:

- To check on the package dependency problem, I run a system update:

$ sudo apt-get update && sudo apt-get --with-new-pkgs upgrade
[sudo] password for z973-admin: 
Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [88.7 kB]          
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease                                                      
Hit:3 [http://packages.microsoft.com/repos/vscode](http://packages.microsoft.com/repos/vscode) stable InRelease                                               
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]                              
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB]                  
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 DEP-11 Metadata [294 kB]
Get:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 DEP-11 Metadata [46.0 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 DEP-11 Metadata [279 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 DEP-11 Metadata [49.2 kB]
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports/universe amd64 DEP-11 Metadata [9,292 B]
Fetched 935 kB in 2s (553 kB/s)                                             
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 grub-efi : Depends: grub-efi-amd64 (= 2.02-2ubuntu8.15)
 grub-pc : Depends: grub-common (= 2.02-2ubuntu8.17)
           Depends: grub2-common (= 2.02-2ubuntu8.17)
 grub-pc-bin : Depends: grub-common (= 2.02-2ubuntu8.17)
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
$ 

```
At this point, I’m not sure what to do next. It appears there are two versions of pieces of the grub stuff. My question is: Do I even need to have grub-pc and grub-pc-bin installed? The system boots and operates corectly as far as I can tell.

Note: after this fix, you still can not boot any older LiveUSBs or DVD’s. The Boot choices menu (F12 on my system) does not even show a bootable device for the LiveUSB! I think that is the intended action  but I’m not sure.

---

### Post by oldfred on 2020-08-09
Most UEFI with Secure boot on do not allow USB boot. As that is then a security issue.
Again if UEFI updated it reverts to defaults. So you probably have to go into UEFI and turn on full USB support or allow USB boot or similar setting.

---

### Post by mgrindle on 2020-08-11
> **oldfred said:**
> Most UEFI with Secure boot on do not allow USB boot. As that is then a security issue.
Again if UEFI updated it reverts to defaults. So you probably have to go into UEFI and turn on full USB support or allow USB boot or similar setting.

                        oldfred – Before I get into the solution to my problem, I wanted to let you know that with UEFI SecureBoot  active after the BootHole fix such as it is now that:  

 1) The latest (K)ubuntu 20.04 LiveCD USB will boot fine on my system.
 
 2) Any older versions, and any older, pre-existing LiveCD USBs/DVDs of other distros (Centos 7, Gparted 1.0.0.5 USB are examples I tried) do not show as bootable devices

 YMMV

---

### Post by mgrindle on 2020-08-11
I was able to successfully resolve the dependency conflict. If you will remember in the last episode, I ran the instructions provided in the Ubuntu Wiki article. Afterwards, I was able to reboot my dual-boot Acer laptop into the Kubuntu 18.04 OS on a separate SSD drive from Windows 10 with UEFI SecureBoot active.

 The result, however, was a dependency conflict in some of the grub2 components. At this point, you do NOT need the mess with the chroot process because you can boot the installed (K)ubuntu OS.
 
 The first step should be to BACK-UP YOUR DATA! You saved your OS. Don&#8217;t throw it all away now. Or you could clone the HD/SSD as a back-up just in case your result is not as good as mine.
 
 Be sure UEFI SecureBoot is active in your BIOS setup. If it&#8217;s not then I can not say if this procedure will work because you probably ran the prior Ubuntu Wiki fix without it active.
 
 - Boot into your installed (K)ubuntu OS.
 
 - Open a terminal session
 
 - Analyzing the conflicts and what versions of pieces of grub(2) were installed, I decided that my last system update bumped the version of grub-pc and grub-pc-bin to .17  Since the fix to the BootHole fix downgraded all (?) the other components of grub(2) to version .15 , I need to downgrade grub-pc and grub-pc-bin as well. I run these steps:
 [INDENT]GRUB2_VERSION=2.02-2ubuntu8.15

 GRUB2_LP_URL=https://launchpad.net/ubuntu/+source/grub2/$GRUB2_VERSION/+build/18831561/+files
 cd /tmp
 for i in grub-pc grub-pc-bin ; do wget $GRUB2_LP_URL/${i}_${GRUB2_VERSION}_amd64.deb ; done
 sudo dpkg -i ./grub*.deb
[/INDENT]
  
 
 - Everything above runs successfully.

 - Now check the state of the dependency problem:
 [INDENT]cd

 sudo apt-get -s upgrade
[/INDENT]
  
 
 - Looks like we are still missing something, grub-efi-amd64. It was listed as not installed
    in the first round of downgrades:


     [INDENT]$ sudo apt-get -s upgrade

 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 You might want to run 'apt --fix-broken install' to correct these.
 The following packages have unmet dependencies:
  grub-efi : Depends: grub-efi-amd64 (= 2.02-2ubuntu8.15)
 E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
 $  
[/INDENT]
  
 
 - You can reboot your system at this point to see that it still boots into the (K)ubuntu 18.04 OS.
 
 
 - I go thru the exercise of trying to download and install the &#8216;missing&#8217; package grub-efi-amd64. Cutting to the end result, you can&#8217;t install grub-efi-amd64 if grub-pc is installed:
 
 [INDENT]dpkg: considering removing grub-pc in favour of grub-efi-amd64 ...

 dpkg: no, cannot proceed with removal of grub-pc (--auto-deconfigure will help):
  grub-gfxpayload-lists depends on grub-pc (>= 1.99~20101210-1ubuntu2)
   grub-pc is to be removed.
[/INDENT]
  
 [INDENT]dpkg: regarding .../grub-efi-amd64_2.02-2ubuntu8.15_amd64.deb containing grub-efi-amd64:
  grub-efi-amd64 conflicts with grub-pc
   grub-pc (version 2.02-2ubuntu8.15) is present and installed.
 
 
 dpkg: error processing archive ./grub-efi-amd64_2.02-2ubuntu8.15_amd64.deb (--install):
  conflicting packages - not installing grub-efi-amd64
 Errors were encountered while processing:
  ./grub-efi-amd64_2.02-2ubuntu8.15_amd64.deb
[/INDENT]
  
 
 ********************************************************************
 *
 *  Now I go back to analyse the first set of downgrades and the resulting errors, it is
 *   my opinion that: I must remove the 'grub-efi' package. It seems that the package
 *   was installed for the first time not downgraded as the other packages were. I
 *   believe this is what introduced the dependency conflicts.
 *
 *********************************************************************
 
 
 - Remove the package: grub-efi added by the Ubuntu fix
 
 [INDENT]sudo apt-get remove grub-efi
[/INDENT]
 
 
 
 - The result:
 
 [INDENT]$ sudo apt-get remove grub-efi                                                                                                

 Reading package lists... Done                                                                                                                     
 Building dependency tree                                                                                                                          
 Reading state information... Done                                                                                                                 
 The following packages were automatically installed and are no longer required:                                                                   
   libllvm9 libllvm9:i386 linux-headers-5.3.0-59 linux-headers-5.3.0-59-generic linux-headers-5.3.0-61 linux-headers-5.3.0-61-generic
   linux-image-5.3.0-59-generic linux-image-5.3.0-61-generic linux-modules-5.3.0-59-generic linux-modules-5.3.0-61-generic
   linux-modules-extra-5.3.0-59-generic linux-modules-extra-5.3.0-61-generic
 Use 'sudo apt autoremove' to remove them.
 The following packages will be REMOVED:
   grub-efi
 0 upgraded, 0 newly installed, 1 to remove and 53 not upgraded.
 1 not fully installed or removed.
 After this operation, 16.4 kB disk space will be freed.
 Do you want to continue? [Y/n] y
 (Reading database ... 445161 files and directories currently installed.)
 Removing grub-efi (2.02-2ubuntu8.15) ...
 $  
[/INDENT]
  
 
 - Now check to see if the dependency problem is resolved:
 
 [INDENT]cd

  sudo apt-get -s upgrade
[/INDENT]
 
 
 
 - SUCCESS!!!!!!!!!!  No dependency conflicts are reported. And my system boots fine with UEFI SecureBoot active.
 
 
 The system upgrade package list includes grub2 updates to version .17  DON&#8217;T RUN the upgrade. You&#8217;ll just be back in the same place. You need to keep reading any advisories about BootHole to see when the &#8216;final fix&#8217; is available.
 
 I personally will put a &#8216;hold&#8217; on any grub/grub2 package upgrades until I&#8217;m aware the grub storm has passed. You are on your own to do this part.
 
 A final note. Downgrading all these grub(2) packages probably makes your system vulnerable to  BootHole again. So be careful!

---

### Post by CatKiller on 2020-08-11
Glad you found a solution that works for you.

> **mgrindle said:**
> Do I even need to have grub-pc and grub-pc-bin installed? The system boots and operates corectly as far as I can tell.

I didn't reply to this earlier because I didn't want to wade through all the formatting on that post on my phone. As I understand it, grub-pc is what lets a Linux machine boot in BIOS mode rather than UEFI mode. Since you want to use Secure Boot, which BIOS can't use, you don't particularly need that package.

---

### Post by mgrindle on 2020-08-11
> **CatKiller said:**
> Glad you found a solution that works for you.

I didn't reply to this earlier because I didn't want to wade through all the formatting on that post on my phone. As I understand it, grub-pc is what lets a Linux machine boot in BIOS mode rather than UEFI mode. Since you want to use Secure Boot, which BIOS can't use, you don't particularly need that package.

It's really strange. It's also my understanding that grub-pc allows booting in BIOS/Legacy mode. But my system is configured to boot in UEFI SecureBoot but gives the option for Legacy boot and I have grub-pc installed. Perhaps the case is if your system can boot both Legacy and UEFI, the OS installs grub-pc. If your system can only boot using UEFI, it installs grub-efi during the installation.

The real answer is above my pay grade.

---

