---
title: "Unable to clean/clear old kernels from /boot..."
date: 2019-09-23
forum: Installation &amp; Upgrades
---

### Post by armegeden on 2019-09-23
I was following this thread to clear a full /boot partition.  I'm at the part where I'm trying to:

```
sudo apt-get purge linux-image-x.x.x.x-generic
```

Then I was planning to:

```
sudo update-initramfs -u                          # remakes boot ramdisk
sudo update-grub2                                 # re-creates boot menu
```

Unfortunately I'm unable to purge:

```
root@ubuntu:~$ sudo apt-get purge linux-image-4.4.0-62-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-generic : Depends: linux-image-4.4.0-164-generic but it is not going to be installed or
                                linux-image-unsigned-4.4.0-164-generic but it is not going to be installed
                       Recommends: thermald but it is not going to be installed
 linux-modules-extra-4.4.0-150-generic : Depends: linux-image-4.4.0-150-generic but it is not going to be installed or
                                                  linux-image-unsigned-4.4.0-150-generic but it is not going to be installed
 linux-modules-extra-4.4.0-151-generic : Depends: linux-image-4.4.0-151-generic but it is not going to be installed or
                                                  linux-image-unsigned-4.4.0-151-generic but it is not going to be installed
 linux-modules-extra-4.4.0-164-generic : Depends: linux-image-4.4.0-164-generic but it is not going to be installed or
                                                  linux-image-unsigned-4.4.0-164-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
Of course apt-get -f install returns the full /boot disk error.

Not sure where to go from here, I know I just have a lot of old images to manually delete.

Help?

Thanks for any advice!

---

### Post by #&amp;thj^% on 2019-09-23
What does this report:
```
sudo apt autoremove
```

---

### Post by deadflowr on 2019-09-23
What do
```
ls /boot
df -hT -x squashfs
```
show?

---

### Post by armegeden on 2019-09-23
~$ sudo apt autoremove
[sudo] password for user:
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic : Depends: linux-image-4.4.0-164-generic but it is not installed or
                                linux-image-unsigned-4.4.0-164-generic but it is not installed
                       Recommends: thermald but it is not installed
 linux-modules-extra-4.4.0-150-generic : Depends: linux-image-4.4.0-150-generic but it is not installed or
                                                  linux-image-unsigned-4.4.0-150-generic but it is not installed
 linux-modules-extra-4.4.0-151-generic : Depends: linux-image-4.4.0-151-generic but it is not installed or
                                                  linux-image-unsigned-4.4.0-151-generic but it is not installed
 linux-modules-extra-4.4.0-164-generic : Depends: linux-image-4.4.0-164-generic but it is not installed or
                                                  linux-image-unsigned-4.4.0-164-generic but it is not installed
E: Unmet dependencies. Try using -f.

---

### Post by armegeden on 2019-09-23
> **deadflowr said:**
> What do
```
ls /boot
df -hT -x squashfs
```
show?

here's the ls /boot:

```
~$ ls /boot
abi-4.4.0-130-generic     config-4.4.0-134-generic  config-4.4.0-148-generic      initrd.img-4.4.0-142-generic  retpoline-4.4.0-139-generic   System.map-4.4.0-141-generic  vmlinuz-4.4.0-138-generic
abi-4.4.0-134-generic     config-4.4.0-137-generic  grub                          initrd.img-4.4.0-143-generic  retpoline-4.4.0-141-generic   System.map-4.4.0-142-generic  vmlinuz-4.4.0-139-generic
abi-4.4.0-137-generic     config-4.4.0-138-generic  initrd.img-4.4.0-130-generic  initrd.img-4.4.0-145-generic  retpoline-4.4.0-142-generic   System.map-4.4.0-143-generic  vmlinuz-4.4.0-141-generic
abi-4.4.0-138-generic     config-4.4.0-139-generic  initrd.img-4.4.0-134-generic  lost+found                    System.map-4.4.0-130-generic  System.map-4.4.0-145-generic  vmlinuz-4.4.0-142-generic
abi-4.4.0-139-generic     config-4.4.0-141-generic  initrd.img-4.4.0-137-generic  retpoline-4.4.0-130-generic   System.map-4.4.0-134-generic  System.map-4.4.0-148-generic  vmlinuz-4.4.0-143-generic
abi-4.4.0-141-generic     config-4.4.0-142-generic  initrd.img-4.4.0-138-generic  retpoline-4.4.0-134-generic   System.map-4.4.0-137-generic  vmlinuz-4.4.0-130-generic     vmlinuz-4.4.0-145-generic
abi-4.4.0-142-generic     config-4.4.0-143-generic  initrd.img-4.4.0-139-generic  retpoline-4.4.0-137-generic   System.map-4.4.0-138-generic  vmlinuz-4.4.0-134-generic     vmlinuz-4.4.0-148-generic
config-4.4.0-130-generic  config-4.4.0-145-generic  initrd.img-4.4.0-141-generic  retpoline-4.4.0-138-generic   System.map-4.4.0-139-generic  vmlinuz-4.4.0-137-generic

