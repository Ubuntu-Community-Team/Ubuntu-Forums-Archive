---
title: "grub-pc broken - dependency problems - kernel wont upgrade"
date: 2014-11-12
forum: Installation &amp; Upgrades
---

### Post by relativ on 2014-11-12
Hello,

This is the first time I'm stuck on an issue since installing 8.04, so's I need a little help.

Below is the output of "sudo apt-get -f install"


```
Setting up linux-image-3.2.0-61-generic (3.2.0-61.92) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-61-generic /boot/vmlinuz-3.2.0-61-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-61-generic /boot/vmlinuz-3.2.0-61-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-61-generic /boot/vmlinuz-3.2.0-61-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-61-generic
Warning: No support for locale: en_US.utf8
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-61-generic /boot/vmlinuz-3.2.0-61-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-61-generic /boot/vmlinuz-3.2.0-61-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-61-generic /boot/vmlinuz-3.2.0-61-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-61-generic...
P: Writing config for /boot/vmlinuz-3.2.0-23-generic...
P: Writing config for Mint on /dev/sda1...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-61-generic /boot/vmlinuz-3.2.0-61-generic
/usr/sbin/grub-mkconfig: 36: /etc/default/grub: menuentry: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-61-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-61-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of grub-pc:
 grub-pc depends on grub2-common (= 1.99-21ubuntu3.9); however:
  Version of grub2-common on system is 1.99-21ubuntu3.17.
 grub-pc depends on grub-pc-bin (= 1.99-21ubuntu3.9); however:
  Version of grub-pc-bin on system is 1.99-21ubuntu3.17.
dpkg: error processing grub-pc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-61-generic; however:
  Package linux-image-3.2.0-61-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.61.72); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already

Errors were encountered while processing:
 linux-image-3.2.0-61-generic
 grub-pc
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-3.2.0-61-generic (3.2.0-61.92) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-61-generic /boot/vmlinuz-3.2.0-61-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-61-generic /boot/vmlinuz-3.2.0-61-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-61-generic /boot/vmlinuz-3.2.0-61-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-61-generic
Warning: No support for locale: en_US.utf8
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-61-generic /boot/vmlinuz-3.2.0-61-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-61-generic /boot/vmlinuz-3.2.0-61-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-61-generic /boot/vmlinuz-3.2.0-61-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-61-generic...
P: Writing config for /boot/vmlinuz-3.2.0-23-generic...
P: Writing config for Mint on /dev/sda1...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-61-generic /boot/vmlinuz-3.2.0-61-generic
/usr/sbin/grub-mkconfig: 36: /etc/default/grub: menuentry: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-61-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-61-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-61-generic; however:
  Package linux-image-3.2.0-61-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-pc:
 grub-pc depends on grub2-common (= 1.99-21ubuntu3.9); however:
  Version of grub2-common on system is 1.99-21ubuntu3.17.
 grub-pc depends on grub-pc-bin (= 1.99-21ubuntu3.9); however:
  Version of grub-pc-bin on system is 1.99-21ubuntu3.17.
dpkg: error processing grub-pc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.61.72); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.2.0-61-generic
 linux-image-generic
 grub-pc
 linux-generic
```



further, trying to update grub-pc in synaptic results with...

```
E: linux-image-3.2.0-61-generic: subprocess installed post-installation script returned error exit status 2
E: grub-pc: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
```


I have read alot on this and have found so many potential fixes... I just don't know what to try first and I really don't want to bork this box.

any ideas???

D.

---

### Post by relativ on 2014-11-14
I'm still confused about this... Does anyone even have a hint for me? I would be very grateful,

---

### Post by oldfred on 2014-11-14
Did you upgrade from 8.04 to 12.04? As kernel 3.2 is from 12.04?

Are you able to boot into system? If not you may need to chroot into it.
But you probably should totally purge grub & reinstall it. But make sure Internet is working as it has to download the new grub2.

Boot-Repair's advanced mode will walk you thru the process. 
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

      
 drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

---

### Post by ian-weisser on 2014-11-14
[EDIT]: Oldfred beat me to it. Said it better, too.

---

### Post by relativ on 2014-11-14
No, this was not an upgrade from 8.04.... I just meant that I've been using ubuntu in one form or another since 8.04, but this is the first time I've had a problem I couldn't fugue out myself.

