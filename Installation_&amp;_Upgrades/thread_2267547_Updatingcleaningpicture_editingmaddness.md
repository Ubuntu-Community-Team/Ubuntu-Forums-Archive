---
title: "Updating/cleaning/picture editing/maddness"
date: 2015-03-02
forum: Installation &amp; Upgrades
---

### Post by russ12 on 2015-03-02
This all started when I was trying to do a normal software update.  It hasn't worked for the past couple months, there has always been an error about proken packages.  Recently this error has turned to not enough room in /boot.  This is fine, I know how to fix this, I have done it before.  Used synaptic to clear up old kernals.  Went to again install updates, boot is full.  Check boot, still shows kernals.  Try to remove them, says they are not installed.  Great.  Try to update 3.13.0-46 - says its broken and I continually get errors. Below is an autoremove command, I get the same errors using sudo apt-get -f install and the like:

```
russell@bokbok-DodoBird:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-extra-3.13.0-46-generic
0 upgraded, 0 newly installed, 1 to remove and 19 not upgraded.
7 not fully installed or removed.
After this operation, 152 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 503382 files and directories currently installed.)
Removing linux-image-extra-3.13.0-46-generic (3.13.0-46.76) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-46-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-46-generic
grep: /boot/config-3.13.0-46-generic: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_A6Zaol/lib/modules/3.13.0-46-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_A6Zaol/lib/modules/3.13.0-46-generic/modules.builtin: No such file or directory

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-46-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-46-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-46-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

I'm at a loss for where to go from here.  I tried updating from 14.04 to 14.10, but it says no room in /boot.  I have thought about reformatting, but I am not on the same continent as my backup hdd, so I am not really happy with that idea.

---

### Post by tgalati4 on 2015-03-02
How much space do you have on your other partitions?  

```
df -h
```

---

### Post by ian-weisser on 2015-03-02
Remove a different old kernel, so -46 has room to finish installing.
Use dpkg -l to list what you have installed...or simply look in /boot

Or, if you don't actually use LVM or encryption, reinstall without them (which is what creates the separate /boot)

---

### Post by russ12 on 2015-03-02
There is no room in boot, thats the issue I am having.

```
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  454G  180G  251G  42% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         1.9G  8.0K  1.9G   1% /dev
tmpfs                        378M  1.5M  376M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         1.9G  1.2M  1.9G   1% /run/shm
none                         100M   64K  100M   1% /run/user
/dev/sda2                    237M  233M     0 100% /boot
/dev/sda1                    487M  3.4M  483M   1% /boot/efi


```

dpkg -l lists a dragon-load of stuff, more than I care to sort through.  Is there a faster way to purge than manually going through?  

When I reformatted my computer last, my friend and I flipped a coin as to whether I should use encription (cause why not?) so I now have encryption on.  What will this force as far as reinstallation goes?

---

### Post by ajgreeny on 2015-03-02
Try running command **sudo apt-get autoremove**

Several users have reported that this command will remove excess kernels, leaving you with just two, the current version and one previous, which is the way to run an OS, but as far as I'm aware, it will work only in 14.04 or later versions of Ubuntu.

If that does not work come back again and we can look at alternative ways using synaptic or a long, complicated clean-up command.

---

### Post by Impavidus on 2015-03-02
Autoremoving old kernels was introduced in Ubuntu 13.10. It works most of the time, but for some reason not always. It may in particular not work if the package system is already broken. But still worth a try.

To get a more useful list from dpkg, use```
dpkg -l "linux-image*"
```That will just list the installed kernel packages.

---

### Post by ian-weisser on 2015-03-02
> **russ12 said:**
>  When I reformatted my computer last, my friend and I flipped a coin as to whether I should use encription (cause why not?) so I now have encryption on.  What will this force as far as reinstallation goes?

Encryption requires a separate /boot.
A known bug in the kernel-autoremoval script (help is welcome to identify the problem and fix it!) causes autoremoval to fail in those separate partitions. Hence your full /boot partition.
It's not a big deal, cleaning out old kernels before the partition tops out is a minor and simple chore. A small price to pay for encryption. And someday some clever person will figure out the bug.

But that's off the point.

Use Impavidus's advice to learn which kernel packages can be safely removed.
Then use dpkg (not apt) to remove some of those packages.
When you have freed enough space in /boot by removing old (unused) kernel packages, apt will be able to finish installing 3.13.0-46. Then apt should work.
Once apt is working, you can use autoremove to clean up a bit.
And then put occasional kernel cleaning on your calendar because you are using a separate /boot.

There are several other fast and clever ways to fix the problem (workaround the bug), but this is the most straightforward and understandable for most users. The others can be rather arcane.

---

### Post by tgalati4 on 2015-03-02
I think we have hit an Edge Case.  Autoremove will remove old kernels unless the package fails due to having run out of room in /boot.  So the tool to fix this condition fails--sort of like having a flat spare tire.  It's nice to have a spare tire, but if it is flat then it does not really serve its purpose.

The OP might have to manually remove old kernels in /boot and may have to do this from a Live Session or boot from GRUB into an older kernel that is still intact.

That is like trying to change a flat tire without a jack--not easy but doable.

---

### Post by russ12 on 2015-03-03
When trying to update, I continually get the error that /boot is full and to use the command sudo apt-get clean.  This command has never worked for me.  Tried autoremove and as guessed, it returns an error:

```
russell@bokbok-DodoBird:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-extra-3.13.0-46-generic
0 upgraded, 0 newly installed, 1 to remove and 19 not upgraded.
7 not fully installed or removed.
After this operation, 152 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 503382 files and directories currently installed.)
Removing linux-image-extra-3.13.0-46-generic (3.13.0-46.76) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-46-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-46-generic
grep: /boot/config-3.13.0-46-generic: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_zxdfon/lib/modules/3.13.0-46-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_zxdfon/lib/modules/3.13.0-46-generic/modules.builtin: No such file or directory

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-46-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-46-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-46-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
russell@bokbok-DodoBird:~$ 


