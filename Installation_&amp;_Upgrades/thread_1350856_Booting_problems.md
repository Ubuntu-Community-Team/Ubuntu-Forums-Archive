---
title: "Booting problems"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by johnmic on 2009-12-09
Hi,

I'm a relative newbie to Linux, and Google is no longer providing answers to my problems, so I was hoping someone could lend a hand. I'll say what the problem I'm having is, then what I did up to that stage.

When I boot up the computer, I get the message that the GRUB is loading. An error message then comes up, but the GRUB loads succesfully before I can get any details - all I know is that it starts with 'error: no such device: ' and then some characters. However, GRUB does come up fine, and allows me to boot XP with no hassle. However, when I try booting Ubuntu 9.10 in either normal or recovery mode, I am presented with the error message 'error: no such device: 11d28c19-a3b0-41c3-9b27-3948189f5056'. It then tells me to press any key, which takes me back to the GRUB.

The background is, as briefly as I can put it, that I am running a Compaq nx6110, originally with a 40GB IDE drive, 256MB of RAM. I upgraded the RAM a long time ago to 2GB, no problem. I also updated the BIOS lately to the most recent version, f.14 (ROM family 68DTD), and tried to upgrade the hard-drive to a 320GB WD IDE drive. Unfortunately, the BIOS is not 48 LBA (I think, by process of elimination). To get round this, I partitioned the drive so Windows XP Professional was installed on the first 120GB of the drive - this works no problem. I then instructed Ubuntu to install on the same partition, resizing Windows to 50GB, Ubuntu taking up the rest of the 120GB. The intention was to figure out some way of partitioning the rest of the drive later to give myself access to that, but baby steps.

Any help that can be given would be greatly appreciated. I've had several issues with installing Ubuntu, most recently this, before that the GRUB refused to install properly (I think this may have been due to my partitioning the entire drive from the get-go, forcing GRUB to try and install itself at the end of the drive, where the BIOS refuses to go). I'll be honest - I don't know how to reinstall Ubuntu over itself, only to install it again, so if that's the only strategy, if you could point me to a manual on how to do that, that would be fantastic.

Thanks for any possible help!
johnmic

---

### Post by kansasnoob on 2009-12-09
It sounds like this is Ubuntu 9.10, is that correct?

Also please boot the Live CD choosing to Try without changes to the computer and from the live Desktop go to Terminal and post the output of the following command:

```
sudo fdisk -l
```

BTW that's a lower case L.

---

### Post by darkod on 2009-12-09
For start, boot with the ubuntu cd, select Try Ubuntu, and when it loads open terminal (in Applications-Accessories) and execute:
sudo blkid

Copy the results here. When you are booted like that with the LiveCD you should have internet access so you can stay booted with it, post on the forum and try to troubleshoot. No need to reboot in windows for internet access, etc.

---

### Post by johnmic on 2009-12-09
Thanks very much for the speedy response!

For sudo fdisk -l, I get:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x182c182b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6532    52468258+   7  HPFS/NTFS
/dev/sda2            6533       38913   260100382+   5  Extended
/dev/sda5            6533       38164   254084008+  83  Linux
/dev/sda6           38165       38913     6016311   82  Linux swap / Solaris

When I put in sudo blkid, I get:

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="4AD8D1F7D8D1E16D" TYPE="ntfs" 
/dev/sda5: UUID="11d28c19-a3b0-41c3-9b27-3948189f5056" TYPE="ext4" 
/dev/sda6: UUID="9a8da0df-9db5-412a-b754-fe553964adb4" TYPE="swap" 

I hope that means something to you...

---

### Post by johnmic on 2009-12-09
Sorry, forgot to mention - yes, it is 9.10

---

### Post by kansasnoob on 2009-12-09
> **johnmic said:**
> Thanks very much for the speedy response!

For sudo fdisk -l, I get:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x182c182b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6532    52468258+   7  HPFS/NTFS
/dev/sda2            6533       38913   260100382+   5  Extended
/dev/sda5            6533       38164   254084008+  83  Linux
/dev/sda6           38165       38913     6016311   82  Linux swap / Solaris