I can boot into the system no problem, I just can't get the new kernel configured because of the aforementioned errors. Since I can boot the pc, which method would be best? Boot-repair?

Thanks for your replies.
D

---

### Post by Bashing-om on 2014-11-14
relativ; Hi !

It will be of interest to see what returns from terminal commands:
```

sudo apt-get install linux-generic linux-headers-generic linux-image-generic

```
maybe the generic approach will apply in the specific ?
At the least, get some additional info.

[INDENT][INDENT]where there are solutions there are no problems
[/INDENT][/INDENT]

---

### Post by relativ on 2014-11-14
the command "sudo apt-get install linux-generic linux-headers-generic linux-image-generic" returns....


Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 grub-pc : Depends: grub2-common (= 1.99-21ubuntu3.9) but 1.99-21ubuntu3.17 is to be installed
           Depends: grub-pc-bin (= 1.99-21ubuntu3.9) but 1.99-21ubuntu3.17 is to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-70-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.2.0-70-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by relativ on 2014-11-14
oldfred,

I added the ppa for boot-repair and upon attempting to install it, I get...


sudo apt-get install -y boot-repair && (boot-repair &)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 boot-repair : Depends: boot-sav but it is not going to be installed
               Recommends: pastebinit but it is not going to be installed
 grub-pc : Depends: grub2-common (= 1.99-21ubuntu3.9) but 1.99-21ubuntu3.17 is to be installed
           Depends: grub-pc-bin (= 1.99-21ubuntu3.9) but 1.99-21ubuntu3.17 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by Bashing-om on 2014-11-14
relativ; Humm ??

I will have to do some checking and homework. From my NOT-updated 12.04 install:
```

vmlinuz-3.2.0-61-generic

```
Is the latest kernel version I have installed. I will later reboot into it and update it and see what is the latest version that 'should' be available in the repository. ( I would prefer to do it bare metal as opposed to a change root means).

Then will see what can be done to resolve the dependency issue.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by relativ on 2014-11-14
@bashing-om.... wow! Thanks.

---

### Post by Bashing-om on 2014-11-14
relativ; Welp;

I did, and I am a little the wiser.
It must have been some time since I booted 12.04, a lot of updates behind, and I can now confirm that :
The latest kernel is indeed 3.2.0-70
And grub is at version 1.99-21ubuntu 3.17

So the question is; why you are not booting the latest kernel ?
And what kernel are you booting ?

@ Ian , which comes first here, the chicken or the egg ? Are we looking at grub holding the kernel back or the kernel version holding grub back ?

Relativ: Show us now what we are working with:
```

uname -r
apt-cache policy grub-pc
ls -al /vmlinuz*
la -a /initrd.img*
ls -al /boot 
df -h
df -i

```

