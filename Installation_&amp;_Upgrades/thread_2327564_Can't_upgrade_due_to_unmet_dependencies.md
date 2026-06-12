---
title: "Can't upgrade due to unmet dependencies"
date: 2016-06-12
forum: Installation &amp; Upgrades
---

### Post by titania177 on 2016-06-12
Hello,
I'm not a newbie but am not experienced using the command line. I'm trying to upgrade Ubuntu but keep getting the following error:

tania@tania-iMac:~$ sudo apt-get upgrade
[sudo] password for tania: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-image-extra-4.2.0-30-generic : Depends: linux-image-4.2.0-30-generic but it is not installed
E: Unmet dependencies. Try using -f.

Right now the only way I can boot up is to use an older kernel: 4.2.0-23-generic in recovery mode.

I've followed suggestions on many of the threads here, tried to fix the broken packages, tried to install linux-image-4.2.0-30-generic but nothing is working. 
Please help!

Tania

---

### Post by grahammechanical on 2016-06-12
Do you have a boot partition? If you installed and choose encryption or LVM then you would have been given a boot partition into which Linux kernels are put. If the boot partition becomes close to full, then a new upgrade to the kernel cannot complete and we get a situation like this.

It seems to be that you have an incomplete install of a new kernel. The first thing that apt-get or the Update Manager will try to do is to finish upgrading the kernel. Which it then fails to complete and that stops the rest of the updates from being installed.

Try running "clean - try to make free space" from the recovery menu. Or from the terminal run

```
sudo apt-get autoremove
```

That may remove one previously installed kernel. If you are using Ubuntu 16.04 then the command is

```
sudo apt autoremove
```

And autoremove will remove all previous kernels except two. Then the kernel upgrade will complete and also the other updates. The command autoremove does not run automatically. If we have a boot partition it makes sense to run the autoremeove command at regular intervals.

Regards.

---

### Post by titania177 on 2016-06-12
Thanks so much, as far as I remember I did chose to encrypt when I installed but not sure about the boot partition. Sorry, not great at all this! I tried your autoremove suggestion and it didn't work, due to unmet dependencies.

---

### Post by Impavidus on 2016-06-12
Let's take it to a lower level then.

Open a terminal, make it full screen so that it can hold enough output and use this command to get a list of the installed kernel packages: (copy-paste the command)```
dpkg --list linux-image\* linux-headers\*
```Post the output here. Next we can use dpkg to uninstall the packages you no longer need.

When you opt for an encrypted system, you automatically get a /boot partition. By default, it's rather small.

---