```

Am I reading this right that it won't install because there isn't enough room, but it won't uninstall because its not fully installed?

The dpkg command returns this: 

```
russell@bokbok-DodoBird:~$ dpkg -l "linux-image"
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  linux-image    <none>       <none>       (no description available)
russell@bokbok-DodoBird:~$ 


```

---

### Post by ajgreeny on 2015-03-03
Yes, you are reading it right, I think.

You forgot to include the asterisk in your **dpkg -l "linux-image*"** command hence the almost no output you got.
Try again, exactly as I show in bold above.
 The simple way to do that is to highlight my command then middle click in your terminal: that will paste the buffer from memory - job done!

---

### Post by russ12 on 2015-03-03
Thats better.  I knew there were a bunch in there, otherwise /boot wouldn't be full, but it won't let me delete them either.

```

russell@bokbok-DodoBird:~$ dpkg -l "linux-image*"
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                  Version                 Architecture            Description
+++-=====================================-=======================-=======================-===============================================================================
un  linux-image                           <none>                  <none>                  (no description available)
un  linux-image-3.0                       <none>                  <none>                  (no description available)
un  linux-image-3.13.0-34-generic         <none>                  <none>                  (no description available)
un  linux-image-3.13.0-35-generic         <none>                  <none>                  (no description available)
ii  linux-image-3.13.0-37-generic         3.13.0-37.64            amd64                   Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-39-generic         3.13.0-39.66            amd64                   Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-40-generic         3.13.0-40.69            amd64                   Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-43-generic         3.13.0-43.72            amd64                   Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-44-generic         3.13.0-44.73            amd64                   Linux kernel image for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-3.13.0-45-generic         3.13.0-45.74            amd64                   Linux kernel image for version 3.13.0 on 64 bit x86 SMP
in  linux-image-3.13.0-46-generic         <none>                  amd64                   (no description available)
rc  linux-image-extra-3.13.0-34-generic   3.13.0-34.60            amd64                   Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-35-generic   3.13.0-35.62            amd64                   Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic   3.13.0-37.64            amd64                   Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic   3.13.0-39.66            amd64                   Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-40-generic   3.13.0-40.69            amd64                   Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic   3.13.0-43.72            amd64                   Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-extra-3.13.0-44-generic   3.13.0-44.73            amd64                   Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-extra-3.13.0-45-generic   3.13.0-45.74            amd64                   Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-46-generic   3.13.0-46.76            amd64                   Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
russell@bokbok-DodoBird:~$ 


```

---

### Post by Impavidus on 2015-03-03
I will assume you run kernel 3.13.0-43 now, which is the last one fully installed. You can check by running```
uname -r
```You can fully uninstall kernels 34 - 40 using dpkg:```
sudo dpkg --purge linux-image{,-extra}-3.13.0-{34,35,37,39,40}-generic
```That should clear enough space to finish installation of the new kernels.

---

### Post by russ12 on 2015-03-03
It shows I am currently running 44.  Also this:

```
russell@bokbok-DodoBird:~$ sudo dpkg --purge linux-image{,-extra}-3.13.0-{34,35,37,39}-generic
[sudo] password for russell: 
dpkg: warning: ignoring request to remove linux-image-3.13.0-34-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-3.13.0-35-generic which isn't installed
dpkg: dependency problems prevent removal of linux-image-3.13.0-37-generic:
 linux-signed-image-3.13.0-37-generic depends on linux-image-3.13.0-37-generic (= 3.13.0-37.64).