As we look to find
[INDENT][INDENT][INDENT]the reason why
[/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2014-11-14
I would like to do the full uninstall and reinstall of grub2 as that should get it & all its dependencies in sync. But my concern is that if the conflict is not grub and then the reinstall of grub does not work, then there will be no way to boot. 
At very least have good working live installer to run repairs, know how to chroot and/or run Boot-Repair.

       # uninstall both grub legacy & grub2 reinstall grub2 and to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common
sudo grub-install /dev/sda
sudo grub-install --recheck /dev/sda
sudo apt-get update 
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a

Have you checked that there are no version differences in sources to make sure that is not an issue?
cat -n /etc/apt/sources.list
ls -l /etc/apt/sources.list.d/

---

### Post by relativ on 2014-11-15
ok... results of those commands below:


```
uname -r
3.2.0-23-generic


apt-cache policy grub-pc
grub-pc:
  Installed: 1.99-21ubuntu3.9
  Candidate: 1.99-21ubuntu3.17
  Version table:
     1.99-21ubuntu3.17 0
        500 http://archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
 *** 1.99-21ubuntu3.9 0
        100 /var/lib/dpkg/status
     1.99-21ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main i386 Packages


ls -al /vmlinuz*
lrwxrwxrwx 1 root root 29 Nov 14 19:02 /vmlinuz -> boot/vmlinuz-3.2.0-61-generic
lrwxrwxrwx 1 root root 29 Nov 12 20:33 /vmlinuz.old -> boot/vmlinuz-3.2.0-61-generic


ls -a /initrd.img*
/initrd.img  /initrd.img.old


ls -al /boot
total 55418
drwxr-xr-x  5 root root     1024 Nov 14 19:03 .
drwxr-xr-x 22 root root     4096 Nov 14 19:02 ..
-rw-r--r--  1 root root   795572 Apr 10  2012 abi-3.2.0-23-generic
-rw-r--r--  1 root root   800253 Mar 31  2014 abi-3.2.0-61-generic
-rw-r--r--  1 root root   147316 Apr 10  2012 config-3.2.0-23-generic
-rw-r--r--  1 root root   147621 Mar 31  2014 config-3.2.0-61-generic
drwxr-xr-x  3 root root     1024 Nov 14 19:03 extlinux
drwxr-xr-x  3 root root     8192 Nov 27  2012 grub
-rw-r--r--  1 root root 20065302 Apr 29  2014 initrd.img-3.2.0-23-generic
-rw-r--r--  1 root root 20149256 Nov 14 19:03 initrd.img-3.2.0-61-generic
drwx------  2 root root    12288 Jun 21  2012 lost+found
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  2252691 Apr 10  2012 System.map-3.2.0-23-generic
-rw-------  1 root root  2259642 Mar 31  2014 System.map-3.2.0-61-generic
-rw-r--r--  1 root root  4864480 May 20  2012 vmlinuz-3.2.0-23-generic
-rw-------  1 root root  4878016 Mar 31  2014 vmlinuz-3.2.0-61-generic


df -h
Filesystem        Size  Used Avail Use% Mounted on
/dev/sda5          80G   71G  4.8G  94% /
udev              487M  4.0K  487M   1% /dev
tmpfs             199M  992K  198M   1% /run
none              5.0M     0  5.0M   0% /run/lock
none              497M   80K  497M   1% /run/shm
/dev/sda2         474M   82M  369M  19% /boot
/home/r/.Private   80G   71G  4.8G  94% /home/r
/dev/sda4         2.9G  1.4G  1.4G  51% /media/extra
/dev/sda1         147G  140G  7.1G  96% /media/C2B4948BB4948397


df -i
Filesystem        Inodes  IUsed   IFree IUse% Mounted on
/dev/sda5        5193728 352770 4840958    7% /
udev              124504    537  123967    1% /dev
tmpfs             127043    476  126567    1% /run
none              127043      3  127040    1% /run/lock
none              127043      5  127038    1% /run/shm
/dev/sda2         122400    269  122131    1% /boot
/home/r/.Private 5193728 352770 4840958    7% /home/r
/dev/sda4         184368     13  184355    1% /media/extra
/dev/sda1        7712412 274384 7438028    4% /media/C2B4948BB4948397
```

---

### Post by relativ on 2014-11-15
"But my concern is that if the conflict is not grub and then the reinstall of grub does not work, then there will be no way to boot. "

Oldfred, that is my concern, too.

This pc has a very non-standard boot setup. I first had windows installed, then ubuntu 10.04 went on after I resized the NTFS partition to make room for a linux install... then I did a fresh install of 12.04 and I set up the dual boot (differently the second time) so I could still boot into windows (when work required it, which, happily, is no longer the case).... but when I set up the dual boot, I did it by hand and couldn't tell you how I did it if my life depended on it (I remember something about copying the linux.bin file over).. so I really don't want to mess it up and have to start over, but if that's the case I'll go ahead and do it... wipe the drive and put 14.04 on there. Just too busy to sit down and do it now.

---

### Post by oldfred on 2014-11-15
Best to run Boot-Repair's summary report just to know what is where.
There is not a trusty version. The instructions have you rename to saucy to download current version.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Someone copied the saucy version into trusty ppa. So that works automatically. But I lost link.

Did not save different link as it was added to above link. kranich/cubuntu
It still is the saucy version which works with the newer ones.

---

### Post by relativ on 2014-11-15
update: I was able to install boot-repair via synaptic... let it do its thing - replaced grub, etc... pc boots ok, but errors are still persistant.

---

### Post by oldfred on 2014-11-15
There is the simple reinstall of grub to the MBR which may fix some issues, but it has in advanced mode the total uninstall and reinstall of grub. 

If it works it should then have consistent versions across the board and no issues from grub.

---

