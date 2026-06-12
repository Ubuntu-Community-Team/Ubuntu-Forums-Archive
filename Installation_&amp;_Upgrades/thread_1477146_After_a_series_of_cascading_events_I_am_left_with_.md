---
title: "After a series of cascading events I am left with broken dependencies"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by Josunik on 2010-05-08
Hello Folks,

I updated my karmic koala to Lucid Lynx; Usually when I am updating I clear off space from my boot partition. In this case I was caught off guard by y updater; to make a long story short here is what happend:

1 update stops after no enough space on my boot.

2 I free off from synaptic by deleting an old install (the one before the last one)

3 install succeeds but with errors, initramfs-tools not correctly updated; not enough space, reads the error, after reboot I am left with low graphic setting from nvidia, and stuck with no updates.

4 tried to liberate more space from my boot partition from synaptic but fails since initramfs-tools cannot update

5 trough terminal I manage to manualy uninstall last vertion of ubuntu Karmic Koala, just to liberate more space.

6 I successfully recover nvidia functionality and make initramfs-tools to update. But I am left with two broken packages from previous Karmic Koala:
the linux-backports-2.6.31-21-generic and linux-backports-alsa-2.6.31-21-generic.

I assumed this comes from manually unistaling linux-image-2.6.31-21

my synaptic shows two red lines for those 2 broken packages that I mentioned before.

I need ideas, otherwise I would have to format and start over.

as for now I am unable to do any upgrades or intalations.

Note:

my computer janitor found and uninstalled packages linked to Karmic Koala repositories, but I assume this is ok, since I wont be using those.

---

### Post by frantid on 2010-05-08
in a terminal do

sudo apt-get check

it will give you errors or things you need to resolve.

if you get unconfigured packages run

sudo dpkg --configure -a

you can try 

sudo apt-get update

sudo apt-get dist-upgrade

---

### Post by kansasnoob on 2010-05-08
Do everything Frantid said, but the command:

```
sudo apt-get -f install
```

may also provide some good info. And also:

```
ls /boot
```

might be useful for troubleshooting.

It should also be safe to run:

```
sudo apt-get clean
```

or:

```
sudo apt-get autoremove
```

---

### Post by Josunik on 2010-05-08
Hi,

thanks for the reply, here is what happend:

apt-get check didn't returned any info

sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  linux-backports-modules-2.6.31-21-generic
  linux-backports-modules-alsa-2.6.31-21-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 11.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 169991 files and directories currently installed.)
Removing linux-backports-modules-2.6.31-21-generic ...
[COLOR="Red"]FATAL: Could not open '/boot/System.map-2.6.31-21-generic': No such file or directory[/COLOR]
update-initramfs: Generating /boot/initrd.img-2.6.31-21-generic
Cannot find /lib/modules/2.6.31-21-generic
update-initramfs: failed for /boot/initrd.img-2.6.31-21-generic
[COLOR="Red"]dpkg: error processing linux-backports-modules-2.6.31-21-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-backports-modules-alsa-2.6.31-21-generic ...
FATAL: Could not open '/boot/System.map-2.6.31-21-generic': No such file or directory[/COLOR]
update-initramfs: Generating /boot/initrd.img-2.6.31-21-generic
Cannot find /lib/modules/2.6.31-21-generic
update-initramfs: failed for /boot/initrd.img-2.6.31-21-generic
dpkg: error processing linux-backports-modules-alsa-2.6.31-21-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-backports-modules-2.6.31-21-generic
 linux-backports-modules-alsa-2.6.31-21-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


I will continue looking

---

### Post by Josunik on 2010-05-08
ls /boot
abi-2.6.32-22-generic         memtest86+.bin
config-2.6.32-22-generic      System.map-2.6.32-22-generic
grub                          vmcoreinfo-2.6.32-22-generic
initrd.img-2.6.32-22-generic  vmlinuz-2.6.32-22-generic

---

### Post by frantid on 2010-05-08
you seem to be right about it not knowing what to do since it can't find the files it wants to remove.

let me look at this a minute.

---

### Post by frantid on 2010-05-08
lets try

```
sudo apt-get remove -f linux-backports-modules-2.6.31-21-generic
```
  
```
sudo apt-get remove -f  linux-backports-modules-alsa-2.6.31-21-generic
```

if those don't work then

```
dpkg --purge linux-backports-modules-2.6.31-21-generic
```


```
dpkg --purge  linux-backports-modules-alsa-2.6.31-21-generic
```

---

### Post by Josunik on 2010-05-08
Thanks for the reply.

It seems that "linux" is trying to read a file that doesn't exist, maybe creating a fake file, and then proceed with this riddle will help, i have no idea duh of how to do that.

the 2 last options returned the same error message:

(Reading database ... 169991 files and directories currently installed.)
Removing linux-backports-modules-2.6.31-21-generic ...
FATAL: Could not open '/boot/System.map-2.6.31-21-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.31-21-generic
Cannot find /lib/modules/2.6.31-21-generic
update-initramfs: failed for /boot/initrd.img-2.6.31-21-generic
dpkg: error processing linux-backports-modules-2.6.31-21-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-backports-modules-2.6.31-21-generic

---

### Post by frantid on 2010-05-08
let's see first what dpkg wants us to do:

```
dpkg --audit  linux-backports-modules-alsa-2.6.31-21-generic
```

---

### Post by Josunik on 2010-05-08
Seems that "linux" will try to read a file that does not exists, maybe creating a fake one will work, but I am not sure if this is the right way or how to do it.

after try all the terminal commands suggested i am still stuck with the next message:

(Reading database ... 169991 files and directories currently installed.)
Removing linux-backports-modules-2.6.31-21-generic ...
FATAL: Could not open '/boot/System.map-2.6.31-21-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.31-21-generic
Cannot find /lib/modules/2.6.31-21-generic
update-initramfs: failed for /boot/initrd.img-2.6.31-21-generic
dpkg: error processing linux-backports-modules-2.6.31-21-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-backports-modules-2.6.31-21-generic

---

### Post by Josunik on 2010-05-08
hey Frantid,

could you repeat your last suggestion?. It wont start.

josunik@josunik-laptop:~$ sudo dpkg --audit  linux-backports-modules-alsa-2.6.31-21-generic
[sudo] password for josunik: 
dpkg: --audit takes no arguments

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

---

### Post by Josunik on 2010-05-08
I am now trying this:

josunik@josunik-laptop:~$ sudo dpkg --audit linux-backports-modules-alsa-2.6.31-21-generic
dpkg: --audit takes no arguments

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
josunik@josunik-laptop:~$ sudo apt-get --audit
E: Command line option --audit is not understood
josunik@josunik-laptop:~$ dpkg --audit
The following packages are only half installed, due to problems during
installation.  The installation can probably be completed by retrying it;
the packages can be removed using dselect or dpkg --remove:
 linux-backports-modules-alsa-2.6.31-21-generic Ubuntu supplied Linux modules f
 linux-backports-modules-2.6.31-21-generic Ubuntu supplied Linux modules for ve

---

### Post by frantid on 2010-05-08
the only way maybe to reinstall then uninstall.

```
   sudo apt-get install linux-backports-modules-2.6.31-21-generic 
``` 
 ```
    sudo apt-get install  linux-backports-modules-alsa-2.6.31-21-generic
```

---

### Post by Josunik on 2010-05-08
josunik@josunik-laptop:~$ sudo apt-get install linux-backports-modules-2.6.31-21-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-backports-modules-2.6.31-21-generic is already the newest version.
The following packages will be REMOVED:
  linux-backports-modules-2.6.31-21-generic
  linux-backports-modules-alsa-2.6.31-21-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 11.3MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

how can it be the newest version if I am in lucid?

maybe will format in the morning

---

### Post by frantid on 2010-05-08
ok

I tried this on mine, but mine wasn't broken.

```
sudo dpkg --force-remove-reinstreq --purge linux-backports-modules-alsa-2.6.31-21-generic
```

---

### Post by Josunik on 2010-05-08
Hello guys,

First of all many thanks to frantid for his time.

I was downloding the Lucid Lynx in order to create an ISO disk and format the whole thing as I was out of patiente.

But finally I found the solution in one site and here I post it for everybody enjoyment or at least for mine:

1. Created all the directories with mkdir
mkdir -p /lib/modules/2.6.27-7-generic/volatile/

2. Created all the files with touch
touch /boot/System.map-2.6.27-7-generic (use the correct problematic file)
touch /boot/initrd.img-2.6.27-7-generic

3. Fixing it with
sudo aptitude -f remove

note: dont forget to use sudo command before mkdir and touch.

And thats it, got my system back and running, synaptic is able to upgrade and isntall again

---

### Post by frantid on 2010-05-08
glad you found it.  I will remember that one.

---

### Post by alexelprogramador on 2010-05-25
> **Josunik said:**
> Thanks for the reply.


(Reading database ... 169991 files and directories currently installed.)
Removing linux-backports-modules-2.6.31-21-generic ...
FATAL: Could not open '/boot/System.map-2.6.31-21-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.31-21-generic
Cannot find /lib/modules/2.6.31-21-generic
update-initramfs: failed for /boot/initrd.img-2.6.31-21-generic
dpkg: error processing linux-backports-modules-2.6.31-21-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-backports-modules-2.6.31-21-generic

Hi!

I got the same problem, but I solved it only executing this command:

```
**sudo aptitude**
```


then, when you try to dowload something (with the "g" key) it will ask you about some broken packages of dpkg

only say yes to everithing and it will be solved.

bye

---

