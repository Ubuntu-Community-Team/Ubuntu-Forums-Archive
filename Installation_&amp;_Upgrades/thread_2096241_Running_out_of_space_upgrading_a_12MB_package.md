---
title: "Running out of space upgrading a 12MB package?"
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by supremedalek on 2012-12-19
Let's say I have an 11.10 install with a disk layout that kinda looks like this:

```
root@ubuntu2:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             1.9G  1.1G  734M  60% /
udev                  2.0G   12K  2.0G   1% /dev
tmpfs                 512M  8.0K  512M   1% /tmp
tmpfs                 793M  288K  793M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  2.0G     0  2.0G   0% /run/shm
/dev/mapper/ubuntu_vg0-home
                      2.0G   69M  1.9G   4% /home
/dev/sda1             472M  156M  292M  35% /boot
/dev/mapper/ubuntu_vg0-usr
                      2.0G  864M  1.1G  46% /usr
/dev/mapper/ubuntu_vg0-var
                      2.0G 1016M  898M  54% /var
/dev/mapper/export   1007M   85M  872M   9% /export
root@ubuntu2:~#
```

in which I need to upgrade a package (linux-headers-server in this case). During the package upgrade process I get the following messages:

```
Fetched 12.3 MB in 1s (11.2 MB/s)          
Selecting previously deselected package linux-headers-3.0.0-28.
(Reading database ... 152680 files and directories currently installed.)
Unpacking linux-headers-3.0.0-28 (from .../linux-headers-3.0.0-28_3.0.0-28.45_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.0.0-28_3.0.0-28.45_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.0.0-28/arch/sh/include/asm/unistd_64.h.dpkg-new' (while processing `./usr/src/linux-headers-3.0.0-28/arch/sh/include/asm/unistd_64.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Selecting previously deselected package linux-headers-3.0.0-28-server.
Unpacking linux-headers-3.0.0-28-server (from .../linux-headers-3.0.0-28-server_3.0.0-28.45_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.0.0-28-server_3.0.0-28.45_amd64.deb (--unpack):
 error creating symbolic link `./usr/src/linux-headers-3.0.0-28-server/include/linux/timb_gpio.h': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              Preparing to replace linux-headers-server 3.0.0.27.31 (using .../linux-headers-server_3.0.0.28.32_amd64.deb) ...
Unpacking replacement linux-headers-server ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.0.0-28_3.0.0-28.45_all.deb
 /var/cache/apt/archives/linux-headers-3.0.0-28-server_3.0.0-28.45_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Why is it claiming I have no space? I am not going to say the space I allocated for this install is massive, but I think that 12MB should not break the bank.

---

### Post by snowpine on 2012-12-19
What do you mean by "kinda looks like this" exactly? Are those the real accurate numbers or not??

---

### Post by oldfred on 2012-12-19
You only have 472MB for /boot which is where the kernel & grub files go. Actually that is fairly large, but have you housecleaned any kernels or accumulated many?

Determine your current kernel:
 uname -a
 uname -r
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
 cd /boot
ls vmlinuz*
sudo apt-get remove linux-image-[version]-generic linux-image-[version]-generic

    For all the versions you may want to erase, keep at least two or three kernel images, the one you are using and one or two more.

       Other HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes dependencies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does as upgrade only does existing packages, this adds new 
sudo apt-get dist-upgrade  #updates dependencies
       #dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a

            # empty trash
# remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

---

### Post by supremedalek on 2012-12-19
> **oldfred said:**
> You only have 472MB for /boot which is where the kernel & grub files go. Actually that is fairly large, but have you housecleaned any kernels or accumulated many?

I found that ubuntu and centos would create IMHO rather small boot partitions (256 and 200MB respectively), which would cause it to be filled depending on what extra stuff I wanted during boot or if I was being too lazy. So I doubled it (ok I was bitten by the 1000 vs 1024 reporting issue) and called it good; when nagios tells me it is more than half full I then have plenty of time to do some housecleaning.

> **oldfred said:**
> Determine your current kernel:
 uname -a
 uname -r
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
 cd /boot
ls vmlinuz*
sudo apt-get remove linux-image-[version]-generic linux-image-[version]-generic

    For all the versions you may want to erase, keep at least two or three kernel images, the one you are using and one or two more.

I am afraid it is a bit more complicated than what we originally thought:

```
root@ubuntu2:~# uname -a
Linux ubuntu2 3.0.0-26-server #42-Ubuntu SMP Wed Sep 5 08:55:42 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
root@ubuntu2:~# uname -r
3.0.0-26-server
root@ubuntu2:~# ls /boot/vmlinuz-3.0.0-*
/boot/vmlinuz-3.0.0-12-server  /boot/vmlinuz-3.0.0-24-server
/boot/vmlinuz-3.0.0-14-server  /boot/vmlinuz-3.0.0-26-server
/boot/vmlinuz-3.0.0-19-server  /boot/vmlinuz-3.0.0-27-server
/boot/vmlinuz-3.0.0-23-server
root@ubuntu2:~# apt-get remove linux-image-3.0.0-14-generic linux-image-3.0.0-14-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-image-3.0.0-14-generic is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-server : Depends: linux-headers-3.0.0-28-server but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@ubuntu2:~# 
```

> **oldfred said:**
>        Other HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes dependencies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does as upgrade only does existing packages, this adds new 
sudo apt-get dist-upgrade  #updates dependencies
       #dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a

            # empty trash
# remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

I think other issues need to be solved first:
```
root@ubuntu2:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-server : Depends: linux-headers-3.0.0-28-server but it is not installed
E: Unmet dependencies. Try using -f.
root@ubuntu2:~# 
```

BTW, I did try to record the disk usae (just a script around df) as "apt-get -f install" was run, but either the sampling speed (1s) was not fast enough or the amount of disk used did not increase that much. Which leads to: why should it increase a lot? I mean, where is it unpacking the .deb files in the step
```
dpkg: error processing /var/cache/apt/archives/linux-headers-3.0.0-28_3.0.0-28.45_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.0.0-28/arch/sh/include/asm/unistd_64.h.dpkg-new' (while processing `./usr/src/linux-headers-3.0.0-28/arch/sh/include/asm/unistd_64.h'): No space left on device
No apport report written because the error message indicates a disk full error
   dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)

```
And how much space should it actually need to do so?

---

### Post by oldfred on 2012-12-19
It looks like you are running -26, but have -27 installed and it wants to upgrade to -28?
Then I might only uninstall -24.
With only 3 kernels you should have room, is some other partition then have issues? None looked full, but you do need some working room.


Did you have a typo in your remove command as you tried to remove -14?

---

### Post by supremedalek on 2012-12-19
You are right; I probably should have run 
```
apt-get remove linux-image-3.0.0-14-server linux-image-3.0.0-14-server
```
but it is still barking about 3.0.0-28. Since I am running right now -26, is there a way I can tell it to get rid of -28 so I can deal with the rest?

About the working room, how much do I actually need? Yes, I can throw another 20GB at the problem but that does not solve it. After all, why would I need more disk space than I have? Why do you think it is not enough? What is the criteria? 

I am really trying to understand what is going on here.

---

### Post by oldfred on 2012-12-19
Is this a server install?

If this is what you have installed, then it is what you should remove. I think the commands I posted were more for Desktops.

       sudo apt-get purge vmlinuz-3.0.0-12-server
I used remove before but purge is probaly more correct, see man apt-get

I am only familiar with Desktop installs where the only extra partition may be /home. I do not know best or any reasonable allocation of space to the various system partitions. Last time I dealt with all those partitions was an install of Redhat 5 about 12 years ago.

More for Desktops:
       Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