When I put in sudo blkid, I get:

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="4AD8D1F7D8D1E16D" TYPE="ntfs" 
/dev/sda5: UUID="11d28c19-a3b0-41c3-9b27-3948189f5056" TYPE="ext4" 
/dev/sda6: UUID="9a8da0df-9db5-412a-b754-fe553964adb4" TYPE="swap" 

I hope that means something to you...

I don't know why but grub2 sometimes messes up during installation so I'd mount and chroot Ubuntu and reinstall grub2 from terminal. Just copy-n-paste these commands:

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
grub-install /dev/sda
```

```
update-grub
```

Be patient that takes a minute or so to complete!

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Hopefully that will let you boot Ubuntu but you probably won't have an option to boot Windows so as soon as you get booted into Ubuntu go to terminal and:

```
sudo update-grub
```

That should find Windows.

---

### Post by johnmic on 2009-12-09
Thanks very much for the help. Unfortunately, it doesn't seem to have worked - same error message as before. To make things worse, when I try entering 'sudo update-grub', I get an error message back, saying 'grub-probe: error: cannot find a device for /.' This unfortunately means that booting with the Live CD is the only way to use my computer now!

---

### Post by johnmic on 2009-12-09
I'll admit, I should have checked this before I posted - sorry about that.

I tried to load the GRUB to play around with it, to be informed that GRUB wasn't installed, which was curious. I consequently used 'apt-get install grub' to get it, and 'update-grub' to try updating it. Now, when I enter GRUB, and try the command 'find /boot/grub', I get 'error 15: File Not Found'. However, from terminal, /boot/grub is there, but there exist no stage1 or stage2 folders. I haven't rebooted yet, but I'll admit, this is looking bad...

---

### Post by johnmic on 2009-12-09
It seems the GRUB is still working, but Windows is not there still.

---

### Post by kansasnoob on 2009-12-09
There are two different grubs now. The package "grub" is the old legacy grub. The new grub is called grub2 but the package it uses is "grub-pc".

So if you installed grub it probably removed grub-pc so you now have both a broken grub and a broken grub2. So let's mount and chroot again.

This time please copy-n-paste the results from the terminal here before you even try to reboot so I can see what's up.

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
mv /boot/grub /boot/grub_old
```

```
mkdir /boot/grub
```

```
apt-get --purge remove grub grub-common
```

```
apt-get install grub-pc
```

```
update-grub
```

```
grub-install /dev/sda
```

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

If that doesn't work we'll try reverting to legacy grub. Don't worry!

---

### Post by johnmic on 2009-12-10
Thanks very much for the help - it's really appreciated. I got partway through the instructions, then bad things happened - here is what my terminal told me:
```

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
root@ubuntu:/# mv /boot/grub /boot/grub_old
root@ubuntu:/# mkdir /boot/grub
root@ubuntu:/# apt-get --purge remove grub grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
The following packages will be REMOVED:
  grub-common* grub-pc*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 4,170kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 114173 files and directories currently installed.)
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for sreadahead ...
Processing triggers for install-info ...
root@ubuntu:/# apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-pc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package grub-pc has no installation candidate
root@ubuntu:/# apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-pc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package grub-pc has no installation candidate
root@ubuntu:/# 

```

This isn't going so well...

---

### Post by kansasnoob on 2009-12-10
Something's goofy with package management!

No worries! Lets just install and setup legacy grub. If you have already exited the chroot then mount & chroot again (otherwise skip the first step):

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
apt-get install grub
```

```
update-grub
```

You'll be asked if you want to create a /boot/grub/menu.lst - yes, you do, so type y and enter!

```
grub-install /dev/sda
```

Now we'll enter a grub shell:

```
grub
```

```
find /boot/grub/stage1
```

Should show (hd0,4) - that's zero,four, so:

```
root (hd0,4)
```

```
setup (hd0)
```

You should see this:

> Checking if "/boot/grub/stage1" exists... **yes**
Checking if "/boot/grub/stage2" exists... **yes**
Checking if "/boot/grub/e2fs_stage1_5" exists... **yes**
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...* 15 sectors are embedded.
**succeeded**
Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... **succeeded**
Done. 

So just leave the grub shell:

```
quit
```

Then exit and unmount the chroot:

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Hopefully you'll then be able to boot Ubuntu. If so then we'll add Windows to the menu.lst.

I'll hang right here with you!

---

### Post by kansasnoob on 2009-12-10
If the package grub fails to install I'd like to see the output of:

```
cat /etc/apt/sources.list
```

That will need to be run in the chroot environment!

---

### Post by johnmic on 2009-12-10
And so the saga continues! Here's what I'm getting so far:

```

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
mount: /dev/sda5 already mounted or /mnt busy
mount: according to mtab, /dev/sda5 is already mounted on /mnt
ubuntu@ubuntu:~$ apt-get install grub
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  grub-doc mdadm
The following packages will be REMOVED:
  grub-pc
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 407kB of archives.
After this operation, 807kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com karmic/main grub 0.97-29ubuntu59 [407kB]
Fetched 407kB in 0s (1,003kB/s)
Preconfiguring packages ...
(Reading database ... 120318 files and directories currently installed.)
Removing grub-pc ...
Processing triggers for man-db ...
Selecting previously deselected package grub.
(Reading database ... 120136 files and directories currently installed.)
Unpacking grub (from .../grub_0.97-29ubuntu59_i386.deb) ...
Processing triggers for man-db ...
Setting up grub (0.97-29ubuntu59) ...