### Post by titania177 on 2016-06-12
Here's the output:
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture                Description
+++-=============================================-===========================-===========================-===============================================================================================
un  linux-headers                                 <none>                      <none>                      (no description available)
un  linux-headers-3.0                             <none>                      <none>                      (no description available)
un  linux-headers-3.19.0-15-generic               <none>                      <none>                      (no description available)
un  linux-headers-3.19.0-25-generic               <none>                      <none>                      (no description available)
un  linux-headers-3.19.0-31-generic               <none>                      <none>                      (no description available)
un  linux-headers-4.2.0-16-generic                <none>                      <none>                      (no description available)
un  linux-headers-4.2.0-18-generic                <none>                      <none>                      (no description available)
ii  linux-headers-4.2.0-19                        4.2.0-19.23                 all                         Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-19-generic                4.2.0-19.23                 amd64                       Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
un  linux-headers-4.2.0-21-generic                <none>                      <none>                      (no description available)
ii  linux-headers-4.2.0-22                        4.2.0-22.27                 all                         Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-22-generic                4.2.0-22.27                 amd64                       Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-23                        4.2.0-23.28                 all                         Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-23-generic                4.2.0-23.28                 amd64                       Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-25                        4.2.0-25.30                 all                         Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-25-generic                4.2.0-25.30                 amd64                       Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-27                        4.2.0-27.32                 all                         Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-27-generic                4.2.0-27.32                 amd64                       Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-30                        4.2.0-30.36                 all                         Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-30-generic                4.2.0-30.36                 amd64                       Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                         4.2.0.30.33                 amd64                       Generic Linux kernel headers
un  linux-image                                   <none>                      <none>                      (no description available)
un  linux-image-3.0                               <none>                      <none>                      (no description available)
rc  linux-image-3.19.0-15-generic                 3.19.0-15.15                amd64                       Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-25-generic                 3.19.0-25.26                amd64                       Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-31-generic                 3.19.0-31.36                amd64                       Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-16-generic                  4.2.0-16.19                 amd64                       Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-18-generic                  4.2.0-18.22                 amd64                       Linux kernel image for version 4.2.0 on 64 bit x86 SMP
pi  linux-image-4.2.0-19-generic                  4.2.0-19.23                 amd64                       Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-21-generic                  4.2.0-21.25                 amd64                       Linux kernel image for version 4.2.0 on 64 bit x86 SMP
pi  linux-image-4.2.0-22-generic                  4.2.0-22.27                 amd64                       Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-23-generic                  4.2.0-23.28                 amd64                       Linux kernel image for version 4.2.0 on 64 bit x86 SMP
iF  linux-image-4.2.0-25-generic                  4.2.0-25.30                 amd64                       Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-27-generic                  4.2.0-27.32                 amd64                       Linux kernel image for version 4.2.0 on 64 bit x86 SMP
in  linux-image-4.2.0-30-generic                  <none>                      amd64                       (no description available)
rc  linux-image-extra-3.19.0-15-generic           3.19.0-15.15                amd64                       Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-25-generic           3.19.0-25.26                amd64                       Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-31-generic           3.19.0-31.36                amd64                       Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-16-generic            4.2.0-16.19                 amd64                       Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-18-generic            4.2.0-18.22                 amd64                       Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-19-generic            4.2.0-19.23                 amd64                       Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-21-generic            4.2.0-21.25                 amd64                       Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-22-generic            4.2.0-22.27                 amd64                       Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
iF  linux-image-extra-4.2.0-23-generic            4.2.0-23.28                 amd64                       Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
iU  linux-image-extra-4.2.0-25-generic            4.2.0-25.30                 amd64                       Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-27-generic            4.2.0-27.32                 amd64                       Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
iU  linux-image-extra-4.2.0-30-generic            4.2.0-30.36                 amd64                       Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
```

---

### Post by ajgreeny on 2016-06-12
We need to get down and dirty with a dpkg command to remove one or two kernels and then you should be able to run the autoremove command suggested above.
```
sudo dpkg -P linux-image-3.19.0-31-generic
sudo apt autoremove
```

---

### Post by titania177 on 2016-06-12
Unfortunately, I get this output:
> 
tania@tania-iMac:~$ sudo dpkg -P linux-image-3.19.0-31-generic 
[sudo] password for tania: 
dpkg: dependency problems prevent removal of linux-image-3.19.0-31-generic:
 linux-image-extra-3.19.0-31-generic depends on linux-image-3.19.0-31-generic.
 linux-signed-image-3.19.0-31-generic depends on linux-image-3.19.0-31-generic (= 3.19.0-31.36).

dpkg: error processing package linux-image-3.19.0-31-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-3.19.0-31-generic


---

### Post by ajgreeny on 2016-06-12
Ah! I forgot about those dependencies so let's try this to remove them first then go back to the first command I suggested
```
sudo dpkg -P linux-image-extra-3.19.0-31-generic
sudo dpkg -P linux-signed-image-3.19.0-31-generic
```
followed by
```
sudo dpkg -P linux-image-3.19.0-31-generic
```
and finally ```
sudo apt-get autoremove
```

---

### Post by titania177 on 2016-06-12
Great, thank you! I did those first three, which seemed to work -  then when i did the autoremove I still got this:
> 
tania@tania-iMac:~$ sudo dpkg -P linux-signed-image-3.19.0-31-generic
dpkg: warning: ignoring request to remove linux-signed-image-3.19.0-31-generic which isn't installed
tania@tania-iMac:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 linux-image-extra-4.2.0-30-generic : Depends: linux-image-4.2.0-30-generic but it is not installed
E: Unmet dependencies. Try using -f.

---

### Post by ajgreeny on 2016-06-12
OK, so now try ```
sudo apt-get -f install
``` which will I hope sort out this final problem for you, then to check let's see what output you get from ```
sudo apt-get autoremove && df -hT
```

---

### Post by titania177 on 2016-06-12
This is the output I got:
```

tania@tania-iMac:~$ sudo apt-get autoremove && df -hT
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  linux-headers-4.2.0-25 linux-headers-4.2.0-25-generic linux-headers-generic
  linux-image-4.2.0-25-generic linux-image-extra-4.2.0-25-generic
  linux-signed-image-4.2.0-25-generic thermald
