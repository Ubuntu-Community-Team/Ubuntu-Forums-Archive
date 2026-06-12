---
title: "I cant update, 3 packages are broken and i cant fix them"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by tatoniss on 2008-06-03
hi i tired to update and i got an error, it said to go to the package manager and fix them. every time i try to reinstall them it does not work.
Packages
Linux-image-generic 
Linux-restricted-modules
Linux-ubuntu-modules

I have hardy 8.04


 Here is the error at the ene of the of installer

E: /var/cache/apt/archives/linux-image-2.6.24-18-generic_2.6.24-18.32_i386.deb: failed in buffer_write(fd) (10, ret=-1)

it keeps saying things about dependencies but i don't know what that means,

If you could help it would mean a lot

---

### Post by iaculallad on 2008-06-03
On your terminal

```
sudo apt-get clean
sudo apt-get autoclean
```

to free spaces.

---

### Post by tatoniss on 2008-06-03
ok the first one worked but the second one had an error

tatoniss@Eric-desktop:~$ sudo apt-get clean
[sudo] password for tatoniss: 
tatoniss@Eric-desktop:~$ sudo apt-get autoclean
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
tatoniss@Eric-desktop:~$

---

### Post by iaculallad on 2008-06-03
Close your Synaptics or Add/Remove window if open then retry sudo apt-get clean.

---

### Post by tatoniss on 2008-06-03
OK both worked, what should i do now?

---

### Post by ChameleonDave on 2008-06-03
> **tatoniss said:**
> OK both worked, what should i do now?
Well, hopefully the problem is solved.

To update your system, input these commands:
```

sudo apt-get update
sudo apt-get upgrade
```

---

### Post by iaculallad on 2008-06-03
If the same error prompts, check synaptic for old Linux image - uninstall the old ones, to get more disk space.

The redo:

sudo apt-get update
sudo apt-get upgrade

---

### Post by tatoniss on 2008-06-03
ok the update worked but the following error happend with the upgrade

tatoniss@Eric-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  linux-image-generic: Depends: linux-image-2.6.24-18-generic but it is not installed
  linux-restricted-modules-2.6.24-18-generic: Depends: linux-image-2.6.24-18-generic but it is not installed
  linux-ubuntu-modules-2.6.24-18-generic: Depends: linux-image-2.6.24-18-generic but it is not installed
E: Unmet dependencies. Try using -f.
tatoniss@Eric-desktop:~$

---

### Post by iaculallad on 2008-06-03
On your terminal, run the command below to fix it.

```
sudo apt-get -f install
```

---

### Post by tatoniss on 2008-06-03
It seemed to be working but then this error happened, by the way thankyou for your time.

tatoniss@Eric-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libtimedate-perl dpkg-dev patch
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-2.6.24-18-generic
Suggested packages:
  linux-doc-2.6.24 linux-source-2.6.24
The following NEW packages will be installed:
  linux-image-2.6.24-18-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 18.4MB of archives.
After this operation, 61.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main linux-image-2.6.24-18-generic 2.6.24-18.32 [18.4MB]
Fetched 18.4MB in 57s (318kB/s)                                                
(Reading database ... 169714 files and directories currently installed.)
Unpacking linux-image-2.6.24-18-generic (from .../linux-image-2.6.24-18-generic_2.6.24-18.32_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-18-generic_2.6.24-18.32_i386.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./boot/vmlinuz-2.6.24-18-generic': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-17-generic
Found kernel: /vmlinuz-2.6.24-16-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.24-18-generic_2.6.24-18.32_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
tatoniss@Eric-desktop:~$

---

### Post by iaculallad on 2008-06-03
Try to perform what I printed on my post #3. You still have to free more drive spaces.

---

### Post by meierfra. on 2008-06-03
> No space left on device

Is you boot partition full?

Post the output of

```
df -h
```

---

### Post by tatoniss on 2008-06-03
o do I need to make my boot partition larger, the errors are happening because of low space

tatoniss@Eric-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              17G  4.9G   11G  31% /
varrun                125M  120K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M   44K  125M   1% /dev
devshm                125M   12K  125M   1% /dev/shm
lrm                   125M   38M   88M  30% /lib/modules/2.6.24-17-generic/volatile
/dev/sda1              31M   30M     0 100% /boot
gvfs-fuse-daemon       17G  4.9G   11G  31% /home/tatoniss/.gvfs
/dev/scd0             4.1M  4.1M     0 100% /media/cdrom0
tatoniss@Eric-desktop:~$

---

### Post by meierfra. on 2008-06-03
> /dev/sda1 31M 30M 0 100% /boot

As you realized,this is your problem. Uninstall some of the older kernels through the synaptic  package manager.

Yes, you might also think  about increasing the size of your boot partition.

---

### Post by tatoniss on 2008-06-04
can i use my live cd to resize my root partition

---

### Post by meierfra. on 2008-06-04
> can i use my live cd to resize my root partition

Sure.  Since you will have to shrink your Ubuntu partition, you  should backup all your important Data first.

So it might be easier to just deleted the  "......24-16....." kernel. Since you still have the 24-17 kernel,  you won't need the 24-16 kernel

---