root@ubuntu:~# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/memtest86+.bin
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

root@ubuntu:~# grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
root@ubuntu:~# grub
Probing devices to guess BIOS drives. This may take a long time.
root@ubuntu:~# 

```

Once in GRUB, I type find /boot/grub/stage1, and am told 'Error 15: File not found'.

I'm afraid I'm not sure how to run in the chroot environment, so, staying in sudo (which you can see I did earlier to try and install GRUB), I got the following:

```

root@ubuntu:~# cat /etc/apt/sources.list
deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb http://archive.ubuntu.com/ubuntu karmic main restricted
deb-src http://archive.ubuntu.com/ubuntu karmic main restricted

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu karmic-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu karmic-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu karmic universe
# deb-src http://archive.ubuntu.com/ubuntu karmic universe
# deb http://archive.ubuntu.com/ubuntu karmic-updates universe
# deb-src http://archive.ubuntu.com/ubuntu karmic-updates universe
# deb http://security.ubuntu.com/ubuntu karmic-security universe
# deb-src http://security.ubuntu.com/ubuntu karmic-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb http://archive.ubuntu.com/ubuntu karmic multiverse
# deb-src http://archive.ubuntu.com/ubuntu karmic multiverse
# deb http://archive.ubuntu.com/ubuntu karmic-updates multiverse
# deb-src http://archive.ubuntu.com/ubuntu karmic-updates multiverse
# deb http://security.ubuntu.com/ubuntu karmic-security multiverse
# deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse

root@ubuntu:~# 

```

Thanks a lot for giving so much help!

---

### Post by darkod on 2009-12-10
First of all lets see if the old grub2 is there enough to be restored. Booting with the cd go into terminal and execute:
sudo mount /dev/sda5 /mnt
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

That will reinstall grub2 on your hdd MBR and use the existing config files which are hopefully still there.
Take the cd out, reboot and see what happens if booting from the hdd.

---

### Post by kansasnoob on 2009-12-10
OK, let me explain some things. My chroot "script", such as it is, is only a string of commands tied together with "space&&space". If any one of the steps in that string returns an error the rest of the string will not complete.

The reason you got this error:

> mount: /dev/sda5 already mounted or /mnt busy
mount: according to mtab, /dev/sda5 is already mounted on /mnt


Would appear to be that you didn't unmount properly when you last exited the chroot. So you should have run the unmount script and then started over.

Also when you became root by "sudo -i" you were only root in the live desktop so the sources.list you posted was only the default list from the live CD. (BTW I never use sudo -i or sudo su in Ubuntu).

Anyway the purpose of mounting and becoming chroot in sda5 is that you will then be actually running the commands within your installed Karmic instead of just on the live desktop.

So back up, go to terminal and if the terminal prompt looks like this "root@ubuntu:/#" or this "root@ubuntu:~#" run:

```
exit
```

It should then look like this "ubuntu@ubuntu:~$" so run:

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

And please to help me help you copy-n-paste full output as you've been doing. Now we'll run the same commands as I said in post #12 with a few minor tweaks to help me:

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
lsb_release -a
```

```
df -H
```

```
cat /etc/apt/sources.list
```

```
apt-get install grub
```

