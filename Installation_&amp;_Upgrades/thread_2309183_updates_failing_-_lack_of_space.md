---
title: "updates failing - lack of space"
date: 2016-01-08
forum: Installation &amp; Upgrades
---

### Post by HappyAsHellas on 2016-01-08
I am using Ubuntu 14.04lts and everything was going fine until a couple of days ago. I tried to install an update and was told I have too free up more space. I'm not  sure as to why this should be as I have a 500 gig hard drive and only Ubuntu running on it. When I wiped out windows a month or so ago I just let Ubuntu "do it's thing" during installation, and didn't make any partitions myself. The problem seems to be the boot area, so how do I go about resizing this?

---

### Post by matt_symes on 2016-01-08
Hi

> **HappyAsHellas said:**
> I am using Ubuntu 14.04lts and everything was going fine until a couple of days ago. I tried to install an update and was told I have too free up more space. I'm not  sure as to why this should be as I have a 500 gig hard drive and only Ubuntu running on it. When I wiped out windows a month or so ago I just let Ubuntu "do it's thing" during installation, and didn't make any partitions myself. The problem seems to be the boot area, so how do I go about resizing this?

Open a terminal type the two commands below into it.

```

df -h
df -i
```

Copy and paste the output from the terminal into your next post.

I suspect your boot partition is full and you are using LVM. This is a known issue if i am right.

Kind regards

---

### Post by HappyAsHellas on 2016-01-08
```
george@george-W240HU-W250HUQ:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         3.9G  8.0K  3.9G   1% /dev
tmpfs                        790M  1.3M  788M   1% /run
/dev/mapper/ubuntu--vg-root  451G   18G  410G   5% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
none                         5.0M     0  5.0M   0% /run/lock
none                         3.9G  388K  3.9G   1% /run/shm
none                         100M   44K  100M   1% /run/user
/dev/sda1                    236M  218M  6.1M  98% /boot
george@george-W240HU-W250HUQ:~$ df -i
Filesystem                    Inodes  IUsed    IFree IUse% Mounted on
udev                         1007153    505  1006648    1% /dev
tmpfs                        1009921    545  1009376    1% /run
/dev/mapper/ubuntu--vg-root 29990912 422677 29568235    2% /
none                         1009921      2  1009919    1% /sys/fs/cgroup
none                         1009921      4  1009917    1% /run/lock
none                         1009921      8  1009913    1% /run/shm
none                         1009921     27  1009894    1% /run/user
/dev/sda1                      62248    332    61916    1% /boot

```

---

### Post by Dennis N on 2016-01-08
As suspected, your boot partition is the problem. 98% full, only 6.1 mB left. This is where the kernels get installed, and if you don't keep the number of kernels down, you run into trouble.

```
sudo apt-get autoremove 
```

may remove unneeded kernels.

---

### Post by HappyAsHellas on 2016-01-08
Is it safe to run the command, by which I mean could it remove needed kernels?

---

### Post by matt_symes on 2016-01-08
Hi

> **HappyAsHellas said:**
> Is it safe to run the command, by which I mean could it remove needed kernels?

Yes it's safe to run that command as it'll only remove old kernels.

If apt fails, which it will do if you are totally out of space, then old kernels can be removed using dpkg.

In your case it should succeed though, as you have just enough space (6.1M).

```
/dev/sda1 236M 218M **6.1M** 98% /boot
```

Kind regards

---

### Post by howefield on 2016-01-08
> **HappyAsHellas said:**
> Is it safe to run the command, by which I mean could it remove needed kernels?

Yes it safe, it should offer to remove all bar the latest 2 kernels.

> autoremove (and the auto-remove alias since 1.1)
           autoremove is used to remove packages that were automatically installed to satisfy dependencies for other packages and are
           now no longer needed.

You should also get the chance to review what it wants to remove before you confirm or back out, eg

```
hugh@xenial:~$ sudo apt-get autoremove
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  libwpd-0.10-10v5
0 to upgrade, 0 to newly install, 1 to remove and 136 not to upgrade.
After this operation, 114 kB disk space will be freed.
Do you want to continue? [Y/n] 
```

---

