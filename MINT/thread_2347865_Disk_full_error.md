---
title: "Disk full error"
date: 2016-12-17
forum: MINT
---

### Post by ccheath2 on 2016-12-17
*Posts from [https://ubuntuforums.org/showthread.php?t=2317494](https://ubuntuforums.org/showthread.php?t=2317494) split off into their own thread*

************

tl;dr: in my case (or anyone else who's encountering this bug) is resizing the partition a recommended solution?  
(also, why do people put tl;dr summaries at the bottom after people have already read what theyre summarizing?)

----

so i've encountered this bug: [Kernels not autoremoving, causing out of space error on LVM or Encrypted installation or on any installation, when /boot partition gets full]("https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1357093") 

it's been a couple weeks or so since the 4.4.0-53 was offered to my linux mint 
the kernel installed but the extras package for 4.4.0-53 didn't 
also the linux-firmware and initramfs-tools packages failed

i noticed the lack of disk space mentioned in the error log  
after quickly checking my drive for free space and having 90% free
i ignored the error and warnings  
because
the system was working without any issues (that I can tell)
and
 i don't really do much besides stream netflix on this laptop
it's an older pentium inside late vista era machine with no battery 
it's hidden in the media center cabinet and basically always on 
i use nomachine on my old ipad2 to control it ususally 
(tangent: nomachine has saved my old ipad2... i almost got rid of it!)
back to this bug 
i have the update manager set to level5 so there's almost always updates to install whenever i check 
so now we're at the point where not only is the error and annoyance
but also it intrigues/challenges me subconsciously to figure this out 
or at the very least make it go away since it's annoying 
(and at that 'failure to fix with a scalpel' point i would have been too invested to just succumb to the annoyance and employ the 'fix with drastic measures')
so
after finally having some time to spend on this i end up on this thread
i began to follow along in bonzo2's footsteps blindly but nothings working (for either of us)
but then....
Bashing-om's commands started having success for bonzo2
but not for me 
[INDENT]**[FONT=courier new]sudo dpkg -P linux-signed-image-4.4.0-21-generic[/FONT]**[/INDENT]
returned[INDENT]**[FONT=courier new]dpkg: warning: ignoring request to remove linux-signed-image-4.4.0-21-generic which isn't installed[/FONT]**[/INDENT]

so i began to just read along and see what happened
 (since it's obviously a solved thread) 
and see if i could figure out a way replicate this success for myself
and then just at the end after all is well bonzo2 asks what I asked myself the second that I realized that it was the /boot partition causing this problem

> **bonzo2 said:**
> 
 Would it be better or even possible for me to just expand my partition? 


> **Bashing-om said:**
> 
As to expanding /boot ... oh boy ... that "can" be a can of worms. I strongly advocate leave well enough alone. The only time that /boot filling up is with new kernel installs ... it is no big deal at all to do terminal command
```

sudo apt-get autoremove

```


so what's the 'can of worms' that expanding /boot just once to allow the updates to complete?
then doing an autoremove and just remembering not to let it get to this point again?

i've got half a mind to just do it and report back what happens before your reply but my rsi/carpel tunnel is kicking in and i need to get out of the house anyway... 

cheers and tyia
chris

---

### Post by Bashing-om on 2016-12-17
ccheath2; Hey !

That "can of worms": let's say that you want to expand the partition that contains /boot to the left, and that the boot code is at the start of the partition - not to discount the partition table also in residence at the start of the partition.. now moving data is problematic in and of it's self .. and there is a hitch moving the boot data . OK .. NOT ; as now you can not boot the system, and one may or may not be able to repair the damage . That is a bad case scenerio, but it does happen ! If it works do not mess with it !

In your case we do not know that the /boot partition is an issue .
Let's back up to square one and see what is:
```

df -h
df -i
dpkg -l | grep linux-
ls -al /boot

```
then logically progress to find the solution .

[INDENT][INDENT]I like a good plan
[/INDENT][/INDENT]

---

### Post by ccheath2 on 2016-12-18
oh im at 100% on my /boot that's def the problem 
definitely won't let the installer do that next time
i'll post the results of those commands later when i get home
thanks for the reply

---

### Post by ccheath2 on 2016-12-29
sorry for the delay 
i just haven't been motivated to attack this in my free time
but i did mention it to someone and they sent me this link
[http://askubuntu.com/questions/2793/how-do-i-remove-old-kernel-versions-to-clean-up-the-boot-menu](http://askubuntu.com/questions/2793/how-do-i-remove-old-kernel-versions-to-clean-up-the-boot-menu)
should i try one/some of these top solutions?
or are we past that point?

---

### Post by ccheath2 on 2016-12-29
the bug in question 
[https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1357093)
for clarification since i got my own thread now

---

### Post by vasa1 on 2016-12-29
By the way, if you want a different title for the thread, you can go to the first post, click *edit* and then click *Go advanced* and change the title there. Otherwise, post a more suitable title and one of the staff will change it for you!

---

### Post by ccheath2 on 2016-12-29
> **Bashing-om said:**
> Let's back up to square one and see what is:
```

df -h
df -i
dpkg -l | grep linux-
ls -al /boot

```

TYIA
```
cch@mint-av ~ $ df -h Filesystem                 Size  Used Avail Use% Mounted on
udev                       1.5G     0  1.5G   0% /dev
tmpfs                      298M  9.1M  289M   4% /run
/dev/mapper/mint--vg-root  144G   19G  118G  14% /
tmpfs                      1.5G   14M  1.5G   1% /dev/shm
tmpfs                      5.0M  4.0K  5.0M   1% /run/lock
tmpfs                      1.5G     0  1.5G   0% /sys/fs/cgroup
/dev/sda1                  472M  472M     0 100% /boot
cgmfs                      100K     0  100K   0% /run/cgmanager/fs
tmpfs                      298M   12K  298M   1% /run/user/1002
tmpfs                      298M   32K  298M   1% /run/user/1000


cch@mint-av ~ $ df -i 
Filesystem                 Inodes  IUsed   IFree IUse% Mounted on
udev                       374949    609  374340    1% /dev
tmpfs                      380300    879  379421    1% /run
/dev/mapper/mint--vg-root 9543680 667195 8876485    7% /
tmpfs                      380300     44  380256    1% /dev/shm
tmpfs                      380300      5  380295    1% /run/lock
tmpfs                      380300     18  380282    1% /sys/fs/cgroup
/dev/sda1                  124928    346  124582    1% /boot
cgmfs                      380300     14  380286    1% /run/cgmanager/fs
tmpfs                      380300     12  380288    1% /run/user/1002
tmpfs                      380300     22  380278    1% /run/user/1000


cch@mint-av ~ $ dpkg -l | grep linux-
ii  linux-base                                   4.0ubuntu1                                 all          Linux image base package
iF  linux-firmware                               1.157.6                                    all          Firmware for Linux kernel drivers
ii  linux-headers-4.4.0-21                       4.4.0-21.37                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-21-generic               4.4.0-21.37                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-36                       4.4.0-36.55                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-36-generic               4.4.0-36.55                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-38                       4.4.0-38.57                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-38-generic               4.4.0-38.57                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-42                       4.4.0-42.62                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-42-generic               4.4.0-42.62                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-43                       4.4.0-43.63                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-43-generic               4.4.0-43.63                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-45                       4.4.0-45.66                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-45-generic               4.4.0-45.66                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-47                       4.4.0-47.68                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-47-generic               4.4.0-47.68                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-51                       4.4.0-51.72                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-51-generic               4.4.0-51.72                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-53                       4.4.0-53.74                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-53-generic               4.4.0-53.74                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-57                       4.4.0-57.78                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-57-generic               4.4.0-57.78                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ri  linux-image-4.4.0-21-generic                 4.4.0-21.37                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-36-generic                 4.4.0-36.55                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-38-generic                 4.4.0-38.57                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-42-generic                 4.4.0-42.62                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-43-generic                 4.4.0-43.63                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-45-generic                 4.4.0-45.66                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-47-generic                 4.4.0-47.68                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-51-generic                 4.4.0-51.72                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-53-generic                 4.4.0-53.74                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-57-generic                 4.4.0-57.78                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ri  linux-image-extra-4.4.0-21-generic           4.4.0-21.37                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-36-generic           4.4.0-36.55                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-38-generic           4.4.0-38.57                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-42-generic           4.4.0-42.62                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-43-generic           4.4.0-43.63                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-45-generic           4.4.0-45.66                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-47-generic           4.4.0-47.68                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-51-generic           4.4.0-51.72                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-extra-4.4.0-53-generic           4.4.0-53.74                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-57-generic           4.4.0-57.78                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-kernel-generic                         4.4.0-21                                   all          The Linux kernel.
ii  linux-libc-dev:amd64                         4.4.0-57.78                                amd64        Linux Kernel Headers for development
ii  linux-sound-base                             1.0.25+dfsg-0ubuntu5                       all          base package for ALSA and OSS sound systems
ii  syslinux-common                              3:6.03+dfsg-11ubuntu1                      all          collection of bootloaders (common)
ii  syslinux-legacy                              2:3.63+dfsg-2ubuntu8                       amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  syslinux-utils                               3:6.03+dfsg-11ubuntu1                      amd64        collection of bootloaders (utilities)


cch@mint-av ~ $ ls -al /boot
total 473280
drwxr-xr-x  4 root root     4096 Dec 29 11:47 .
drwxr-xr-x 23 root root     4096 Dec 29 11:46 ..
-rw-r--r--  1 root root  1239577 Apr 18  2016 abi-4.4.0-21-generic
-rw-r--r--  1 root root  1241960 Aug 11 15:58 abi-4.4.0-36-generic
-rw-r--r--  1 root root  1242262 Sep  6 14:52 abi-4.4.0-38-generic
-rw-r--r--  1 root root  1242701 Oct  7 22:15 abi-4.4.0-42-generic
-rw-r--r--  1 root root  1242701 Oct 12 11:47 abi-4.4.0-43-generic
-rw-r--r--  1 root root  1242701 Oct 19 12:34 abi-4.4.0-45-generic
-rw-r--r--  1 root root  1243086 Oct 26 18:27 abi-4.4.0-47-generic
-rw-r--r--  1 root root  1243479 Nov 24 16:12 abi-4.4.0-51-generic
-rw-r--r--  1 root root  1243479 Dec  2 14:11 abi-4.4.0-53-generic
-rw-r--r--  1 root root  1243800 Dec  9 23:04 abi-4.4.0-57-generic
-rw-r--r--  1 root root   189412 Apr 18  2016 config-4.4.0-21-generic
-rw-r--r--  1 root root   189696 Aug 11 15:58 config-4.4.0-36-generic
-rw-r--r--  1 root root   189732 Sep  6 14:52 config-4.4.0-38-generic
-rw-r--r--  1 root root   189760 Oct  7 22:15 config-4.4.0-42-generic
-rw-r--r--  1 root root   189760 Oct 12 11:47 config-4.4.0-43-generic
-rw-r--r--  1 root root   189760 Oct 19 12:34 config-4.4.0-45-generic
-rw-r--r--  1 root root   189809 Oct 26 18:27 config-4.4.0-47-generic
-rw-r--r--  1 root root   189877 Nov 24 16:12 config-4.4.0-51-generic
-rw-r--r--  1 root root   189877 Dec  2 14:11 config-4.4.0-53-generic
-rw-r--r--  1 root root   189991 Dec  9 23:04 config-4.4.0-57-generic
drwxr-xr-x  5 root root     1024 Dec  8 04:15 grub
-rw-r--r--  1 root root 38516411 Aug 31 22:27 initrd.img-4.4.0-21-generic
-rw-r--r--  1 root root 38549345 Sep 15 02:53 initrd.img-4.4.0-36-generic
-rw-r--r--  1 root root 39819772 Oct  6 10:49 initrd.img-4.4.0-38-generic
-rw-r--r--  1 root root 40224595 Oct 12 23:30 initrd.img-4.4.0-42-generic
-rw-r--r--  1 root root 40224819 Oct 17 18:47 initrd.img-4.4.0-43-generic
-rw-r--r--  1 root root 40225227 Nov  3 16:58 initrd.img-4.4.0-45-generic
-rw-r--r--  1 root root 40325134 Nov 19 20:41 initrd.img-4.4.0-47-generic
-rw-r--r--  1 root root 40331187 Nov 30 10:41 initrd.img-4.4.0-51-generic
-rw-r--r--  1 root root 40329780 Dec  8 04:15 initrd.img-4.4.0-53-generic
drwx------  2 root root    12288 Aug 31 19:25 lost+found
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  3853719 Apr 18  2016 System.map-4.4.0-21-generic
-rw-------  1 root root  3867829 Aug 11 15:58 System.map-4.4.0-36-generic
-rw-------  1 root root  3869329 Sep  6 14:52 System.map-4.4.0-38-generic
-rw-------  1 root root  3869895 Oct  7 22:15 System.map-4.4.0-42-generic
-rw-------  1 root root  3869895 Oct 12 11:47 System.map-4.4.0-43-generic
-rw-------  1 root root  3869895 Oct 19 12:34 System.map-4.4.0-45-generic
-rw-------  1 root root  3873447 Oct 26 18:27 System.map-4.4.0-47-generic
-rw-------  1 root root  3874377 Nov 24 16:12 System.map-4.4.0-51-generic
-rw-------  1 root root  3874377 Dec  2 14:11 System.map-4.4.0-53-generic
-rw-------  1 root root  3875329 Dec  9 23:04 System.map-4.4.0-57-generic
-rw-r--r--  1 root root  7013968 Jul 28 07:30 vmlinuz-4.4.0-21-generic
-rw-------  1 root root  7045472 Aug 11 15:58 vmlinuz-4.4.0-36-generic
-rw-------  1 root root  7051680 Sep  6 14:52 vmlinuz-4.4.0-38-generic
-rw-------  1 root root  7053472 Oct  7 22:15 vmlinuz-4.4.0-42-generic
-rw-------  1 root root  7053568 Oct 12 11:47 vmlinuz-4.4.0-43-generic
-rw-------  1 root root  7054208 Oct 19 12:34 vmlinuz-4.4.0-45-generic
-rw-------  1 root root  7060896 Oct 26 18:27 vmlinuz-4.4.0-47-generic
-rw-------  1 root root  7064208 Nov 24 16:12 vmlinuz-4.4.0-51-generic
-rw-------  1 root root  7065648 Dec  2 14:11 vmlinuz-4.4.0-53-generic
-rw-------  1 root root  7067152 Dec  9 23:04 vmlinuz-4.4.0-57-generic
```

---

### Post by deadflowr on 2016-12-29
> **ccheath2 said:**
> sorry for the delay 
i just haven't been motivated to attack this in my free time
but i did mention it to someone and they sent me this link
[http://askubuntu.com/questions/2793/how-do-i-remove-old-kernel-versions-to-clean-up-the-boot-menu](http://askubuntu.com/questions/2793/how-do-i-remove-old-kernel-versions-to-clean-up-the-boot-menu)
should i try one/some of these top solutions?
or are we past that point?

I'd recommend trying to remove just one, single, linux-image package. To start.
Use 
```
uname -r
```
to see what the current, in use, kernel is; so you do not remove that one.

Then try running the remove command for another linux-image package, perhaps try it against the oldest kernel in that list you have
(The oldest I see is linux-image-4.4.0-21-generic, so try that one, as long as it is not the current kernel, of course)
Like so,
```
sudo apt-get purge linux-image-4.4.0-21-generic 
```
see if that frees up a little space.
Then if it does, maybe try a second one, to help open up a little more space.
If it does not work, post the output so we can see what happened.

If it does free up some space then see if the autoremove command will list any of the others for remove and run it.
```
sudo apt-get autoremove
```

Then run
```
sudo apt-get update
```
you might need to run
```
sudo apt-get install -f
```
since the latest kernel is already on the system, but is half-configured, so the install -f command might help fix that issue.
or if that doesn't do anything, run the upgrade command
```
sudo apt-get dist-upgrade
```
to get the latest kernel fully installed

Hope it helps.
Or makes sense.

---

### Post by ccheath2 on 2016-12-29
thanks for the reply ... i'll try and post results in a hour or so

---

### Post by ccheath2 on 2016-12-30
thanks deadflowr

```


[COLOR=#008000]cch@mint-av[/COLOR] [COLOR=#008080]~ $[/COLOR] uname -r
4.4.0-53-generic

[COLOR=#008000]cch@mint-av[/COLOR] [COLOR=#008080]~ $[/COLOR]  sudo apt-get purge linux-image-4.4.0-21-generic
[sudo] password for cch: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-4.4.0-21-generic* linux-image-extra-4.4.0-21-generic* linux-kernel-generic*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 217 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 496089 files and directories currently installed.)
Removing linux-kernel-generic (4.4.0-21) ...
Removing linux-image-extra-4.4.0-21-generic (4.4.0-21.37) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-21-generic
Warning: No support for locale: en_US.utf8

[COLOR=#ff8c00]
**gzip: stdout: No space left on device**[/COLOR]
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-21-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-21-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-21-generic (4.4.0-21.37) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
dkms: removing: bcmwl 6.30.223.248+bdcom (4.4.0-21-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.30.223.248+bdcom
Kernel:  4.4.0-21-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-21-generic/updates/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.
dkms: removing: ndiswrapper 1.59 (4.4.0-21-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  ndiswrapper
Version: 1.59
Kernel:  4.4.0-21-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


ndiswrapper.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-21-generic/updates/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.
dkms: removing: virtualbox-guest 5.0.24 (4.4.0-21-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  virtualbox-guest
Version: 5.0.24
Kernel:  4.4.0-21-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


vboxguest.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-21-generic/updates/
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/4.4.0-21-generic/updates/


vboxsf.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-21-generic/updates/
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/4.4.0-21-generic/updates/


vboxvideo.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-21-generic/updates/
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/4.4.0-21-generic/updates/
depmod....


Removing original_module from DKMS tree for kernel 4.4.0-21-generic (x86_64)


DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-21-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found initrd image: /boot/initrd.img-4.4.0-36-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-4.4.0-21-generic (4.4.0-21.37) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
Errors were encountered while processing:
 linux-image-extra-4.4.0-21-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

_postscript & tangents:_
note the orange bold on the line that i googled that got me to [bonzo2's thread]("https://ubuntuforums.org/showthread.php?t=2317494") (that this thread was split from)

"*gzip: stdout: No space left on device site:ubuntuforums.org*"
site: is the first google-fu i teach my friends 
(and google even does' the 'more results from' link often)

question: why the use of code tags for copy/paste of commandline outputs...  or would having another tag be redundant?
i used to always use quote tags ... is it so the long pastes get scroll boxes and don't make the overall page extra long? 
(they're often already really long - and you can set the # of posts per page in preferences right?)

and btw, how can a kick (that's not even a kick) be a location?

/digression

---

### Post by Bashing-om on 2016-12-30
ccheath2; Hey;

Looks to me that you are making progress on one front and loosing on others.
Let's keep the focus to the main issue here " gzip: stdout: No space left on device  " which is the reason for the thread.

Now that ONE kernel is removed ( and -57 attempted to install) .. what now is the disk space status ?
show a new:
```

df -h
dpkg -l | grep linux

```
see if we keep on keep'n on or if at this point we can have the package manager manage this for you .

Always read for comprehension what the package manager is telling you .
Here we have that you are told there is a problem
> 
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]

and we do need to make sure that now you can boot the system.
show now the outputs:
```

ls -al /vmlinuz*
ls -al /initrd.img*
ls -al /boot

```

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]could be otherwise
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ccheath on 2016-12-31
on it asap 
i did notice that bit about the damaged link and grub
(almost mentioned it too)

standby
but don't hold your breath

---

### Post by ccheath on 2017-01-07
```
cch@mint-av ~ $ df -h
Filesystem                 Size  Used Avail Use% Mounted on
udev                       1.5G     0  1.5G   0% /dev
tmpfs                      298M   32M  266M  11% /run
/dev/mapper/mint--vg-root  144G   20G  117G  15% /
tmpfs                      1.5G  8.6M  1.5G   1% /dev/shm
tmpfs                      5.0M  4.0K  5.0M   1% /run/lock
tmpfs                      1.5G     0  1.5G   0% /sys/fs/cgroup
/dev/sda1                  472M  434M   14M  97% /boot
cgmfs                      100K     0  100K   0% /run/cgmanager/fs
tmpfs                      298M   12K  298M   1% /run/user/1002
tmpfs                      298M   52K  298M   1% /run/user/1000
/dev/sdd1                  1.9T  1.5T  361G  81% /media/cch/2.0T
/dev/sde1                  7.6G  3.6G  4.0G  48% /media/cch/W7_X64_OEM_ESD_en-US_Apr2015
cch@mint-av ~ $ dpkg -l | grep linux
ii  apturl                                       0.5.2+linuxmint3                           all          install packages using the apt protocol - GTK+ frontend
ii  apturl-common                                0.5.2+linuxmint3                           all          install packages using the apt protocol - common data
ii  bash                                         4.3+linuxmint3                             amd64        GNU Bourne Again SHell
ii  console-setup-linux                          1.108ubuntu15.2                            all          Linux specific part of console-setup
ii  firefox                                      50.1.0+linuxmint1+serena                   amd64        Safe and easy web browser from Mozilla
ii  firefox-locale-en                            50.1.0+linuxmint1+serena                   amd64        English language pack for Firefox
ii  indicator-sound                              12.10.2+16.04.20160714-1linuxmint1         amd64        System sound indicator.
ii  libgarcon-1-0                                0.4.0-2linuxmint1                          amd64        freedesktop.org compliant menu implementation for Xfce
ii  libgarcon-common                             0.4.0-2linuxmint1                          all          common files for libgarcon menu implementation
ii  libgksu2-0                                   2.0.13~pre1-7linuxmint4                    amd64        library providing su and sudo functionality
ii  libselinux1:amd64                            2.4-3build2                                amd64        SELinux runtime shared libraries
ii  libselinux1:i386                             2.4-3build2                                i386         SELinux runtime shared libraries
ii  libv4l-0:amd64                               1.10.0-1                                   amd64        Collection of video4linux support libraries
ii  libv4l-0:i386                                1.10.0-1                                   i386         Collection of video4linux support libraries
ii  libv4lconvert0:amd64                         1.10.0-1                                   amd64        Video4linux frame format conversion library
ii  libv4lconvert0:i386                          1.10.0-1                                   i386         Video4linux frame format conversion library
ii  linux-base                                   4.0ubuntu1                                 all          Linux image base package
iF  linux-firmware                               1.157.6                                    all          Firmware for Linux kernel drivers
ii  linux-headers-4.4.0-21                       4.4.0-21.37                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-21-generic               4.4.0-21.37                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-36                       4.4.0-36.55                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-36-generic               4.4.0-36.55                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-38                       4.4.0-38.57                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-38-generic               4.4.0-38.57                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-42                       4.4.0-42.62                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-42-generic               4.4.0-42.62                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-43                       4.4.0-43.63                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-43-generic               4.4.0-43.63                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-45                       4.4.0-45.66                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-45-generic               4.4.0-45.66                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-47                       4.4.0-47.68                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-47-generic               4.4.0-47.68                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-51                       4.4.0-51.72                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-51-generic               4.4.0-51.72                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-53                       4.4.0-53.74                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-53-generic               4.4.0-53.74                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-57                       4.4.0-57.78                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-57-generic               4.4.0-57.78                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-36-generic                 4.4.0-36.55                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-38-generic                 4.4.0-38.57                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-42-generic                 4.4.0-42.62                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-43-generic                 4.4.0-43.63                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-45-generic                 4.4.0-45.66                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-47-generic                 4.4.0-47.68                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-51-generic                 4.4.0-51.72                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-53-generic                 4.4.0-53.74                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-57-generic                 4.4.0-57.78                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-21-generic           4.4.0-21.37                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-36-generic           4.4.0-36.55                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-38-generic           4.4.0-38.57                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-42-generic           4.4.0-42.62                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-43-generic           4.4.0-43.63                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-45-generic           4.4.0-45.66                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-47-generic           4.4.0-47.68                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-51-generic           4.4.0-51.72                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-extra-4.4.0-53-generic           4.4.0-53.74                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-57-generic           4.4.0-57.78                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-libc-dev:amd64                         4.4.0-57.78                                amd64        Linux Kernel Headers for development
ii  linux-sound-base                             1.0.25+dfsg-0ubuntu5                       all          base package for ALSA and OSS sound systems
ii  linuxmint-keyring                            2016.05.26                                 all          GnuPG key of the Linux Mint repository
ii  pptp-linux                                   1.8.0-1                                    amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  synaptic                                     0.83linuxmint3                             amd64        Graphical package manager
ii  syslinux                                     3:6.03+dfsg-11ubuntu1                      amd64        collection of bootloaders (DOS FAT and NTFS bootloader)
ii  syslinux-common                              3:6.03+dfsg-11ubuntu1                      all          collection of bootloaders (common)
ii  syslinux-legacy                              2:3.63+dfsg-2ubuntu8                       amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  syslinux-utils                               3:6.03+dfsg-11ubuntu1                      amd64        collection of bootloaders (utilities)
ii  ubuntu-drivers-common                        1:0.4.17.2linuxmint1                       amd64        Detect and install additional Ubuntu driver packages
ii  util-linux                                   2.27.1-6ubuntu3.1                          amd64        miscellaneous system utilities
cch@mint-av ~ $ 

```

```
cch@mint-av ~ $ ls -al /vmlinuz*
lrwxrwxrwx 1 root root 29 Dec 29 11:45 /vmlinuz -> boot/vmlinuz-4.4.0-57-generic
lrwxrwxrwx 1 root root 29 Dec  8 04:14 /vmlinuz.old -> boot/vmlinuz-4.4.0-53-generic
cch@mint-av ~ $ ls -al /initrd.img*
lrwxrwxrwx 1 root root 32 Jan  7 14:32 /initrd.img -> boot/initrd.img-4.4.0-57-generic
lrwxrwxrwx 1 root root 32 Jan  7 14:30 /initrd.img.old -> boot/initrd.img-4.4.0-57-generic
cch@mint-av ~ $ ls -al /boot
total 434550
drwxr-xr-x  4 root root     4096 Jan  7 14:34 .
drwxr-xr-x 23 root root     4096 Jan  7 14:32 ..
-rw-r--r--  1 root root  1241960 Aug 11 15:58 abi-4.4.0-36-generic
-rw-r--r--  1 root root  1242262 Sep  6 14:52 abi-4.4.0-38-generic
-rw-r--r--  1 root root  1242701 Oct  7 22:15 abi-4.4.0-42-generic
-rw-r--r--  1 root root  1242701 Oct 12 11:47 abi-4.4.0-43-generic
-rw-r--r--  1 root root  1242701 Oct 19 12:34 abi-4.4.0-45-generic
-rw-r--r--  1 root root  1243086 Oct 26 18:27 abi-4.4.0-47-generic
-rw-r--r--  1 root root  1243479 Nov 24 16:12 abi-4.4.0-51-generic
-rw-r--r--  1 root root  1243479 Dec  2 14:11 abi-4.4.0-53-generic
-rw-r--r--  1 root root  1243800 Dec  9 23:04 abi-4.4.0-57-generic
-rw-r--r--  1 root root   189696 Aug 11 15:58 config-4.4.0-36-generic
-rw-r--r--  1 root root   189732 Sep  6 14:52 config-4.4.0-38-generic
-rw-r--r--  1 root root   189760 Oct  7 22:15 config-4.4.0-42-generic
-rw-r--r--  1 root root   189760 Oct 12 11:47 config-4.4.0-43-generic
-rw-r--r--  1 root root   189760 Oct 19 12:34 config-4.4.0-45-generic
-rw-r--r--  1 root root   189809 Oct 26 18:27 config-4.4.0-47-generic
-rw-r--r--  1 root root   189877 Nov 24 16:12 config-4.4.0-51-generic
-rw-r--r--  1 root root   189877 Dec  2 14:11 config-4.4.0-53-generic
-rw-r--r--  1 root root   189991 Dec  9 23:04 config-4.4.0-57-generic
drwxr-xr-x  5 root root     1024 Jan  7 14:29 grub
-rw-r--r--  1 root root 11313032 Jan  7 14:28 initrd.img-4.4.0-21-generic
-rw-r--r--  1 root root 38549345 Sep 15 02:53 initrd.img-4.4.0-36-generic
-rw-r--r--  1 root root 39819772 Oct  6 10:49 initrd.img-4.4.0-38-generic
-rw-r--r--  1 root root 40224595 Oct 12 23:30 initrd.img-4.4.0-42-generic
-rw-r--r--  1 root root 40224819 Oct 17 18:47 initrd.img-4.4.0-43-generic
-rw-r--r--  1 root root 40225227 Nov  3 16:58 initrd.img-4.4.0-45-generic
-rw-r--r--  1 root root 40325134 Nov 19 20:41 initrd.img-4.4.0-47-generic
-rw-r--r--  1 root root 40331187 Nov 30 10:41 initrd.img-4.4.0-51-generic
-rw-r--r--  1 root root 40329780 Dec  8 04:15 initrd.img-4.4.0-53-generic
drwx------  2 root root    12288 Aug 31 19:25 lost+found
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  3867829 Aug 11 15:58 System.map-4.4.0-36-generic
-rw-------  1 root root  3869329 Sep  6 14:52 System.map-4.4.0-38-generic
-rw-------  1 root root  3869895 Oct  7 22:15 System.map-4.4.0-42-generic
-rw-------  1 root root  3869895 Oct 12 11:47 System.map-4.4.0-43-generic
-rw-------  1 root root  3869895 Oct 19 12:34 System.map-4.4.0-45-generic
-rw-------  1 root root  3873447 Oct 26 18:27 System.map-4.4.0-47-generic
-rw-------  1 root root  3874377 Nov 24 16:12 System.map-4.4.0-51-generic
-rw-------  1 root root  3874377 Dec  2 14:11 System.map-4.4.0-53-generic
-rw-------  1 root root  3875329 Dec  9 23:04 System.map-4.4.0-57-generic
-rw-------  1 root root  7045472 Aug 11 15:58 vmlinuz-4.4.0-36-generic
-rw-------  1 root root  7051680 Sep  6 14:52 vmlinuz-4.4.0-38-generic
-rw-------  1 root root  7053472 Oct  7 22:15 vmlinuz-4.4.0-42-generic
-rw-------  1 root root  7053568 Oct 12 11:47 vmlinuz-4.4.0-43-generic
-rw-------  1 root root  7054208 Oct 19 12:34 vmlinuz-4.4.0-45-generic
-rw-------  1 root root  7060896 Oct 26 18:27 vmlinuz-4.4.0-47-generic
-rw-------  1 root root  7064208 Nov 24 16:12 vmlinuz-4.4.0-51-generic
-rw-------  1 root root  7065648 Dec  2 14:11 vmlinuz-4.4.0-53-generic
-rw-------  1 root root  7067152 Dec  9 23:04 vmlinuz-4.4.0-57-generic

```

sorry for such a late reply... lots goin' on lately
and btw, i can boot

---

### Post by ccheath on 2017-01-07
think i might be good.. here's what i did```
cch@mint-av ~ $ sudo apt-get autoremove
[sudo] password for cch: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up initramfs-tools (0.122ubuntu8.7) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-firmware (1.157.6) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-53-generic
Warning: No support for locale: en_US.utf8

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-53-generic with 1.
dpkg: error processing package linux-firmware (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-image-4.4.0-57-generic (4.4.0-57.78) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-4.4.0-57-generic
vmlinuz(/boot/vmlinuz-4.4.0-57-generic
) points to /boot/vmlinuz-4.4.0-57-generic
 (/boot/vmlinuz-4.4.0-57-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-57-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-57-generic
Warning: No support for locale: en_US.utf8

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-57-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-57-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-57-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-extra-4.4.0-53-generic (4.4.0-53.74) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-53-generic
Warning: No support for locale: en_US.utf8

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-53-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-53-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-57-generic:
 linux-image-extra-4.4.0-57-generic depends on linux-image-4.4.0-57-generic; however:
  Package linux-image-4.4.0-57-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-57-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools (0.122ubuntu8.7) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-53-generic
Warning: No support for locale: en_US.utf8

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-53-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-firmware
 linux-image-4.4.0-57-generic
 linux-image-extra-4.4.0-53-generic
 linux-image-extra-4.4.0-57-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
cch@mint-av ~ $ df -h
Filesystem                 Size  Used Avail Use% Mounted on
udev                       1.5G     0  1.5G   0% /dev
tmpfs                      298M   32M  266M  11% /run
/dev/mapper/mint--vg-root  144G   20G  117G  15% /
tmpfs                      1.5G  9.1M  1.5G   1% /dev/shm
tmpfs                      5.0M  4.0K  5.0M   1% /run/lock
tmpfs                      1.5G     0  1.5G   0% /sys/fs/cgroup
/dev/sda1                  472M  434M   14M  97% /boot
cgmfs                      100K     0  100K   0% /run/cgmanager/fs
tmpfs                      298M   12K  298M   1% /run/user/1002
tmpfs                      298M   52K  298M   1% /run/user/1000
/dev/sdd1                  1.9T  1.5T  361G  81% /media/cch/2.0T
/dev/sde1                  7.6G  3.6G  4.0G  48% /media/cch/W7_X64_OEM_ESD_en-US_Apr2015
cch@mint-av ~ $ sudo apt-get purge linux-image-4.4.0-21
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-image-4.4.0-21-generic' for regex 'linux-image-4.4.0-21'
Note, selecting 'linux-image-4.4.0-21-lowlatency' for regex 'linux-image-4.4.0-21'
Package 'linux-image-4.4.0-21-generic' is not installed, so not removed
Package 'linux-image-4.4.0-21-lowlatency' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up initramfs-tools (0.122ubuntu8.7) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-firmware (1.157.6) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-53-generic
Warning: No support for locale: en_US.utf8

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-53-generic with 1.
dpkg: error processing package linux-firmware (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-image-4.4.0-57-generic (4.4.0-57.78) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-4.4.0-57-generic
vmlinuz(/boot/vmlinuz-4.4.0-57-generic
) points to /boot/vmlinuz-4.4.0-57-generic
 (/boot/vmlinuz-4.4.0-57-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-57-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-57-generic
Warning: No support for locale: en_US.utf8

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-57-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-57-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-57-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-extra-4.4.0-53-generic (4.4.0-53.74) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-53-generic
Warning: No support for locale: en_US.utf8

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-53-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-53-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-57-generic:
 linux-image-extra-4.4.0-57-generic depends on linux-image-4.4.0-57-generic; however:
  Package linux-image-4.4.0-57-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-57-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools (0.122ubuntu8.7) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-53-generic
Warning: No support for locale: en_US.utf8

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-53-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-firmware
 linux-image-4.4.0-57-generic
 linux-image-extra-4.4.0-53-generic
 linux-image-extra-4.4.0-57-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
cch@mint-av ~ $ df -h
Filesystem                 Size  Used Avail Use% Mounted on
udev                       1.5G     0  1.5G   0% /dev
tmpfs                      298M   32M  266M  11% /run
/dev/mapper/mint--vg-root  144G   21G  116G  15% /
tmpfs                      1.5G  9.1M  1.5G   1% /dev/shm
tmpfs                      5.0M  4.0K  5.0M   1% /run/lock
tmpfs                      1.5G     0  1.5G   0% /sys/fs/cgroup
/dev/sda1                  472M  423M   25M  95% /boot
cgmfs                      100K     0  100K   0% /run/cgmanager/fs
tmpfs                      298M   12K  298M   1% /run/user/1002
tmpfs                      298M   52K  298M   1% /run/user/1000
/dev/sdd1                  1.9T  1.5T  361G  81% /media/cch/2.0T
/dev/sde1                  7.6G  3.6G  4.0G  48% /media/cch/W7_X64_OEM_ESD_en-US_Apr2015
cch@mint-av ~ $ sudo apt-get purge linux-image-4.4.0-36-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-4.4.0-36-generic* linux-image-extra-4.4.0-36-generic*
0 upgraded, 0 newly installed, 2 to remove and 9 not upgraded.
5 not fully installed or removed.
After this operation, 218 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 490498 files and directories currently installed.)
Removing linux-image-extra-4.4.0-36-generic (4.4.0-36.55) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-36-generic
Warning: No support for locale: en_US.utf8
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found initrd image: /boot/initrd.img-4.4.0-36-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sde1
done
Purging configuration files for linux-image-extra-4.4.0-36-generic (4.4.0-36.55) ...
Removing linux-image-4.4.0-36-generic (4.4.0-36.55) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
dkms: removing: bcmwl 6.30.223.248+bdcom (4.4.0-36-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.30.223.248+bdcom
Kernel:  4.4.0-36-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-36-generic/updates/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
dkms: removing: ndiswrapper 1.59 (4.4.0-36-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  ndiswrapper
Version: 1.59
Kernel:  4.4.0-36-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

ndiswrapper.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-36-generic/updates/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
dkms: removing: virtualbox-guest 5.0.24 (4.4.0-36-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  virtualbox-guest
Version: 5.0.24
Kernel:  4.4.0-36-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxguest.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-36-generic/updates/
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/4.4.0-36-generic/updates/

vboxsf.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-36-generic/updates/
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/4.4.0-36-generic/updates/

vboxvideo.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-36-generic/updates/
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/4.4.0-36-generic/updates/
depmod....

Removing original_module from DKMS tree for kernel 4.4.0-36-generic (x86_64)

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sde1
done
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-4.4.0-36-generic (4.4.0-36.55) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
Setting up initramfs-tools (0.122ubuntu8.7) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-firmware (1.157.6) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-53-generic
Warning: No support for locale: en_US.utf8
update-initramfs: Generating /boot/initrd.img-4.4.0-51-generic
Warning: No support for locale: en_US.utf8
update-initramfs: Generating /boot/initrd.img-4.4.0-47-generic
Warning: No support for locale: en_US.utf8
update-initramfs: Generating /boot/initrd.img-4.4.0-45-generic
Warning: No support for locale: en_US.utf8
update-initramfs: Generating /boot/initrd.img-4.4.0-43-generic
Warning: No support for locale: en_US.utf8
update-initramfs: Generating /boot/initrd.img-4.4.0-42-generic
Warning: No support for locale: en_US.utf8
update-initramfs: Generating /boot/initrd.img-4.4.0-38-generic
Warning: No support for locale: en_US.utf8
update-initramfs: Generating /boot/initrd.img-4.4.0-21-generic
Warning: No support for locale: en_US.utf8
depmod: WARNING: could not open /var/tmp/mkinitramfs_2BoewT/lib/modules/4.4.0-21-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_2BoewT/lib/modules/4.4.0-21-generic/modules.builtin: No such file or directory
Setting up linux-image-4.4.0-57-generic (4.4.0-57.78) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
vmlinuz(/boot/vmlinuz-4.4.0-57-generic
) points to /boot/vmlinuz-4.4.0-57-generic
 (/boot/vmlinuz-4.4.0-57-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-57-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-57-generic
Warning: No support for locale: en_US.utf8
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sde1
done
Setting up linux-image-extra-4.4.0-53-generic (4.4.0-53.74) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-53-generic
Warning: No support for locale: en_US.utf8
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sde1
done
Setting up linux-image-extra-4.4.0-57-generic (4.4.0-57.78) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-57-generic
Warning: No support for locale: en_US.utf8
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sde1
done
Processing triggers for initramfs-tools (0.122ubuntu8.7) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-57-generic
Warning: No support for locale: en_US.utf8
cch@mint-av ~ $ df -h
Filesystem                 Size  Used Avail Use% Mounted on
udev                       1.5G     0  1.5G   0% /dev
tmpfs                      298M   32M  266M  11% /run
/dev/mapper/mint--vg-root  144G   21G  116G  15% /
tmpfs                      1.5G  9.1M  1.5G   1% /dev/shm
tmpfs                      5.0M  4.0K  5.0M   1% /run/lock
tmpfs                      1.5G     0  1.5G   0% /sys/fs/cgroup
/dev/sda1                  472M  424M   24M  95% /boot
cgmfs                      100K     0  100K   0% /run/cgmanager/fs
tmpfs                      298M   12K  298M   1% /run/user/1002
tmpfs                      298M   52K  298M   1% /run/user/1000
/dev/sdd1                  1.9T  1.5T  361G  81% /media/cch/2.0T
/dev/sde1                  7.6G  3.6G  4.0G  48% /media/cch/W7_X64_OEM_ESD_en-US_Apr2015
cch@mint-av ~ $ sudo apt-get purge linux-image-4.4.0-38-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-4.4.0-38-generic* linux-image-extra-4.4.0-38-generic*
0 upgraded, 0 newly installed, 2 to remove and 9 not upgraded.
After this operation, 218 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 484908 files and directories currently installed.)
Removing linux-image-extra-4.4.0-38-generic (4.4.0-38.57) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-38-generic
Warning: No support for locale: en_US.utf8
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sde1
done
Purging configuration files for linux-image-extra-4.4.0-38-generic (4.4.0-38.57) ...
Removing linux-image-4.4.0-38-generic (4.4.0-38.57) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
dkms: removing: bcmwl 6.30.223.248+bdcom (4.4.0-38-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.30.223.248+bdcom
Kernel:  4.4.0-38-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-38-generic/updates/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
dkms: removing: ndiswrapper 1.59 (4.4.0-38-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  ndiswrapper
Version: 1.59
Kernel:  4.4.0-38-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

ndiswrapper.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-38-generic/updates/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
dkms: removing: virtualbox-guest 5.0.24 (4.4.0-38-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  virtualbox-guest
Version: 5.0.24
Kernel:  4.4.0-38-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxguest.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-38-generic/updates/
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/4.4.0-38-generic/updates/

vboxsf.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-38-generic/updates/
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/4.4.0-38-generic/updates/

vboxvideo.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-38-generic/updates/
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/4.4.0-38-generic/updates/
depmod....

Removing original_module from DKMS tree for kernel 4.4.0-38-generic (x86_64)

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-38-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sde1
done
Purging configuration files for linux-image-4.4.0-38-generic (4.4.0-38.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
cch@mint-av ~ $ df -h
Filesystem                 Size  Used Avail Use% Mounted on
udev                       1.5G     0  1.5G   0% /dev
tmpfs                      298M   32M  266M  11% /run
/dev/mapper/mint--vg-root  144G   20G  117G  15% /
tmpfs                      1.5G  9.1M  1.5G   1% /dev/shm
tmpfs                      5.0M  4.0K  5.0M   1% /run/lock
tmpfs                      1.5G     0  1.5G   0% /sys/fs/cgroup
/dev/sda1                  472M  374M   74M  84% /boot
cgmfs                      100K     0  100K   0% /run/cgmanager/fs
tmpfs                      298M   12K  298M   1% /run/user/1002
tmpfs                      298M   52K  298M   1% /run/user/1000
/dev/sdd1                  1.9T  1.5T  361G  81% /media/cch/2.0T
/dev/sde1                  7.6G  3.6G  4.0G  48% /media/cch/W7_X64_OEM_ESD_en-US_Apr2015
cch@mint-av ~ $ sudo apt-get purge linux-image-4.4.0-42-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-4.4.0-42-generic* linux-image-extra-4.4.0-42-generic*
0 upgraded, 0 newly installed, 2 to remove and 9 not upgraded.
After this operation, 218 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 479316 files and directories currently installed.)
Removing linux-image-extra-4.4.0-42-generic (4.4.0-42.62) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-42-generic
Warning: No support for locale: en_US.utf8
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sde1
done
Purging configuration files for linux-image-extra-4.4.0-42-generic (4.4.0-42.62) ...
Removing linux-image-4.4.0-42-generic (4.4.0-42.62) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
dkms: removing: bcmwl 6.30.223.248+bdcom (4.4.0-42-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.30.223.248+bdcom
Kernel:  4.4.0-42-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-42-generic/updates/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
dkms: removing: ndiswrapper 1.59 (4.4.0-42-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  ndiswrapper
Version: 1.59
Kernel:  4.4.0-42-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

ndiswrapper.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-42-generic/updates/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
dkms: removing: virtualbox-guest 5.0.24 (4.4.0-42-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  virtualbox-guest
Version: 5.0.24
Kernel:  4.4.0-42-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxguest.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-42-generic/updates/
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/4.4.0-42-generic/updates/

vboxsf.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-42-generic/updates/
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/4.4.0-42-generic/updates/

vboxvideo.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-42-generic/updates/
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/4.4.0-42-generic/updates/
depmod....

Removing original_module from DKMS tree for kernel 4.4.0-42-generic (x86_64)

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-42-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sde1
done
Purging configuration files for linux-image-4.4.0-42-generic (4.4.0-42.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
cch@mint-av ~ $ df -h
Filesystem                 Size  Used Avail Use% Mounted on
udev                       1.5G     0  1.5G   0% /dev
tmpfs                      298M   32M  266M  11% /run
/dev/mapper/mint--vg-root  144G   20G  117G  15% /
tmpfs                      1.5G  9.1M  1.5G   1% /dev/shm
tmpfs                      5.0M  4.0K  5.0M   1% /run/lock
tmpfs                      1.5G     0  1.5G   0% /sys/fs/cgroup
/dev/sda1                  472M  323M  125M  73% /boot
cgmfs                      100K     0  100K   0% /run/cgmanager/fs
tmpfs                      298M   12K  298M   1% /run/user/1002
tmpfs                      298M   52K  298M   1% /run/user/1000
/dev/sdd1                  1.9T  1.5T  361G  81% /media/cch/2.0T
/dev/sde1                  7.6G  3.6G  4.0G  48% /media/cch/W7_X64_OEM_ESD_en-US_Apr2015
cch@mint-av ~ $ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
cch@mint-av ~ $ sudo apt-get update 
Hit:1 http://archive.linux.duke.edu/ubuntu xenial InRelease
Hit:2 http://archive.linux.duke.edu/ubuntu xenial-updates InRelease                                                                                                    
Ign:3 http://mirrors.advancedhosters.com/linuxmint/packages sarah InRelease                                                                                            
Hit:4 http://mirrors.advancedhosters.com/linuxmint/packages sarah Release                                                                                              
Hit:5 http://archive.canonical.com/ubuntu xenial InRelease                                                                                          
Hit:6 http://ppa.launchpad.net/team-xbmc/ppa/ubuntu xenial InRelease                                                                                
Get:7 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]                    
Hit:8 http://archive.linux.duke.edu/ubuntu xenial-backports InRelease             
Fetched 102 kB in 1s (68.7 kB/s)                                                  
Reading package lists... Done
cch@mint-av ~ $ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
cch@mint-av ~ $ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  grub-common grub-pc grub-pc-bin grub2-common libnss3:i386 libnss3 libnss3-1d libnss3-nssdb unattended-upgrades
9 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 5,720 kB of archives.
After this operation, 76.8 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.linux.duke.edu/ubuntu xenial-updates/main amd64 grub-pc amd64 2.02~beta2-36ubuntu3.6 [197 kB]
Get:2 http://archive.linux.duke.edu/ubuntu xenial-updates/main amd64 grub-pc-bin amd64 2.02~beta2-36ubuntu3.6 [889 kB]
Get:3 http://archive.linux.duke.edu/ubuntu xenial-updates/main amd64 grub2-common amd64 2.02~beta2-36ubuntu3.6 [512 kB]
Get:4 http://archive.linux.duke.edu/ubuntu xenial-updates/main amd64 grub-common amd64 2.02~beta2-36ubuntu3.6 [1,706 kB]
Get:5 http://archive.linux.duke.edu/ubuntu xenial-updates/main amd64 libnss3-1d amd64 2:3.26.2-0ubuntu0.16.04.2 [9,308 B]
Get:6 http://archive.linux.duke.edu/ubuntu xenial-updates/main amd64 libnss3-nssdb all 2:3.26.2-0ubuntu0.16.04.2 [10.6 kB]
Get:7 http://archive.linux.duke.edu/ubuntu xenial-updates/main amd64 libnss3 amd64 2:3.26.2-0ubuntu0.16.04.2 [1,153 kB]
Get:8 http://archive.linux.duke.edu/ubuntu xenial-updates/main i386 libnss3 i386 2:3.26.2-0ubuntu0.16.04.2 [1,212 kB]
Get:9 http://archive.linux.duke.edu/ubuntu xenial-updates/main amd64 unattended-upgrades all 0.90ubuntu0.3 [31.7 kB]
Fetched 5,720 kB in 2s (2,771 kB/s)       
Preconfiguring packages ...
(Reading database ... 473725 files and directories currently installed.)
Preparing to unpack .../grub-pc_2.02~beta2-36ubuntu3.6_amd64.deb ...
Unpacking grub-pc (2.02~beta2-36ubuntu3.6) over (2.02~beta2-36ubuntu3.2) ...
Preparing to unpack .../grub-pc-bin_2.02~beta2-36ubuntu3.6_amd64.deb ...
Unpacking grub-pc-bin (2.02~beta2-36ubuntu3.6) over (2.02~beta2-36ubuntu3.2) ...
Preparing to unpack .../grub2-common_2.02~beta2-36ubuntu3.6_amd64.deb ...
Unpacking grub2-common (2.02~beta2-36ubuntu3.6) over (2.02~beta2-36ubuntu3.2) ...
Preparing to unpack .../grub-common_2.02~beta2-36ubuntu3.6_amd64.deb ...
Unpacking grub-common (2.02~beta2-36ubuntu3.6) over (2.02~beta2-36ubuntu3.2) ...
Preparing to unpack .../libnss3-nssdb_2%3a3.26.2-0ubuntu0.16.04.2_all.deb ...
Unpacking libnss3-nssdb (2:3.26.2-0ubuntu0.16.04.2) over (2:3.23-0ubuntu0.16.04.1) ...
Preparing to unpack .../libnss3-1d_2%3a3.26.2-0ubuntu0.16.04.2_amd64.deb ...
Unpacking libnss3-1d:amd64 (2:3.26.2-0ubuntu0.16.04.2) over (2:3.23-0ubuntu0.16.04.1) ...
Preparing to unpack .../libnss3_2%3a3.26.2-0ubuntu0.16.04.2_amd64.deb ...
De-configuring libnss3:i386 (2:3.23-0ubuntu0.16.04.1) ...
Unpacking libnss3:amd64 (2:3.26.2-0ubuntu0.16.04.2) over (2:3.23-0ubuntu0.16.04.1) ...
Preparing to unpack .../libnss3_2%3a3.26.2-0ubuntu0.16.04.2_i386.deb ...
Unpacking libnss3:i386 (2:3.26.2-0ubuntu0.16.04.2) over (2:3.23-0ubuntu0.16.04.1) ...
Preparing to unpack .../unattended-upgrades_0.90ubuntu0.3_all.deb ...
Unpacking unattended-upgrades (0.90ubuntu0.3) over (0.90ubuntu0.2) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for install-info (6.1.0.dfsg.1-5) ...
Processing triggers for systemd (229-4ubuntu13) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Setting up grub-common (2.02~beta2-36ubuntu3.6) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Setting up grub2-common (2.02~beta2-36ubuntu3.6) ...
Setting up grub-pc-bin (2.02~beta2-36ubuntu3.6) ...
Setting up grub-pc (2.02~beta2-36ubuntu3.6) ...
Installing for i386-pc platform.
Installation finished. No error reported.
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sde1
done
Setting up unattended-upgrades (0.90ubuntu0.3) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Setting up libnss3-nssdb (2:3.26.2-0ubuntu0.16.04.2) ...
Setting up libnss3:amd64 (2:3.26.2-0ubuntu0.16.04.2) ...
Setting up libnss3:i386 (2:3.26.2-0ubuntu0.16.04.2) ...
Setting up libnss3-1d:amd64 (2:3.26.2-0ubuntu0.16.04.2) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...

```

---

### Post by ian-weisser on 2017-01-07
Autoremove did not fail...but it also did not do what you expected.
You still have six kernels installed, and little available space in /boot.

Suggestion: Uninstall the oldest four kernels.
Suggestion: Mark your calendar once every three months or so to clean out /boot manually.

---

### Post by ccheath on 2017-01-08
thanks ian
i was in the process of doing just that when you posted 
i used the mint update gui to do the kernel removals

thanks to all for the help

---

