---
title: "Apt-get -f install -- Vicious Circle"
date: 2013-03-14
forum: Installation &amp; Upgrades
---

### Post by ezphilosophy on 2013-03-14
It has been a long time since I've asked for help, but I'm in dire need now.

Some time ago, I set up a friend's computer with 10.04. He's still running it but somewhere along the way, he started having trouble with his nvidia drivers and seemingly his whole system. Remotely, I've been trying to help him start from scratch and install fresh with 12.10. The problem is that his CD-rom is broken, and his BIOS will not allow him to boot from external media, i.e., usb cd/dvd rom and/or usb flash drives. Space on his system partition was very low but has deleted enough to give him just over a gig. I thought the best solution would be to boot from a local iso file through grub2. However, his system hasn't been updated/upgraded to grub2, he is still using the legacy version. We can't seem to upgrade him because, well, I guess you could say apt-get is (broken?) and apt-get -f install isn't fixing it. We can't remove or add packages until this is resolved. I've listed the commands we've tried and their output.

I would appreciate any help that would allow us to update the computer to grub2 and/or do a fresh install of Ubuntu.

**sudo apt-get -f install**

dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.32-45_2.6.32-45.104_all.deb (--unpack): unable to create /usr/src/linux-headers-2.6.32-45/drivers/cpufreq/Kconfig.dpkg-new' (while processing./usr/src/linux-headers-2.6.32-45/drivers/cpufreq/Kconfig'): No space left on device No apport report written because the error message indicates a disk full error dpkg-deb: subprocess paste killed by signal (Broken pipe) Errors were encountered while processing: /var/cache/apt/archives/linux-headers-2.6.32-45_2.6.32-45.104_all.deb

**sudo dpkg --configure -a**

dpkg: dependency problems prevent configuration of linux-headers-2.6.32-45-generic: linux-headers-2.6.32-45-generic depends on linux-headers-2.6.32-45; however: Package linux-headers-2.6.32-45 is not installed. dpkg: error processing linux-headers-2.6.32-45-generic (--configure): dependency problems - leaving unconfigured dpkg: dependency problems prevent configuration of linux-headers-generic: linux-headers-generic depends on linux-headers-2.6.32-45-generic; however: Package linux-headers-2.6.32-45-generic is not configured yet. dpkg: error processing linux-headers-generic (--configure): dependency problems - leaving unconfigured Errors were encountered while processing: linux-headers-2.6.32-45-generic linux-headers-generic

**sudo dpkg -i --force-overwrite /var/cache/apt/archives/linux-headers-2.6.32-45_2.6.32-45.104_all.deb**

dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.32-45_2.6.32-45.104_all.deb (--install): unable to create /usr/src/linux-headers-2.6.32-45/drivers/cpufreq/Kconfig.dpkg-new' (while processing./usr/src/linux-headers-2.6.32-45/drivers/cpufreq/Kconfig'): No space left on device dpkg-deb: subprocess paste killed by signal (Broken pipe) Errors were encountered while processing: /var/cache/apt/archives/linux-headers-2.6.32-45_2.6.32-45.104_all.deb

**sudo apt-get autoremove**

You might want to run `apt-get -f install' to correct these. The following packages have unmet dependencies: linux-headers-2.6.32-45-generic: Depends: linux-headers-2.6.32-45 but it is not installed E: Unmet dependencies. Try using -f.

---

### Post by schragge on 2013-03-14
> [COLOR=red]No space left on device[/COLOR] The message is pretty clear. Try
```
sudo apt-get clean
``` You probably won't be able to upgrade the whole system at once. Try to clean up as much space on the partition as possible, remove some big applications like LibreOffice that can be reinstalled after the base system is upgraded. Also take a look at [Release Notes for Debian 7.0 (wheezy)](http://www.debian.org/releases/testing/amd64/release-notes/ch-upgrading.en.html#sufficient-space) where this problem gets discussed at some length.

---

### Post by ibjsb4 on 2013-03-14
Also sounds like you should remove some of those old kernels.  Take a look at /boot.

---

### Post by ezphilosophy on 2013-03-15
Thanks for the replies!
Autoclean has already been performed.  There's about 1.3 gig free on the partition, and the updates amount to a couple hundred MB. (Maybe my friend is wrong about this)
I would love to remove some programs and/or kernels, but I can't remove (or add) anything until apt-get is fixed as it won't allow me to do so.  (Hence, the vicious circle)

---

### Post by schragge on 2013-03-15
I guess *sudo apt-get clean* should help somewhat nevertheless. After that try ```
sudo apt-get --reinstall --no-upgrade install [COLOR=#000000]linux-headers-2.6.32-45[/COLOR]
``` to complete installation of the half-installed package. Don't attempt the full dist-upgrade. You will need twice as much space as the total size of all packages to be upgraded.

---

### Post by oldos2er on 2013-03-15
More info on freeing up disk space here: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by ezphilosophy on 2013-03-20
The results from the *sudo apt-get --reinstall --no-upgrade install linux-headers-2.6.32-45* command:
```
The following packages were automatically installed and are no longer required:
  libaccess-bridge-java-jni libaccess-bridge-java
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-headers-2.6.32-45
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
2 not fully installed or removed.
Need to get 10.2MB of archives.
After this operation, 75.9MB of additional disk space will be used.
Get:1 [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) lucid-updates/main linux-headers-2.6.32-45 2.6.32-45.104 [10.2MB]
Fetched 10.2MB in 27s (364kB/s)                                                
(Reading database ... 574550 files and directories currently installed.)
Unpacking linux-headers-2.6.32-45 (from .../linux-headers-2.6.32-45_2.6.32-45.104_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.32-45_2.6.32-45.104_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-2.6.32-45/drivers/parisc/Makefile.dpkg-new' (while processing `./usr/src/linux-headers-2.6.32-45/drivers/parisc/Makefile'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-2.6.32-45_2.6.32-45.104_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

And after autoremove command:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  linux-headers-2.6.32-45-generic: Depends: linux-headers-2.6.32-45 but it is not installed
E: Unmet dependencies. Try using -f.
```

He has about 900 mb free on the system partition.

---

### Post by oldos2er on 2013-03-20
> unable to create `/usr/src/linux-headers-2.6.32-45/drivers/parisc/Makefile.dpkg-new' (while processing `./usr/src/linux-headers-2.6.32-45/drivers/parisc/Makefile'): [COLOR=#ff0000]No space left on device[/COLOR]

Sounds like it's time for a new hard drive.

---

### Post by schragge on 2013-03-21
Check how many linux kernels and related packages have been installed:
```
dpkg -l linux-\*|grep -o '^i.. *[^ ]*'
``` and remove the older packages. You probably won't be able to do this with APT, so use dpkg:
```
sudo dpkg -r linux-{image,headers}-[COLOR=red]2.6.32-36[/COLOR]-generic
```Replace [COLOR=red]2.6.32-36[/COLOR] with appropriate kernel version. You also can try to free up some more space by removing old logs:
```
sudo find /var/log -type f -name '*.[1go]*' -delete
``` The free 900M don't matter if you've run out of file inodes. Check this with
```
df -hi
```

---