```

and the other:

```
:~$ df -hT -x squashfs
Filesystem                    Type      Size  Used Avail Use% Mounted on
udev                          devtmpfs  2.0G     0  2.0G   0% /dev
tmpfs                         tmpfs     396M  6.3M  389M   2% /run
/dev/mapper/vali--vg-root ext4       90G   45G   41G  53% /
tmpfs                         tmpfs     2.0G  8.0K  2.0G   1% /dev/shm
tmpfs                         tmpfs     5.0M     0  5.0M   0% /run/lock
tmpfs                         tmpfs     2.0G     0  2.0G   0% /sys/fs/cgroup
/dev/sda1                     ext2      472M  469M     0 100% /boot
//172.16.0.6/m         cifs      4.3T  2.8T  1.5T  66% /mnt/Media
tmpfs                         tmpfs     396M     0  396M   0% /run/user/1000




```

---

### Post by #&amp;thj^% on 2019-09-23
One more Please:
```
sudo apt -f install
```

---

### Post by deadflowr on 2019-09-23
[s]Might require some finessing.
One method is

1) Remove all files related to one of those kernels in the /boot directory
Something like
```
sudo rm *-4.4.0-130-generic
```
this frees some room.

2) Next remove one or two kernels manually
```
sudo apt purge linux-image-4.4.0-134-generic linux-image-4.4.0-137-generic
```
That'll free even more room.

3) Next reinstall the files for that first kernel manually removed
```
sudo apt install --reinstall linux-image-4.4.0-130-generic
```
You reinstall that kernel image so the package management doesn't freak out.

4)
```
sudo apt autoremove --purge
```[/s]

Scratch that.
Looking at the boot folder output some stuff seems off.
Newer kernels are missing files in the listed output
What does 
```
dpkg -l | grep linux-image
```
show?
Best to see how broken things already are before moving forward.

---

### Post by TheFu on 2019-09-23
Ouch. You are stuck.  This problem has been there, 2-3 week, at least.  Like a leaky roof, out of storage errors while patching don't get better over time.

There are some things I'd try, but I have excellent backups, so I can put things back easily.  If you are willing to go to extreme measures, let me know.  Be certain you have everything you want to keep backed up.  It would entail moving some files to make room, but create empty files in /boot/ so APT doesn't know any better.  Then do the **sudo apt-get -f install** to get out of *APT hell*. Then come back and use some aggressive apt-get purge package globbing to remove all but 3 kernels. And lastly, run an autoremove.  If all that works, you can wipe the kernel files that were copied *somewhere else*.  Only move the kernel files that won't be used, for any needed reboots.

Next time around, run **sudo apt autoremove** every 2 weeks or so. This will clean up all but 2-3 kernels.  Under 200MB should be needed in /boot/.

---

### Post by armegeden on 2019-09-23
> **1fallen said:**
> One more Please:
```
sudo apt -f install
```

Sorry, this is long output:

```
~$ sudo apt -f install
[sudo] password for user:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-150 linux-headers-4.4.0-150-generic linux-headers-4.4.0-151 linux-headers-4.4.0-151-generic linux-image-4.4.0-130-generic linux-image-4.4.0-134-generic linux-image-4.4.0-137-generic
  linux-image-4.4.0-138-generic linux-image-4.4.0-139-generic linux-image-4.4.0-141-generic linux-image-4.4.0-142-generic linux-image-4.4.0-143-generic linux-image-4.4.0-150-generic linux-image-4.4.0-151-generic
  linux-image-extra-4.4.0-130-generic linux-image-extra-4.4.0-134-generic linux-image-extra-4.4.0-137-generic linux-image-extra-4.4.0-138-generic linux-image-extra-4.4.0-139-generic
  linux-image-extra-4.4.0-141-generic linux-image-extra-4.4.0-142-generic linux-modules-4.4.0-143-generic linux-modules-4.4.0-150-generic linux-modules-4.4.0-151-generic linux-modules-extra-4.4.0-143-generic
  linux-modules-extra-4.4.0-150-generic linux-modules-extra-4.4.0-151-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-image-4.4.0-150-generic linux-image-4.4.0-151-generic linux-image-4.4.0-164-generic linux-modules-4.4.0-150-generic linux-modules-4.4.0-151-generic linux-modules-4.4.0-164-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following NEW packages will be installed:
  linux-image-4.4.0-150-generic linux-image-4.4.0-151-generic linux-image-4.4.0-164-generic linux-modules-4.4.0-150-generic linux-modules-4.4.0-151-generic linux-modules-4.4.0-164-generic