```
update-grub
```

Say yes to creating a menu.lst!

```
grub-install /dev/sda
```

```
grub
```

That should drop you into a grub shell like this:

>       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> 


Then:

```
root (hd0,4)
```

```
setup (hd0)
```

```
quit
```

Then you must exit the chroot and remember to unmount:

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

After copy-n-pasting the results here (even if it didn't appear to fail) reboot.

If that succeeds, which it should, then we'll add Windows to your new menu.lst. It's easy!

---

### Post by kansasnoob on 2009-12-10
A few other thoughts:

(1) If you grow weary of this and just want to take a break and be able to run Windows while you take a breather simply boot the Ubuntu Live CD (no need to chroot anything) and run:

```
sudo apt-get install mbr
```

```
sudo install-mbr /dev/sda
```

That should allow you to boot only Windows. I've used it on both XP and Win 7 and it just worked. We can still work on straightening out Ubuntu then at your leisure.

(2) I am adding "lsb_release -a" to the list of commands above just because I wonder if this may have been a pre-release CD. If you ran the instructions before I added it don't sweat it, but I've actually booted my Karmic Live CD and "grub-pc" should be in the default repositories!

(3) Since this failed for no really good reason on initial installation I'm wondering if this might be a bad Live CD so the next time you reboot instead of choosing Try without changes ........ select Check CD for defects. It takes several minutes to run but we should know for sure.

---

### Post by johnmic on 2009-12-11
My computer seems absolutely determined to make life difficult:

```

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
root@ubuntu:/# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic
root@ubuntu:/# df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda5              257G   2.2G   241G   1% /
/dev/scd0              257G   2.2G   241G   1% /media/cdrom0
none                   257G   2.2G   241G   1% /sys
root@ubuntu:/# cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic universe
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
root@ubuntu:/# apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package grub has no installation candidate
root@ubuntu:/# update-grub
The program 'update-grub' can be found in the following packages:
 * grub
 * grub-pc
 * grub-coreboot
 * grub-efi-amd64
 * grub-efi-ia32
 * grub-ieee1275
Try: apt-get install <selected package>
update-grub: command not found

```

Re-running apt-get gives the same result.

---

### Post by johnmic on 2009-12-11
I've also checked the disc for defects - no problems there.

---

### Post by darkod on 2009-12-11
> **johnmic said:**
> I've also checked the disc for defects - no problems there.

Did you try my commands from post #15?
You should start with simple commands and then move to complicated if that doesn't work. I am not convinced you need to execute so many commands just to reinstall grub2. I might be wrong though. :)
Try the two commands in post #15 and report what happens.

---

### Post by johnmic on 2009-12-11
Sorry, darkod - I did actually try it, just forgot to mention the results! However, another use of your commands gave the same effect as before, so you can see what's going on:

```

 ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda       

```

After that, I reboot, but the GRUB doesn't load correctly - I go straight to the grub command line thing.

---

### Post by kansasnoob on 2009-12-11
That last attempt and the info provided are actually very helpful! Your sources.list looks fine, and "df -H" tells me that you were for sure in sda5. Although in your original post you said:

> I partitioned the drive so Windows XP Professional was installed on the first 120GB of the drive - this works no problem. I then instructed Ubuntu to install on the same partition, resizing Windows to 50GB, Ubuntu taking up the rest of the 120GB.

df -H says:

```
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda5              257G   2.2G   241G   1% /
```

So the Ubuntu partition is actually 257GB, so it would be interesting to see the output of:

```
sudo parted /dev/sda print
```

From the Live CD just to see the actual size of Windows, but I don't think that should be a huge problem. I could be wrong however, you seem to know much more about your BIOS and hardware than I do.

What does have me somewhat puzzled is why the package list says neither grub or grub-pc is available, but we're going to mount and chroot sda5 again and update the package list. To do so requires a couple of additional commands, the reason is explained in the release notes:

[http://www.ubuntu.com/getubuntu/releasenotes/910#Upstart%20jobs%20cannot%20be%20run%20in%20a%20chroot](http://www.ubuntu.com/getubuntu/releasenotes/910#Upstart%20jobs%20cannot%20be%20run%20in%20a%20chroot)

So hang on for just a bit while I rewrite a new set of commands. Sorry you've had so much trouble.

In retrospect I wish I'd just had you run the Boot Info Script to begin with, but I can't turn the clock back so please continue to be patient.

I'll type up the new list of commands right now.

---

### Post by kansasnoob on 2009-12-11
I'm not going to rehash a lot of my previous explanations to try and keep this short and sweet.

Now just like before make sure you've exited the chroot and unmounted sda5:

If the terminal prompt looks like this "root@ubuntu:/#" or this "root@ubuntu:~#" run:

```
exit
```

It should then look like this "ubuntu@ubuntu:~$" so run:

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

**Please see the notes at the very end of this about what to do if any part of the mount/chroot/unmount script ever fails!**

Now we'll remount and chroot:

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
df -H
```

```
parted /dev/sda print
```

This is where we want to add the commands explained in the release notes:

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

Now we'll update the package list:

```
apt-get update
```

That may take a few minutes to complete. If it produces any errors I need to know but regardless try:

```
apt-get install grub
```

If it fails we'll have to go back to the drawing board. (Maybe I'll need to read a bit about maximum partition size - 257GB is unusually large).

If it appears to succeed then continue:

```
update-grub
```

Say yes to creating a /boot/grub/menu.lst.

```
grub-install /dev/sda
```

```
grub
```

Something I hadn't thought to mention before: I've noticed while working in a grub shell that the enter key in the numerical block of the keyboard doesn't always work properly, so use the enter key just above the right shift key!

```
root (hd0,4)
```

```
setup (hd0)
```

```
quit
```

Adding this now to save you a reboot later:

```
apt-get install startupmanager
```

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Then reboot if all was successful.

I'm going to go ahead and add the part about adding Windows to your menu.lst since there's an hours long lag between us. This of course only applies if you're able to boot into Ubuntu.

 First copy the menu.lst:

```
cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

Then we'll edit using gedit, just be careful not to delete anything! Run:

```
gksudo gedit /boot/grub/menu.lst
```

Then at the very bottom of the menu.lst you should see this:

> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

Just below that copy-n-paste this:

```
title		Microsoft Windows XP Pro
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
```

Then click on Save, then File > Quit.

Then you need to make grub visible at boot so go to System > Administration > Startup Manager:

[http://www.psychocats.net/ubuntu/images/sum09.png](http://www.psychocats.net/ubuntu/images/sum09.png)

Be sure that the timeout is set to something appropriate, by default it'll be 3 seconds, I recommend at least 10 seconds. Also in the lower left hand corner be certain that Show bootloader menu is checked.

I sure hope this works! I'll go ahead and do some research on maximum size of partitions but that certainly had nothing to do with the ability to install the grub or grub-pc packages.

NOTE: If any part of that chroot script ever spits errors remember what I said about being just a bunch of commands strung togeter with "space&&space" so if either the mount or unmount spits errors try running the commands separately (not using code tags to save space):

MOUNT:
sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev/pts /mnt/dev/pts
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt

REMEMBER: exit

UNMOUNT:
sudo umount /mnt/dev/pts
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

---

### Post by kansasnoob on 2009-12-11
I sure hope you didn't just give up!

I should have thought to ask for more info and more importantly I should have thought to have you update the package list.

---

### Post by johnmic on 2009-12-12
Sorry I didn't get back to you sooner - I'm writing this reply from within my very own working Ubuntu installation! Thanks very much for all your help - it was really appreciated, and without it I wouldn't have got this working.

As a final piece of advice - can you recommend any way of learning the ins and outs of Ubuntu, so that some day in the future, I might be able to help someone else as much as you helped me?

---

### Post by kansasnoob on 2009-12-13
Without a doubt this was the greatest single help to me:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

Lots and lots of stuff:

Post install:

[http://members.iinet.net.au/~herman546/p5.html](http://members.iinet.net.au/~herman546/p5.html)

Command line:

[http://members.iinet.net.au/~herman546/p8.html](http://members.iinet.net.au/~herman546/p8.html)

Some simple tasks here:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

And of course these forums are great.

Also I'm a bit of a distro-hopper and if I'm going to try a new distro I always google "the perfect desktop ubuntu karmic" (of course replace ubuntu with whatever distro you're curious about, but for instance:

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.10-karmic-koala](http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.10-karmic-koala)

HowtoForge does great with those!

---