0 to upgrade, 0 to newly install, 7 to remove and 118 not to upgrade.
6 not fully installed or removed.
After this operation, 288 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 385694 files and directories currently installed.)
Removing linux-signed-image-4.2.0-25-generic (4.2.0-25.30) ...
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-30-generic
Found linux image: /boot/vmlinuz-4.2.0-25-generic
Found linux image: /boot/vmlinuz-4.2.0-23-generic
Found initrd image: /boot/initrd.img-4.2.0-23-generic
Found linux image: /boot/vmlinuz-4.2.0-22-generic
Found initrd image: /boot/initrd.img-4.2.0-22-generic
Found linux image: /boot/vmlinuz-4.2.0-19-generic
Found initrd image: /boot/initrd.img-4.2.0-19-generic
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
done
Removing linux-image-extra-4.2.0-25-generic (4.2.0-25.30) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.2.0-25-generic /boot/vmlinuz-4.2.0-25-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.2.0-25-generic /boot/vmlinuz-4.2.0-25-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.2.0-25-generic /boot/vmlinuz-4.2.0-25-generic
update-initramfs: Generating /boot/initrd.img-4.2.0-25-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.2.0-25-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.2.0-25-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.2.0-25-generic (4.2.0-25.30) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.2.0-25-generic /boot/vmlinuz-4.2.0-25-generic
dkms: removing: bcmwl 6.30.223.248+bdcom (4.2.0-25-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.30.223.248+bdcom
Kernel:  4.2.0-25-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.2.0-25-generic /boot/vmlinuz-4.2.0-25-generic
update-initramfs: Deleting /boot/initrd.img-4.2.0-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.2.0-25-generic /boot/vmlinuz-4.2.0-25-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-30-generic
Found linux image: /boot/vmlinuz-4.2.0-23-generic
Found initrd image: /boot/initrd.img-4.2.0-23-generic
Found linux image: /boot/vmlinuz-4.2.0-22-generic
Found initrd image: /boot/initrd.img-4.2.0-22-generic
Found linux image: /boot/vmlinuz-4.2.0-19-generic
Found initrd image: /boot/initrd.img-4.2.0-19-generic
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
done
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Removing linux-headers-4.2.0-25-generic (4.2.0-25.30) ...
Removing linux-headers-4.2.0-25 (4.2.0-25.30) ...
Removing linux-headers-generic (4.2.0.30.33) ...
Removing thermald (1.4.3-5) ...
Processing triggers for man-db (2.7.4-1) ...
Processing triggers for dbus (1.10.0-1ubuntu1) ...
Errors were encountered while processing:
 linux-image-extra-4.2.0-25-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by ajgreeny on 2016-06-12
There was no output from the final part of the command I showed so please run ```
df -hT
```again to see how much space you now have on all mounted partitions.

---

### Post by titania177 on 2016-06-12
Here it is:
> 
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3.9G     0  3.9G   0% /dev
tmpfs          tmpfs     793M  9.5M  783M   2% /run
/dev/dm-0      ext4      909G   52G  811G   7% /
tmpfs          tmpfs     3.9G   75M  3.8G   2% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda2      ext2      237M  216M  9.1M  96% /boot
/dev/sda1      vfat      511M  3.4M  508M   1% /boot/efi
cgmfs          tmpfs     100K     0  100K   0% /run/cgmanager/fs
tmpfs          tmpfs     793M   52K  793M   1% /run/user/1000


---

### Post by ajgreeny on 2016-06-12
This is still the problem > /dev/sda2 ext2 237M 216M 9.1M 96% /boot so it looks as if we have not yet managed to get rid of those unwanted kernels.

Just out of interest what does command ```
ls /boot | grep vmlinuz
``` give as output.

---

### Post by titania177 on 2016-06-12
it gives this:

> tania@tania-iMac:~$ ls /boot | grep vmlinuz
vmlinuz-3.19.0-31-generic
vmlinuz-4.2.0-19-generic
vmlinuz-4.2.0-19-generic.efi.signed
vmlinuz-4.2.0-22-generic
vmlinuz-4.2.0-22-generic.efi.signed
vmlinuz-4.2.0-23-generic
vmlinuz-4.2.0-23-generic.efi.signed
vmlinuz-4.2.0-30-generic


---

### Post by ajgreeny on 2016-06-12
Right, so let's try ```
sudo dpkg -P linux-image-extra-4.2.0-19-generic
sudo dpkg -P linux-image-4.2.0-19-generic
```
to see if that gets rid of something and makes some space for you to run the autoremove command again.

---

### Post by titania177 on 2016-06-12
The first removal worked, but the second returned this:

> tania@tania-iMac:~$ sudo dpkg -P linux-image-4.2.0-19-generic
dpkg: dependency problems prevent removal of linux-image-4.2.0-19-generic:
 linux-signed-image-4.2.0-19-generic depends on linux-image-4.2.0-19-generic (= 4.2.0-19.23).

dpkg: error processing package linux-image-4.2.0-19-generic (--purge):
 dependency problems - not removing
Errors were encountered while p

---

### Post by ajgreeny on 2016-06-12
We keep going round in circles here with all the dependencies of these various linu-image* packages but let's keep working on it.

Try ```
sudo dpkg -P linux-signed-image-4.2.0-19-generic && sudo dpkg -P linux-image-4.2.0-19-generic
``` and with a bit of luck that will do it.

Then again try the ```
sudo apt-get autoremove
``` command.

We'll get there eventually!

---

### Post by titania177 on 2016-06-12
It worked! Thank you all SO much! I had to do a bit more manual purging of packages, but just upgraded to 16.04 and everything seems fine!

Thank you all again for your help.

Tania

---

### Post by ajgreeny on 2016-06-13
Brilliant! I knew we could do it.
Now please mark this as solved from the Thread Tools menu up top.

---