dpkg: error processing package linux-image-3.13.0-37-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-39-generic:
 linux-signed-image-3.13.0-39-generic depends on linux-image-3.13.0-39-generic (= 3.13.0-39.66).

dpkg: error processing package linux-image-3.13.0-39-generic (--purge):
 dependency problems - not removing
(Reading database ... 503382 files and directories currently installed.)
Removing linux-image-extra-3.13.0-34-generic (3.13.0-34.60) ...
Purging configuration files for linux-image-extra-3.13.0-34-generic (3.13.0-34.60) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
Removing linux-image-extra-3.13.0-35-generic (3.13.0-35.62) ...
Purging configuration files for linux-image-extra-3.13.0-35-generic (3.13.0-35.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
dpkg: dependency problems prevent removal of linux-image-extra-3.13.0-37-generic:
 linux-signed-image-3.13.0-37-generic depends on linux-image-extra-3.13.0-37-generic (= 3.13.0-37.64).

dpkg: error processing package linux-image-extra-3.13.0-37-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-extra-3.13.0-39-generic:
 linux-signed-image-3.13.0-39-generic depends on linux-image-extra-3.13.0-39-generic (= 3.13.0-39.66).

dpkg: error processing package linux-image-extra-3.13.0-39-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-3.13.0-37-generic
 linux-image-3.13.0-39-generic
 linux-image-extra-3.13.0-37-generic
 linux-image-extra-3.13.0-39-generic


```

---

### Post by tgalati4 on 2015-03-03
This is what I was referring to earlier.  The package system is broken because of the crash during an update.

Log in as *sudo* and manually *rm* the older kernels.

```
sudo su
```

---

### Post by russ12 on 2015-03-03
Success, I am now on .46!  After going in and removing the older kernels through terminal, then going to synaptic and removing them again, plus .45 which wasn't being used?, then reinstalling .46, I am back on track.

Last question: When I ```
dpkg -l "linux-image*"
``` how do I get it to not show all of the old kernels that are no longer installed?

---

### Post by tgalati4 on 2015-03-03
You need to clean up the *dpkg* database.  I don't know the exact syntax to do this.  Regardless, be careful because you can seriously break your system.

```
man dpkg
```

What is the output of:

```
sudo dpkg --audit
```

You want to cut-and-paste the list of problems and save them to a text file (using *zim* or *gedit* or *pluma*) before blasting the *dpkg* database.

---

### Post by ian-weisser on 2015-03-03
> **russ12 said:**
> [H]ow do I get it to not show all of the old kernels that are no longer installed?

Two ways:

1) The way I recommend to new users because it's safe: Reinstall the package, then uninstall it using the package manager
```
sudo apt-get install --reinstall linux-image-3.13.0-34-generic
sudo apt-get remove linux-image-3.13.0-34-generic
```

This repairs the inaccurate dpkg database by making it accurate first, then removing the packages you don't want anymore.
Apt will, of course, pull in dependencies as well. It takes longer and takes more disk space while working, but it's a proper clean removal.


2) The other way is faster, but I consider it DANGEROUS. I call it the nuclear option. I *never* use it (nor recommend it) unless I understand exactly what went wrong and how to prevent it from happening again. 
```
sudo dpkg --remove --force-remove-reinstreq linux-image-3.13.0-34-generic
```
It's certain to leave your dpkg database inaccurate (different from your system) - a risk for future failure.

---

### Post by tgalati4 on 2015-03-03
After the dpkg audit (which you should capture) you can use:

```
cd
sudo dpkg --audit > my_list_of_borked_packages.txt

```

Then:

```
sudo apt-get clean
sudo apt-get check
```

This will wipe the cached (downloaded) packages which sometimes trips up *dpkg*.

---

### Post by russ12 on 2015-03-04
I accidentally cleared the logs before I was able to read them, so that route didn't work.  Everything is sorted though,  thanks for the help!

---

### Post by bnmohler on 2015-03-12
dude thank you so much for this post. I had a similar issue as the OP. i purged the 3.13.0.32 and i was able to finish my apt-get update again. had no idea this would be an issue found in running an encrypted lvm. 

thanks again!

---