0 upgraded, 6 newly installed, 0 to remove and 178 not upgraded.
16 not fully installed or removed.
Need to get 56.7 MB of archives.
After this operation, 201 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-modules-4.4.0-164-generic amd64 4.4.0-164.192 [11.9 MB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-4.4.0-164-generic amd64 4.4.0-164.192 [6,935 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-modules-4.4.0-150-generic amd64 4.4.0-150.176 [12.0 MB]
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-4.4.0-150-generic amd64 4.4.0-150.176 [6,928 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-modules-4.4.0-151-generic amd64 4.4.0-151.178 [12.0 MB]
Get:6 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-4.4.0-151-generic amd64 4.4.0-151.178 [6,928 kB]
Fetched 56.7 MB in 8s (7,002 kB/s)
(Reading database ... 213410 files and directories currently installed.)
Preparing to unpack .../linux-modules-4.4.0-164-generic_4.4.0-164.192_amd64.deb ...
Unpacking linux-modules-4.4.0-164-generic (4.4.0-164.192) ...
dpkg: error processing archive /var/cache/apt/archives/linux-modules-4.4.0-164-generic_4.4.0-164.192_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-4.4.0-164-generic' to '/boot/System.map-4.4.0-164-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../linux-image-4.4.0-164-generic_4.4.0-164.192_amd64.deb ...
Unpacking linux-image-4.4.0-164-generic (4.4.0-164.192) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-164-generic_4.4.0-164.192_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.4.0-164-generic' to '/boot/vmlinuz-4.4.0-164-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../linux-modules-4.4.0-150-generic_4.4.0-150.176_amd64.deb ...
Unpacking linux-modules-4.4.0-150-generic (4.4.0-150.176) ...
dpkg: error processing archive /var/cache/apt/archives/linux-modules-4.4.0-150-generic_4.4.0-150.176_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-4.4.0-150-generic' to '/boot/System.map-4.4.0-150-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../linux-image-4.4.0-150-generic_4.4.0-150.176_amd64.deb ...
Unpacking linux-image-4.4.0-150-generic (4.4.0-150.176) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-150-generic_4.4.0-150.176_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.4.0-150-generic' to '/boot/vmlinuz-4.4.0-150-generic.dpkg-new': failed to write (No space left on device)
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../linux-modules-4.4.0-151-generic_4.4.0-151.178_amd64.deb ...
Unpacking linux-modules-4.4.0-151-generic (4.4.0-151.178) ...
dpkg: error processing archive /var/cache/apt/archives/linux-modules-4.4.0-151-generic_4.4.0-151.178_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-4.4.0-151-generic' to '/boot/System.map-4.4.0-151-generic.dpkg-new': failed to write (No space left on device)
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../linux-image-4.4.0-151-generic_4.4.0-151.178_amd64.deb ...
Unpacking linux-image-4.4.0-151-generic (4.4.0-151.178) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-151-generic_4.4.0-151.178_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.4.0-151-generic' to '/boot/vmlinuz-4.4.0-151-generic.dpkg-new': failed to write (No space left on device)
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-modules-4.4.0-164-generic_4.4.0-164.192_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-164-generic_4.4.0-164.192_amd64.deb
 /var/cache/apt/archives/linux-modules-4.4.0-150-generic_4.4.0-150.176_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-150-generic_4.4.0-150.176_amd64.deb
 /var/cache/apt/archives/linux-modules-4.4.0-151-generic_4.4.0-151.178_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-151-generic_4.4.0-151.178_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by #&amp;thj^% on 2019-09-23
TheFu has a solution for you, I have to go to work so I'll leave you in his very capable hands. ;)
Good Luck though.

---

### Post by armegeden on 2019-09-23
> **TheFu said:**
> Ouch. You are stuck.  This problem has been there, 2-3 week, at least.  Like a leaky roof, out of storage errors while patching don't get better over time.

There are some things I'd try, but I have excellent backups, so I can put things back easily.  If you are willing to go to extreme measures, let me know.  Be certain you have everything you want to keep backed up.  It would entail moving some files to make room, but create empty files in /boot/ so APT doesn't know any better.  Then do the **sudo apt-get -f install** to get out of *APT hell*. Then come back and use some aggressive apt-get purge package globbing to remove all but 3 kernels. And lastly, run an autoremove.  If all that works, you can wipe the kernel files that were copied *somewhere else*.  Only move the kernel files that won't be used, for any needed reboots.

Next time around, run **sudo apt autoremove** every 2 weeks or so. This will clean up all but 2-3 kernels.  Under 200MB should be needed in /boot/.


Holy crap.  Okay.  Believe it or not I'm actually relieved it wasn't something easy I'm missing.  Yes, I do suck at autoremove, better believe I'll be better now.

The good news is that this is a VM in ESXi 6.5 and I have a snapshot taken before I started any of this.  So if things get rough, I can always restore the snapshot back to before I started.

I would very, very much appreciate any instructions or advice you would be so kind to give!

---

### Post by TheFu on 2019-09-23
Be very careful, NOT to delete the kernel that is currently booting or any of those support files.

There are 4 kernels and supporting files trying to be installed, but failing because there isn't any space left.  I don't know how to skip those failed installs. We need to make room, get them installed, then remove them. Need to remove the oldest, largest, kernels from /boot/, but that will make APT unhappy. 
 
Any files that are deleted, need to be recreated, so the filenames exist, but they don't need to have any specific contents or size.  I'd use **touch** to create zero-length files.  I've used this technique before for other package that wouldn't install/remove, but never for kernel failures.  I'm hoping this works.

If not, you can always reinstall or clone the datastore and shift everything right, so you can double the size of /boot/.

If this took me over 1 hr to resolve, I would have invoked my restore process, where I can resize any storage areas as needed.  Takes about 45 minutes, at most, to have the system up and working exactly as before.

---

### Post by Impavidus on 2019-09-24
Usually dpkg can still remove old kernel packages even when apt no longer works. The problem can probably be solved with just a few commands. First identify which packages are installed and which kernel is currently running, than use dpkg to remove one or two, then fix apt and use autoremove to remove the other old kernels.

Can you show the output of```
dpkg --list | grep linux-
uname -r
df -h /boot
```

---

### Post by TheFu on 2019-09-24
```
dpkg -l |egrep linux-image | grep '^ii'
```
would be better to show just the *currently installed* linux kernels.  without the 2nd grep, removed kernels will be displayed too. While I avoid using dpkg to install anything, getting information about installed packages is handy.

---

### Post by Impavidus on 2019-09-25
Not showing the rc (removed, remaining configuration) packages is a good idea, but I prefer to see the linux-generic, linux-headers* and linux-modules-*, as well as the partially installed packages, too. The fully removed packages won't show.

You could make it```
dpkg -l | grep linux- | grep -v '^rc'
```

---

### Post by rsteinmetz70112 on 2019-09-26
Have you tried```
 sudo apt autoclean
```? You might even try ```
sudo apt clean
```
I don't see that mentioned. There may be a lot of trash hanging around from old upgrades that autoclean or clean can clear out.
The space problem seems to be in```
 /var/cache/apt/archives/
```

Also a ```
df -k
``` might show which files systems are full and give some insight into your setup.

Looking at the autoremove package list. Why can't he just remove the 5 oldest kernel versions - 4.4.4.0-130, 4.4.4.0-134, 4.4.4.0-137, 4.4.4.0-138, and 4.4.4.0-139?
I'm asking not suggesting that but seeing how many kernel versions are installed it seems highly unlikely any that old are actually being used.
I'm hoping someone can enlighten me.

---

### Post by Impavidus on 2019-09-26
> **rsteinmetz70112 said:**
> 
Looking at the autoremove package list. Why can't he just remove the 5 oldest kernel versions - 4.4.4.0-130, 4.4.4.0-134, 4.4.4.0-137, 4.4.4.0-138, and 4.4.4.0-139?
I'm asking not suggesting that but seeing how many kernel versions are installed it seems highly unlikely any that old are actually being used.
I'm hoping someone can enlighten me.
The problem is the /boot partition, which is full. Systems with a separate /boot partition often suffer from this problem. The solution is indeed to remove some of the older kernels, but unfortunately the package management is now in an inconsistent state. The metapackage (linux-image or linux-image-generic or something like that) that pulls in the next kernel package (linux-image-w.x.y-z-generic) has been upgraded, but installation of the new kernel package has failed because of lacking space. Now apt first wants to make the package system consistent by completing installation of the new kernel package before it's willing to do anything else, like removing old kernel packages, but that can't be done before those old kernel packages have been removed. So you have to use lower level tools to get those old kernel packages removed.

---

### Post by rsteinmetz70112 on 2019-09-26
So why can't those files in /boot simply be deleted? It will create an additional inconsistency which, given some space to work apt might be able to handle. 

Of course the packages might be able to be removed using dokg, which is what apt mostly uses to remove packages, but dpkg does a lot less checking, which in this case might be good. You could try something like ```
dpkg -r linux-image-extra-4.4.0-130-generic
dpkg -r linux-image-4.4.0-130-generic 
```
Then work your way through the packages autoremove wants to remove.Until you get enough space in boot to run autoremove.
Based on the message above it looks like you will need something like 200 megabytes.
```
After this operation, 201 MB of additional disk space will be used.
```

According to the code posted earlier the packages you want to remove would be:
> linux-headers-4.4.0-150 
linux-headers-4.4.0-150-generic 
linux-headers-4.4.0-151 
linux-headers-4.4.0-151-generic 
linux-image-4.4.0-130-generic 
linux-image-4.4.0-134-generic 
linux-image-4.4.0-137-generic
linux-image-4.4.0-138-generic 
linux-image-4.4.0-139-generic 
linux-image-4.4.0-141-generic 
linux-image-4.4.0-142-generic 
linux-image-4.4.0-143-generic 
linux-image-4.4.0-150-generic 
linux-image-4.4.0-151-generic
linux-image-extra-4.4.0-130-generic 
linux-image-extra-4.4.0-134-generic 
linux-image-extra-4.4.0-137-generic 
linux-image-extra-4.4.0-138-generic 
linux-image-extra-4.4.0-139-generic
linux-image-extra-4.4.0-141-generic 
linux-image-extra-4.4.0-142-generic 
linux-modules-4.4.0-143-generic 
linux-modules-4.4.0-150-generic 
linux-modules-4.4.0-151-generic 
linux-modules-extra-4.4.0-143-generic
linux-modules-extra-4.4.0-150-generic 
linux-modules-extra-4.4.0-151-generic

I noticed that all of the same packages are not installed for every kernel version.

I also noticed that a lot of packages have not been updated:

```
0 upgraded, 
6 newly installed, 
0 to remove and 
**178 not upgraded.**
16 not fully installed or removed.
```

---

### Post by Impavidus on 2019-09-26
> **rsteinmetz70112 said:**
> So why can't those files in /boot simply be deleted? It will create an additional inconsistency which, given some space to work apt might be able to handle. 

Of course the packages might be able to be removed using dokg, which is what apt mostly uses to remove packages, but dpkg does a lot less checking, which in this case might be good. You could try something like ...

Exactly, that's the plan. And as dpkg does less checking, we have to do that ourselves. That's why I first want a list of all installed and partially installed kernels and the currently running version. The list of files in /boot may give false information in case of partially installed packages and I don't want to create even more inconsistencies by manually removing files, which could confuse dpkg when it tries to remove a package that's not properly installed, when package management says it's fully installed. The removal script may return an error, which can only be solved by reinstalling the package, then removing it again, when there's no room for that.

So let's wait until OP reports back.

---

### Post by rsteinmetz70112 on 2019-09-27
What kernel is normally booting? ```
# uname -r
```
Anything older than that should be relatively safe to remove.
If you remove those older kernels with dpkg it shouldn't cause any real problems. I'd start with the oldest first and work my way forward until you have enough space in  /boot. 
I have seen situations where removing the kernel does not update /boot even using more sophisticated tools like synaptic. In that case you should try to remove them with ```
# update-initramfs -d -k <Kernel version number>
# example:
# update-initramfs -d -k 4.4.0-130
``` If that fails you will need need to rm the files manually.
The update-initramfs command doesn't remove all of the files in /boot related to a specific kernel. Those have to be removed manually.

Typically each kernel installed has at least the following files in /boot:

> abi-<kernel number>
config-<kernel number>
initrd-<kernel number>
System.map-<kernel number>
vmlinuz-<kernel number>

On my machine each of these sets of files takes up around 50 megabytes so you would likely would need to remove 5 sets to get enough space according to the information previously posted. That would be 4.4.0-130, 4.4.0-134, 4.4.0-137, 4.4.0-138, and 4.4.0-139. It is possible there kernels aren't even still installed.

You can probably remove these older files and still boot as long as you don't try to boot that kernel but it's highly not recommended. In any event as long as the kernel files are installed these files will probably get recreated.

Once you get enough space you can try```
$ sudo -i
# apt autoremove
# apt autoclean
```or  ```
$ sudo apt install -f 
$ sudo dpg --configure -a
$ sudo apt autoremove
$ sudo apt autoclean
``` either should be able to fix it.

After that I suggest you run:

```
# update-initramfs -u all
# update-grub
``` Although the apt install will typically update this stuff. 
Then make sure everything is working properly

---

### Post by armegeden on 2019-10-07
> **Impavidus said:**
> Exactly, that's the plan. And as dpkg does less checking, we have to do that ourselves. That's why I first want a list of all installed and partially installed kernels and the currently running version. The list of files in /boot may give false information in case of partially installed packages and I don't want to create even more inconsistencies by manually removing files, which could confuse dpkg when it tries to remove a package that's not properly installed, when package management says it's fully installed. The removal script may return an error, which can only be solved by reinstalling the package, then removing it again, when there's no room for that.

So let's wait until OP reports back.

I sincerely apologize to all for the delay.  I travel for work and finally have some downtime to resume this, and wow has there been some discussion.  To be honest I'm not quite sure who/where to follow, so I'll try to start answering some questions on output:


```

usr@sys:~$ dpkg --list | grep linux-
ii  linux-base                            4.5ubuntu1~16.04.1                         all          Linux image base package
ii  linux-firmware                        1.157.21                                   all          Firmware for Linux kernel drivers
iU  linux-generic                         4.4.0.164.172                              amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-148               4.4.0-148.174                              all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-148-generic       4.4.0-148.174                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
iU  linux-headers-4.4.0-150               4.4.0-150.176                              all          Header files related to Linux kernel version 4.4.0
iU  linux-headers-4.4.0-150-generic       4.4.0-150.176                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
iU  linux-headers-4.4.0-151               4.4.0-151.178                              all          Header files related to Linux kernel version 4.4.0
iU  linux-headers-4.4.0-151-generic       4.4.0-151.178                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
iU  linux-headers-4.4.0-164               4.4.0-164.192                              all          Header files related to Linux kernel version 4.4.0
iU  linux-headers-4.4.0-164-generic       4.4.0-164.192                              amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
iU  linux-headers-generic                 4.4.0.164.172                              amd64        Generic Linux kernel headers
rc  linux-image-4.4.0-101-generic         4.4.0-101.124                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-103-generic         4.4.0-103.126                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-104-generic         4.4.0-104.127                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-108-generic         4.4.0-108.131                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-109-generic         4.4.0-109.132                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-112-generic         4.4.0-112.135                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-116-generic         4.4.0-116.140                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-119-generic         4.4.0-119.143                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-121-generic         4.4.0-121.145                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-124-generic         4.4.0-124.148                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-127-generic         4.4.0-127.153                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-128-generic         4.4.0-128.154                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-130-generic         4.4.0-130.156                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-133-generic         4.4.0-133.159                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-134-generic         4.4.0-134.160                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-137-generic         4.4.0-137.163                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-138-generic         4.4.0-138.164                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-139-generic         4.4.0-139.165                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-141-generic         4.4.0-141.167                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-142-generic         4.4.0-142.168                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-143-generic         4.4.0-143.169                              amd64        Signed kernel image generic
ii  linux-image-4.4.0-145-generic         4.4.0-145.171                              amd64        Signed kernel image generic
iF  linux-image-4.4.0-148-generic         4.4.0-148.174                              amd64        Signed kernel image generic
rc  linux-image-4.4.0-62-generic          4.4.0-62.83                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-72-generic          4.4.0-72.93                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-75-generic          4.4.0-75.96                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-77-generic          4.4.0-77.98                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-78-generic          4.4.0-78.99                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-79-generic          4.4.0-79.100                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-81-generic          4.4.0-81.104                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-83-generic          4.4.0-83.106                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-87-generic          4.4.0-87.110                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-89-generic          4.4.0-89.112                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-91-generic          4.4.0-91.114                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-92-generic          4.4.0-92.115                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-93-generic          4.4.0-93.116                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-96-generic          4.4.0-96.119                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-97-generic          4.4.0-97.120                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-98-generic          4.4.0-98.121                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-101-generic   4.4.0-101.124                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-103-generic   4.4.0-103.126                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-104-generic   4.4.0-104.127                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-108-generic   4.4.0-108.131                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-109-generic   4.4.0-109.132                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-112-generic   4.4.0-112.135                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-116-generic   4.4.0-116.140                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-119-generic   4.4.0-119.143                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-121-generic   4.4.0-121.145                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-124-generic   4.4.0-124.148                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-127-generic   4.4.0-127.153                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-128-generic   4.4.0-128.154                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-130-generic   4.4.0-130.156                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-133-generic   4.4.0-133.159                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-134-generic   4.4.0-134.160                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-137-generic   4.4.0-137.163                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-138-generic   4.4.0-138.164                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-139-generic   4.4.0-139.165                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-141-generic   4.4.0-141.167                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-142-generic   4.4.0-142.168                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-62-generic    4.4.0-62.83                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-72-generic    4.4.0-72.93                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-75-generic    4.4.0-75.96                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-77-generic    4.4.0-77.98                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-78-generic    4.4.0-78.99                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-79-generic    4.4.0-79.100                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-81-generic    4.4.0-81.104                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-83-generic    4.4.0-83.106                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-87-generic    4.4.0-87.110                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-89-generic    4.4.0-89.112                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-91-generic    4.4.0-91.114                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-92-generic    4.4.0-92.115                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-93-generic    4.4.0-93.116                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-96-generic    4.4.0-96.119                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-97-generic    4.4.0-97.120                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-98-generic    4.4.0-98.121                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                   4.4.0.164.172                              amd64        Generic Linux kernel image
ii  linux-modules-4.4.0-143-generic       4.4.0-143.169                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-modules-4.4.0-145-generic       4.4.0-145.171                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-modules-4.4.0-148-generic       4.4.0-148.174                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.4.0-143-generic 4.4.0-143.169                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.4.0-145-generic 4.4.0-145.171                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.4.0-148-generic 4.4.0-148.174                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-modules-extra-4.4.0-150-generic 4.4.0-150.176                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-modules-extra-4.4.0-151-generic 4.4.0-151.178                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-modules-extra-4.4.0-164-generic 4.4.0-164.192                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP


```

And:

```
usr@sys:~$ uname -r
4.4.0-145-generic

```

And:

```
usr@sys:~$ df -h /boot
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       472M  469M     0 100% /boot

```

And:
```
usr@sys:~$ dpkg -l |egrep linux-image | grep '^ii'
ii  linux-image-4.4.0-130-generic         4.4.0-130.156                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-134-generic         4.4.0-134.160                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-137-generic         4.4.0-137.163                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-138-generic         4.4.0-138.164                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-139-generic         4.4.0-139.165                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-141-generic         4.4.0-141.167                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-142-generic         4.4.0-142.168                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-143-generic         4.4.0-143.169                              amd64        Signed kernel image generic
ii  linux-image-4.4.0-145-generic         4.4.0-145.171                              amd64        Signed kernel image generic
ii  linux-image-extra-4.4.0-130-generic   4.4.0-130.156                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-134-generic   4.4.0-134.160                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-137-generic   4.4.0-137.163                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-138-generic   4.4.0-138.164                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-139-generic   4.4.0-139.165                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-141-generic   4.4.0-141.167                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-142-generic   4.4.0-142.168                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP

```

Did I miss any requests for output? 

Should I start following rsteinmetz70112's instructions?

Thank you all so much for any time you've given.  This is turning out to be a mess!

---

### Post by Impavidus on 2019-10-07
Now try to remove some old kernels:```
sudo dpkg --purge linux-image-4.4.0-130-generic linux-image-extra-4.4.0-130-generic
sudo dpkg --purge linux-image-4.4.0-134-generic linux-image-extra-4.4.0-134-generic
sudo dpkg --purge linux-image-4.4.0-137-generic linux-image-extra-4.4.0-137-generic
sudo dpkg --purge linux-image-4.4.0-138-generic linux-image-extra-4.4.0-138-generic
sudo dpkg --purge linux-image-4.4.0-139-generic linux-image-extra-4.4.0-139-generic
```Does that work? It usually works. If not, we need even lower level tools.

---

### Post by armegeden on 2019-10-07
> **Impavidus said:**
> Now try to remove some old kernels:```
sudo dpkg --purge linux-image-4.4.0-130-generic linux-image-extra-4.4.0-130-generic
sudo dpkg --purge linux-image-4.4.0-134-generic linux-image-extra-4.4.0-134-generic
sudo dpkg --purge linux-image-4.4.0-137-generic linux-image-extra-4.4.0-137-generic
sudo dpkg --purge linux-image-4.4.0-138-generic linux-image-extra-4.4.0-138-generic
sudo dpkg --purge linux-image-4.4.0-139-generic linux-image-extra-4.4.0-139-generic
```Does that work? It usually works. If not, we need even lower level tools.

Output:

```

susr@sys:~$ sudo dpkg --purge linux-image-4.4.0-130-generic linux-image-extra-4.4.0-130-generic
[sudo] password for usr: 
(Reading database ... 213420 files and directories currently installed.)
Removing linux-image-extra-4.4.0-130-generic (4.4.0-130.156) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-130-generic /boot/vmlinuz-4.4.0-130-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-130-generic /boot/vmlinuz-4.4.0-130-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-130-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-130-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-130-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-130-generic (4.4.0-130.156) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-130-generic /boot/vmlinuz-4.4.0-130-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-130-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-130-generic /boot/vmlinuz-4.4.0-130-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-148-generic
Found linux image: /boot/vmlinuz-4.4.0-145-generic
Found initrd image: /boot/initrd.img-4.4.0-145-generic
Found linux image: /boot/vmlinuz-4.4.0-143-generic
Found initrd image: /boot/initrd.img-4.4.0-143-generic
Found linux image: /boot/vmlinuz-4.4.0-142-generic
Found initrd image: /boot/initrd.img-4.4.0-142-generic
Found linux image: /boot/vmlinuz-4.4.0-141-generic
Found initrd image: /boot/initrd.img-4.4.0-141-generic
Found linux image: /boot/vmlinuz-4.4.0-139-generic
Found initrd image: /boot/initrd.img-4.4.0-139-generic
Found linux image: /boot/vmlinuz-4.4.0-138-generic
Found initrd image: /boot/initrd.img-4.4.0-138-generic
Found linux image: /boot/vmlinuz-4.4.0-137-generic
Found initrd image: /boot/initrd.img-4.4.0-137-generic
Found linux image: /boot/vmlinuz-4.4.0-134-generic
Found initrd image: /boot/initrd.img-4.4.0-134-generic
done
Purging configuration files for linux-image-4.4.0-130-generic (4.4.0-130.156) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-130-generic /boot/vmlinuz-4.4.0-130-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-130-generic /boot/vmlinuz-4.4.0-130-generic
Errors were encountered while processing:
 linux-image-extra-4.4.0-130-generic

```

And the last one:

```
[COLOR=#2fb41d]user@sys[/COLOR]:~$ sudo dpkg --purge linux-image-4.4.0-139-generic linux-image-extra-4.4.0-139-generic
(Reading database ... 190936 files and directories currently installed.)
Removing linux-image-extra-4.4.0-139-generic (4.4.0-139.165) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-139-generic /boot/vmlinuz-4.4.0-139-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-139-generic /boot/vmlinuz-4.4.0-139-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-139-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-139-generic /boot/vmlinuz-4.4.0-139-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-139-generic /boot/vmlinuz-4.4.0-139-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-139-generic /boot/vmlinuz-4.4.0-139-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-148-generic
Found linux image: /boot/vmlinuz-4.4.0-145-generic
Found initrd image: /boot/initrd.img-4.4.0-145-generic
Found linux image: /boot/vmlinuz-4.4.0-143-generic
Found initrd image: /boot/initrd.img-4.4.0-143-generic
Found linux image: /boot/vmlinuz-4.4.0-142-generic
Found initrd image: /boot/initrd.img-4.4.0-142-generic
Found linux image: /boot/vmlinuz-4.4.0-141-generic
Found initrd image: /boot/initrd.img-4.4.0-141-generic
Found linux image: /boot/vmlinuz-4.4.0-139-generic
Found initrd image: /boot/initrd.img-4.4.0-139-generic
done
Purging configuration files for linux-image-extra-4.4.0-139-generic (4.4.0-139.165) ...
Removing linux-image-4.4.0-139-generic (4.4.0-139.165) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-139-generic /boot/vmlinuz-4.4.0-139-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-139-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-139-generic /boot/vmlinuz-4.4.0-139-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-148-generic
Found linux image: /boot/vmlinuz-4.4.0-145-generic
Found initrd image: /boot/initrd.img-4.4.0-145-generic
Found linux image: /boot/vmlinuz-4.4.0-143-generic
Found initrd image: /boot/initrd.img-4.4.0-143-generic
Found linux image: /boot/vmlinuz-4.4.0-142-generic
Found initrd image: /boot/initrd.img-4.4.0-142-generic
Found linux image: /boot/vmlinuz-4.4.0-141-generic
Found initrd image: /boot/initrd.img-4.4.0-141-generic
done
Purging configuration files for linux-image-4.4.0-139-generic (4.4.0-139.165) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-139-generic /boot/vmlinuz-4.4.0-139-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-139-generic /boot/vmlinuz-4.4.0-139-generic

```

Same basic output for all the lines you recommended.  Should I continue with 141 & 142?  Or should I try updating/upgrading like normal?

Thanks again!

---

### Post by armegeden on 2019-10-07
> **Impavidus said:**
> Now try to remove some old kernels:```
sudo dpkg --purge linux-image-4.4.0-130-generic linux-image-extra-4.4.0-130-generic
sudo dpkg --purge linux-image-4.4.0-134-generic linux-image-extra-4.4.0-134-generic
sudo dpkg --purge linux-image-4.4.0-137-generic linux-image-extra-4.4.0-137-generic
sudo dpkg --purge linux-image-4.4.0-138-generic linux-image-extra-4.4.0-138-generic
sudo dpkg --purge linux-image-4.4.0-139-generic linux-image-extra-4.4.0-139-generic
```Does that work? It usually works. If not, we need even lower level tools.


It looks like I'm good to go! 

After doing an 'apt-get -f install' followed by a couple update/upgrades and finally autoremoves, it looks like I'm all up to date and have ~280MB free on /boot!

Finally!

Thank you all so much for all the help.  I'll be sure to keep 'autoremove' in my normal maintenance from now on.  Sheesh.

Thank you again, so much.

---

### Post by Impavidus on 2019-10-07
Good.

Could you mark this thread as solved? Thread tools -> mark as solved.

---

### Post by rsteinmetz70112 on 2019-10-07
Adding to this thread. I've done an investigation and determined that if the kernel version files are not loaded the related files in /boot can simply be deleted.
I used Synaptic to search for packages containing the kernel number like 4.4.0-130, but there are other ways to check. If the packages aren't present the files in boot can simply be deleted.

---