### Post by HappyAsHellas on 2016-01-08
Tried running autoremove and am now getting this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 13 not to upgrade.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-extra-3.19.0-43-generic (3.19.0-43.49~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-43-generic /boot/vmlinuz-3.19.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-43-generic /boot/vmlinuz-3.19.0-43-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-43-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.19.0-43-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.19.0-43-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic-lts-vivid:
 linux-image-generic-lts-vivid depends on linux-image-extra-3.19.0-43-generic; however:
  Package linux-image-extra-3.19.0-43-generic is not configured yet.

dpkg: error processing package linux-image-generic-lts-vivid (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-lts-vivid:
 linux-generic-lts-vivid depends on linux-image-generic-lts-vivid (= 3.19.0.43.28); however:
  Package linux-image-generic-lts-vivid is not configured yet.

dpkg: error processing package linux-generic-lts-vivid (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                        E: Sub-process /usr/bin/dpkg returned an error code (1)
george@george-W240HU-W250HUQ:~$
```

---

### Post by matt_symes on 2016-01-08
Hi

Well there you go. Not enough space to run apt-get autoremove. I thought you might have just enough. Seems i was wrong :)

Let's use dpkg to remove the old kernels. This will work.

Open a terminal and type

```
dpkg -l | grep linux-image
``` 

Copy and paste the output from the terminal into your next post.

This will show us what kernels you have installed and then we can remove the old ones for you using dpkg and purging them.

Kind regards

---

### Post by HappyAsHellas on 2016-01-08
This is what I've got:

```
ii  linux-image-3.13.0-24-generic                         3.13.0-24.47                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-68-generic                         3.13.0-68.111                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-71-generic                         3.13.0-71.114                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-73-generic                         3.13.0-73.116                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-74-generic                         3.13.0-74.118                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-42-generic                         3.19.0-42.48~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-43-generic                         3.19.0-43.49~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-68-generic                   3.13.0-68.111                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-71-generic                   3.13.0-71.114                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-73-generic                   3.13.0-73.116                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-74-generic                   3.13.0-74.118                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-42-generic                   3.19.0-42.48~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
iF  linux-image-extra-3.19.0-43-generic                   3.19.0-43.49~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic                                   3.13.0.74.80                                        amd64        Generic Linux kernel image
iU  linux-image-generic-lts-vivid                         3.19.0.43.28                                        amd64        Generic Linux kernel image
```

---

### Post by matt_symes on 2016-01-08
Hi

Copy and paste these commands into the terminal

```
sudo dpkg -P linux-image{,-extra}-3.13.0-{24,68,71,73,74}-generic
```

```
sudo apt-get -f install
```

```
sudo apt-get autoremove
```

You'll need to run the command below every month.

```
sudo apt-get autoremove
```

Kind regards

---

### Post by ian-weisser on 2016-01-08
Ah, good old [bug 1357093]("https://bugs.launchpad.net/bugs/1357093").
A small boot partition is required for your LVM or Encrypted install.SInce this happened after one month, I recommend autoremove every two weeks or so.
Alternately, you can enable the setting in unattended-upgrades that will run autoremove every day. Then you never need worry about it anymore.

---

### Post by HappyAsHellas on 2016-01-08
Thanks for all the help. How do I enable the setting to run this automatically? Tried looking in settings but couldn't see anything obvious.

---

### Post by matt_symes on 2016-01-08
Hi

> **ian-weisser said:**
> Alternately, you can enable the setting in unattended-upgrades that will run autoremove every day. Then you never need worry about it anymore.

That's a fine idea.

> **HappyAsHellas said:**
> Thanks for all the help. How do I enable the setting to run this automatically? Tried looking in settings but couldn't see anything obvious.

*Copy and paste* this into the terminal. Copy and pasting will eliminate typos

```
sudo sed -i 's/^[\/]*\(.*Remove-Unused.*\) "false";/\1 "true";/g' /etc/apt/apt.conf.d/50unattended-upgrades
```

This will enable autoremoval of packages when you upgrade.

BTW: We should also remove any kernel headers associated with the kernel images we removed.

Please post the output of

```
dpkg -l | egrep "linux-headers|linux-image"
```

Kind regards

---

### Post by HappyAsHellas on 2016-01-08
```
ii  linux-headers-3.13.0-24                               3.13.0-24.47                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                       3.13.0-24.47                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-68                               3.13.0-68.111                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-68-generic                       3.13.0-68.111                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-71                               3.13.0-71.114                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-71-generic                       3.13.0-71.114                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-73                               3.13.0-73.116                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-73-generic                       3.13.0-73.116                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-74                               3.13.0-74.118                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-74-generic                       3.13.0-74.118                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-42                               3.19.0-42.48~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-42-generic                       3.19.0-42.48~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-43                               3.19.0-43.49~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-43-generic                       3.19.0-43.49~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.74.80                                        amd64        Generic Linux kernel headers
ii  linux-headers-generic-lts-vivid                       3.19.0.43.28                                        amd64        Generic Linux kernel headers
pi  linux-image-3.13.0-74-generic                         3.13.0-74.118                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-42-generic                         3.19.0-42.48~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-43-generic                         3.19.0-43.49~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
pi  linux-image-extra-3.13.0-74-generic                   3.13.0-74.118                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-42-generic                   3.19.0-42.48~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-43-generic                   3.19.0-43.49~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic                                   3.13.0.74.80                                        amd64        Generic Linux kernel image
ii  linux-image-generic-lts-vivid                         3.19.0.43.28                                        amd64        Generic Linux kernel image

```

---

### Post by matt_symes on 2016-01-08
Hi

Open a terminal and copy and paste this to remove your old header files.

```
sudo dpkg -P linux-headers-3.13.0-{24,68,71,73,74}-generic
```

There's one final kernel to clean up as well. autoremove should take care of it but if we remove it now, then you are up to date.

```
sudo dpkg -P linux-image{,-extra}-3.13.0-74-generic
```

When you have run the commands above, please mark this thread as SOLVED using the thread tools menu under post #1, unless there are any errors, in which case post them back here.

Kind regards

---

### Post by ian-weisser on 2016-01-09
> **HappyAsHellas said:**
> How do I enable the setting to run this automatically?
The setting is in /etc/apt/apt.conf.d/50unattended-upgrades
It won't fix an already-full /boot. It will merely prevent /boot from growing full.

---

### Post by matt_symes on 2016-01-09
Hi

> **ian-weisser said:**
> The setting is in /etc/apt/apt.conf.d/50unattended-upgrades
It won't fix an already-full /boot. It will merely prevent /boot from growing full.

Check out the *sed* command in post #14. That'll enable it with a quick copy and paste into the terminal.

BTW: I didn't realise you were instrumental in that bug report. That's a good job as that bug seems to be biting many people.

Kind regards

---

### Post by HappyAsHellas on 2016-01-22
When trying to upgrade I am getting told that I don't have enough space in boot and to empty the trash and run sudo apt get clean. I have tried this but still have the same problem. I had posted this in an earlier thread, and tried running all the commands from that thread, but still no joy. Why is the boot sector so small if it requires more space? Can I resize it in some way or just wait till the next lts release in April?

---

### Post by howefield on 2016-01-22
Duplicate threads merged.

---

### Post by matt_symes on 2016-01-22
Hi

> **HappyAsHellas said:**
> When trying to upgrade I am getting told that I don't have enough space in boot and to empty the trash and run sudo apt get clean. I have tried this but still have the same problem. I had posted this in an earlier thread, and tried running all the commands from that thread, but still no joy. Why is the boot sector so small if it requires more space? Can I resize it in some way or just wait till the next lts release in April?

Please post the output of

```
df -h
```

Kind regards

---

### Post by HappyAsHellas on 2016-01-22
Filesystem                   Size  Used Avail Use% Mounted on
udev                         3.9G  4.0K  3.9G   1% /dev
tmpfs                        790M  1.3M  788M   1% /run
/dev/mapper/ubuntu--vg-root  451G   17G  411G   4% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
none                         5.0M     0  5.0M   0% /run/lock
none                         3.9G  160K  3.9G   1% /run/shm
none                         100M   44K  100M   1% /run/user
/dev/sda1                    236M  101M  123M  45% /boot

---

### Post by matt_symes on 2016-01-23
Hi

```
/dev/sda1 236M 101M 123M **45%** /boot 
```

Your boot partition is not full.

Please post the output of

```
sudo apt-get install htop
```

Kind regards

---

### Post by HappyAsHellas on 2016-01-23
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  htop
0 to upgrade, 1 to newly install, 0 to remove and 32 not to upgrade.
Need to get 68.0 kB of archives.
After this operation, 188 kB of additional disk space will be used.
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty/universe htop amd64 1.0.2-3 [68.0 kB]
Fetched 68.0 kB in 0s (413 kB/s)
Selecting previously unselected package htop.
(Reading database ... 298661 files and directories currently installed.)
Preparing to unpack .../htop_1.0.2-3_amd64.deb ...
Unpacking htop (1.0.2-3) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up htop (1.0.2-3) ...
```

---

### Post by matt_symes on 2016-01-23
Hi

I don't see anything wrong with your last post as well.

What exactly is wrong with your installation ?

When are you getting the "out of space" error ?

Kind regards

---

### Post by HappyAsHellas on 2016-01-23
his is the error message I get when trying to install

The upgrade needs a total of 133 M free space on disk '/boot'. Please free at least an additional 4,406 k of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

---

### Post by matt_symes on 2016-01-23
Hi

> **HappyAsHellas said:**
> his is the error message I get when trying to install

The upgrade needs a total of 133 M free space on disk '/boot'. Please free at least an additional 4,406 k of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

OK. Please post the output of this command again.

```
dpkg -l | egrep "linux-headers|linux-image"
```

Also did you run that sed command from my post in the last page ?

There was actually a mistake in it that i have fixed. 

Somehow i managed to uncomment the line but forgot to change the false to true. 

I must have been pretty distracted when i posted. 

Anyway i have updated that post and and i'll post the updated command below as well.

```
sudo sed -i 's/^[\/]*\(.*Remove-Unused.*\) "false";/\1 "true";/g' /etc/apt/apt.conf.d/50unattended-upgrades
```

Kind regards

---

### Post by HappyAsHellas on 2016-01-23
Here is the output:

```

ii  linux-headers-3.13.0-24                               3.13.0-24.47                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-68                               3.13.0-68.111                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-71                               3.13.0-71.114                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-73                               3.13.0-73.116                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-74                               3.13.0-74.118                                       all          Header files related to Linux kernel version 3.13.0
pi  linux-headers-3.13.0-74-generic                       3.13.0-74.118                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-42                               3.19.0-42.48~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-42-generic                       3.19.0-42.48~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-43                               3.19.0-43.49~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-43-generic                       3.19.0-43.49~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.74.80                                        amd64        Generic Linux kernel headers
ii  linux-headers-generic-lts-vivid                       3.19.0.43.28                                        amd64        Generic Linux kernel headers
pi  linux-image-3.13.0-74-generic                         3.13.0-74.118                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-42-generic                         3.19.0-42.48~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-43-generic                         3.19.0-43.49~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
pi  linux-image-extra-3.13.0-74-generic                   3.13.0-74.118                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-42-generic                   3.19.0-42.48~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-43-generic                   3.19.0-43.49~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic                                   3.13.0.74.80                                        amd64        Generic Linux kernel image
ii  linux-image-generic-lts-vivid                         3.19.0.43.28                                        amd64        Generic Linux kernel image
```

---

### Post by matt_symes on 2016-01-23
Hi

The kernel linux-image{-extra}-3.13.0-74-generic been marked for purging but is still installed. Let's remove that first

```
sudo dpkg -P linux-image{,-extra}-3.13.0-74-generic linux-image-generic
```

```
sudo apt-get -f install
```

If there are any errors then please post them back here.

Then please run the sed command in my last post.

After that please post the output of

```
grep Remove-Unused /etc/apt/apt.conf.d/50unattended-upgrades
```

After that we can remove some old headers in our next posts.

Kind regards

---

### Post by HappyAsHellas on 2016-01-23
```
dpkg: dependency problems prevent removal of linux-image-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.74.80).

dpkg: error processing package linux-image-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-74-generic:
 linux-image-generic depends on linux-image-3.13.0-74-generic.

dpkg: error processing package linux-image-3.13.0-74-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-extra-3.13.0-74-generic:
 linux-image-generic depends on linux-image-extra-3.13.0-74-generic.

dpkg: error processing package linux-image-extra-3.13.0-74-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-generic
 linux-image-3.13.0-74-generic
 linux-image-extra-3.13.0-74-generic
```

Have to retire now for the evening - will check back tomorrow - thanks for your patience and help.

---

### Post by matt_symes on 2016-01-24
Hi

Alright. Let's try removing the older kernel only.

```
sudo dpkg -P linux-image{,-extra}-3.13.0-74-generic
```

```
sudo apt-get install -f
```

Post back any errors.

Kind regards

---

### Post by HappyAsHellas on 2016-01-24
Still get this error:

dpkg: dependency problems prevent removal of linux-image-3.13.0-74-generic:
 linux-image-generic depends on linux-image-3.13.0-74-generic.

dpkg: error processing package linux-image-3.13.0-74-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-extra-3.13.0-74-generic:
 linux-image-generic depends on linux-image-extra-3.13.0-74-generic.

dpkg: error processing package linux-image-extra-3.13.0-74-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-3.13.0-74-generic
 linux-image-extra-3.13.0-74-generic

---

### Post by matt_symes on 2016-01-24
Hi

You still have the linux-generic-vivid-lts metapackage installed.

Looks like you can't remove the last trusty kernel without working through the dependencies, so copy and paste these commands one after another.

```
sudo dpkg -P linux-generic
```

```
sudo dpkg -P linux-image-generic
```

```
sudo dpkg -P linux-image{,-extra}-3.13.0-74-generic
```

```
sudo apt-get install -f
```

Post back any errors.

If that all works then we'll see in what state your system is in.

Kind regards

---

### Post by HappyAsHellas on 2016-01-24
No errors when I ran the commands this time, so hopefully all is well.

---

### Post by matt_symes on 2016-01-24
Hi

> **HappyAsHellas said:**
> No errors when I ran the commands this time, so hopefully all is well.

Good.

Please post the output of

```
grep Remove-Unused /etc/apt/apt.conf.d/50unattended-upgrades
```

```
dpkg -l | egrep "linux-image|linux-headers"
```

```
df -i
```

```
df -h
```

Kind regards

---

### Post by HappyAsHellas on 2016-01-24
These are the outputs now:

```
george@george-W240HU-W250HUQ:~$ grep Remove-Unused /etc/apt/apt.conf.d/50unattended-upgrades
attended-Upgrade::Remove-Unused-Dependencies "true";
```

```
george@george-W240HU-W250HUQ:~$ dpkg -l | egrep "linux-image|linux-headers"
ii  linux-headers-3.13.0-24                               3.13.0-24.47                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-68                               3.13.0-68.111                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-71                               3.13.0-71.114                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-73                               3.13.0-73.116                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-74                               3.13.0-74.118                                       all          Header files related to Linux kernel version 3.13.0
pi  linux-headers-3.13.0-74-generic                       3.13.0-74.118                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-42                               3.19.0-42.48~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-42-generic                       3.19.0-42.48~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-43                               3.19.0-43.49~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-43-generic                       3.19.0-43.49~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.74.80                                        amd64        Generic Linux kernel headers
ii  linux-headers-generic-lts-vivid                       3.19.0.43.28                                        amd64        Generic Linux kernel headers
ii  linux-image-3.19.0-42-generic                         3.19.0-42.48~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-43-generic                         3.19.0-43.49~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-42-generic                   3.19.0-42.48~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-43-generic                   3.19.0-43.49~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-vivid                         3.19.0.43.28                                        amd64        Generic Linux kernel image
```

```
george@george-W240HU-W250HUQ:~$ df -i
Filesystem                    Inodes  IUsed    IFree IUse% Mounted on
udev                         1007153    503  1006650    1% /dev
tmpfs                        1009921    538  1009383    1% /run
/dev/mapper/ubuntu--vg-root 29990912 342005 29648907    2% /
none                         1009921      2  1009919    1% /sys/fs/cgroup
none                         1009921      4  1009917    1% /run/lock
none                         1009921      7  1009914    1% /run/shm
none                         1009921     25  1009896    1% /run/user
/dev/sda1                      62248    307    61941    1% /boot

```

```
george@george-W240HU-W250HUQ:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         3.9G  4.0K  3.9G   1% /dev
tmpfs                        790M  1.3M  788M   1% /run
/dev/mapper/ubuntu--vg-root  451G   17G  411G   4% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
none                         5.0M     0  5.0M   0% /run/lock
none                         3.9G  156K  3.9G   1% /run/shm
none                         100M   36K  100M   1% /run/user
/dev/sda1                    236M   72M  153M  32% /boot
```

---

### Post by matt_symes on 2016-01-24
Hi

Open a terminal and run these commands.

```
sudo dpkg -P linux-headers-3.13.0-{24,68,71,73}
```

```
sudo dpkg -P linux-headers-3.13.0-74{,-generic}
```

Also, you must have run my original sed command more than once. This has created a slight error that we need to fix. That was my fault for posting a broken sed  command in the first place. We can fix that now.

```
sudo sed -i 's/\(.*Remove-Unused.*\)/Un\1/g' /etc/apt/apt.conf.d/50unattended-upgrades
```

Finally please post the output of

```
grep Remove-Unused /etc/apt/apt.conf.d/50unattended-upgrades
```

Kind regards

---

### Post by HappyAsHellas on 2016-01-24
Output:

```
george@george-W240HU-W250HUQ:~$ grep Remove-Unused /etc/apt/apt.conf.d/50unattended-upgrades
Unattended-Upgrade::Remove-Unused-Dependencies "true";
george@george-W240HU-W250HUQ:~$
```

---

### Post by matt_symes on 2016-01-24
Hi

You should be good to go now.

You have two vivid kernels installed and autoremove is correctly enabled.

If you have any more problems with your package manager then post back.

Kind regards

---

