---
title: "Freeing space on /boot partition"
date: 2017-06-12
forum: Installation &amp; Upgrades
---

### Post by jackwhitaker3 on 2017-06-12
Hi, I'm running Ubuntu Studio and trying to run software update fails as I have almost run out of space on my boot partition.

```
homer@homer-Precision-3510:~$ df -h
Filesystem                           Size  Used Avail Use% Mounted on
udev                                 3.9G     0  3.9G   0% /dev
tmpfs                                788M  9.7M  778M   2% /run
/dev/mapper/ubuntu--studio--vg-root  226G   56G  160G  26% /
tmpfs                                3.9G  208M  3.7G   6% /dev/shm
tmpfs                                5.0M  4.0K  5.0M   1% /run/lock
tmpfs                                3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/nvme0n1p2                       473M  470M     0 100% /boot
/dev/nvme0n1p1                       511M  3.6M  508M   1% /boot/efi
tmpfs                                788M   40K  787M   1% /run/user/1000
/home/homer/.Private                 226G   56G  160G  26% /home/homer
homer@homer-Precision-3510:~$ 


```

So I followed instructions here [https://www.cyberciti.biz/faq/proper-way-to-remove-old-linux-kernels/](https://www.cyberciti.biz/faq/proper-way-to-remove-old-linux-kernels/) to try and free up space:

```
homer@homer-Precision-3510:~$ uname -r
4.4.0-72-lowlatency

```
```
homer@homer-Precision-3510:~$ dpkg --list 'linux-image*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version            Architecture       Description
+++-===========================-==================-==================-============================================================
un  linux-image                 <none>             <none>             (no description available)
ii  linux-image-4.4.0-31-lowlat 4.4.0-31.50        amd64              Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-62-lowlat 4.4.0-62.83        amd64              Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-63-lowlat 4.4.0-63.84        amd64              Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-64-lowlat 4.4.0-64.85        amd64              Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-65-lowlat 4.4.0-65.86        amd64              Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-66-lowlat 4.4.0-66.87        amd64              Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-70-lowlat 4.4.0-70.91        amd64              Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-71-lowlat 4.4.0-71.92        amd64              Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-72-lowlat 4.4.0-72.93        amd64              Linux kernel image for version 4.4.0 on 64 bit x86 SMP
in  linux-image-4.4.0-75-lowlat <none>             amd64              (no description available)
in  linux-image-4.4.0-79-lowlat <none>             amd64              (no description available)
iU  linux-image-lowlatency      4.4.0.79.85        amd64              lowlatency Linux kernel image



```

But asking it to remove what appear to be old kernels isn't working:

```
homer@homer-Precision-3510:~$ sudo apt-get remove linux-image-4.4.0-31-lowlat
[sudo] password for homer: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-image-4.4.0-31-lowlatency' for regex 'linux-image-4.4.0-31-lowlat'
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-image-lowlatency : Depends: linux-image-4.4.0-79-lowlatency but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

```
 homer@homer-Precision-3510:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-31 linux-headers-4.4.0-31-lowlatency linux-headers-4.4.0-62 linux-headers-4.4.0-62-lowlatency
  linux-headers-4.4.0-63 linux-headers-4.4.0-63-lowlatency linux-headers-4.4.0-64 linux-headers-4.4.0-64-lowlatency
  linux-headers-4.4.0-65 linux-headers-4.4.0-65-lowlatency linux-headers-4.4.0-66 linux-headers-4.4.0-66-lowlatency
  linux-headers-4.4.0-70 linux-headers-4.4.0-70-lowlatency linux-headers-4.4.0-75 linux-headers-4.4.0-75-lowlatency
  linux-image-4.4.0-31-lowlatency linux-image-4.4.0-62-lowlatency linux-image-4.4.0-63-lowlatency linux-image-4.4.0-64-lowlatency
  linux-image-4.4.0-65-lowlatency linux-image-4.4.0-66-lowlatency linux-image-4.4.0-70-lowlatency
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-image-4.4.0-79-lowlatency
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following NEW packages will be installed
  linux-image-4.4.0-79-lowlatency
0 to upgrade, 1 to newly install, 0 to remove and 226 not to upgrade.
8 not fully installed or removed.
Need to get 0 B/58.1 MB of archives.
After this operation, 219 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 592023 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-79-lowlatency_4.4.0-79.100_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-79-lowlatency (4.4.0-79.100) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-79-lowlatency_4.4.0-79.100_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-4.4.0-79-lowlatency' to '/boot/System.map-4.4.0-79-lowlatency.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-79-lowlatency /boot/vmlinuz-4.4.0-79-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-79-lowlatency /boot/vmlinuz-4.4.0-79-lowlatency
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.4.0-79-lowlatency_4.4.0-79.100_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Does anyone understand what I'm doing wrong?

---

### Post by ajgreeny on 2017-06-12
Both apt and apt-get require a fair bit of headroom to work their magic and install or uninstall packages, and as you can see from your **df -h** output there is none.
```
/dev/nvme0n1p2                       473M  470M     0 100% /boot
```
We will need to get down and deal with this using dpkg to remove all the excess kernel packages.

Let's start with the oldest by running ```
sudo dpkg -P linux-image-4.4.0-31-lowlatency
```to see if that works and if successful we can also remove others except for the 4.4.0-72 which you are currently running and the 4.4.0-79 which is installed but not configured.

Give that a try then you can see if running ```
sudo apt-get autoremove
``` works to uninstall all the other kernel versions not needed.

---

### Post by jackwhitaker3 on 2017-06-12
Autoremove didn't work:

```
 homer@homer-Precision-3510:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 linux-image-lowlatency : Depends: linux-image-4.4.0-79-lowlatency but it is not installed
E: Unmet dependencies. Try using -f.


```

But I was able to delete each version one by one with dpkg.

Thanks so much for your help!

---

### Post by ajgreeny on 2017-06-12
Great news! 
Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

It is now probably best to run the autoremove command regularly as now you have enough free disk space it should work fine for you.

---

