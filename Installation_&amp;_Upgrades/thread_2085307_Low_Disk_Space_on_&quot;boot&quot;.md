---
title: "Low Disk Space on &quot;boot&quot;"
date: 2012-11-17
forum: Installation &amp; Upgrades
---

### Post by benjamin.s.vaccaro on 2012-11-17
Hello,

For a few months now 12.04 Desktop Edition has been informing me that I only have 2.9MB desk space remaining.

I have never seen this message on previous versions of ubuntu - does anyone know a method (preferably something in terminal) that will allow me to erase all but the current grub version? Or whatever is deemed the appropriate # of grub versions to keep. Unless I clean up the boot folder I cannot install crucial updates (its been two months since my last update/upgrade).

The current size of "boot" is 223.1MB.

Thanks!

---

### Post by darkod on 2012-11-17
You should be able to see all of them with something like:
```
ls /boot
```

Note that in /boot they show as vmlinuz-3.2.0-XX-generic or similar.

You can remove them with:
```
sudo apt-get purge linux-image-3.2.0-XX-generic
```

Be very careful not to remove all of them, or the latest. After that run:
```
sudo update-grub
```

to recreate the grub menu.

---

### Post by Bashing-om on 2012-11-17
To get a report of how much disk space is available and what is taking up the space where; terminal code:
```
df -h
```IF  indeed you find that boot is full, This method to delete old kernels and headers:
The command in terminal:
```
uname -a
``` will tell you which kernel you are running....then:
-- if you have the disk space--
Go to Synaptic Package Manager  select status on the left-lower  pane and select installed on the left-upper pane and search for linux-image.
 select the ones you want deleted. listed in the right-upperpane.
  and mark for removal/complete removal.
Click the Apply button in the toolbar and then Apply in the summary window that pops up. Close Synaptic Package Manager.
sudo update-grub
if spm is not installed; terminal code:
```
sudo apt-get install synaptic
```  In addition to linux-image, also remove old versions of linux-headers and linux-restricted-modules (if you have them).

To look at the disk usage:
```
du -h /home | sort -nr | less
```by directories ->change the /home in the above to different directories to "see". Pay particular attention to the /var/log/ directory...many times there exist lots of old files.; And it does happen there is a system problem the system is advising of that results in extremely large log files.[INDENT]just try'n to help <== BDQ

[/INDENT]

---

### Post by ajgreeny on 2012-11-17
Do you have a separate /boot partition, and if so is there a good reason why you installed with one, as it tends to complicate matters in most cases.

You can see how many kernels or OSs are on your system with ```
grep menuentry /boot/grub/grub.cfg
``` which will list everything that appears in the grub menu, including any other OSs, eg Windows or other Linux OSs.  It will also show all the different kernels that are installed and you can then uninstall all except the two latest using software-center or synaptic, or whatever you normally use for package management.

Unfortunately as a result of the newer version of grub in 12.10, that command is no longer very helpful.  It still works but grub now has a lot of extraneous information in grub.cfg which just complicates the output, making it almost useless, though I am sure there must be a way of extracting only what is needed somehow or other.

---

### Post by Bashing-om on 2012-11-17
@ajgreeny;   Nifty code -> placed for remembrance !

---

### Post by benjamin.s.vaccaro on 2012-11-18
Thanks for all of your advice, unfortunately I was unsuccessful at deleting the older grubs (there are about 6 older versions in /boot).

Even though this PC is a little over 5 years old it recently started freezing and I think the best solution at this point will be to reformat and possibly dual boot mint 13 with 12.04. 

Thanks for all your help!

---

### Post by Bashing-om on 2012-11-18
How about deleting the cache files and obsolete files ? See if ya get enough space to install synaptic -> use synaptic to remove the old kernels ?
```
sudo apt-get autoclean
sudo apt-get clean

```[INDENT][INDENT]try'n to help ==> BDQ

[/INDENT][/INDENT]

---

### Post by cwsnyder on 2012-11-18
You may also want to try the bleachbit package to remove cache files, old log files, etc.

---

### Post by snowpine on 2012-11-18
You must use the recommended code from post #3 to find out where the problem is:

```
df -h
```

Otherwise you are simply guessing.

---

### Post by benjamin.s.vaccaro on 2012-11-18
Filesystem                 Size  Used Avail Use% Mounted on
/dev/mapper/benjamin-root  292G   30G  248G  11% /
udev                       990M  4.0K  990M   1% /dev
tmpfs                      401M  812K  400M   1% /run
none                       5.0M     0  5.0M   0% /run/lock
none                      1002M  676K 1001M   1% /run/shm
/dev/sda1                  228M  213M  2.8M  99% /boot


Things I have tried:
-$ ls /boot
-$ sudo apt-get purge abi-3.2.0-23-generic
I keep getting this error message: 
E: Unable to locate package abi-3.2.0-23-generic
E: Couldn't find any package by regex 'abi-3.2.0-23-generic'

I also get this message with other versions. Below is a list of ls /boot:

abi-3.2.0-23-generic         initrd.img-3.2.0-29-generic
abi-3.2.0-24-generic         initrd.img-3.2.0-30-generic
abi-3.2.0-25-generic         lost+found
abi-3.2.0-26-generic         memtest86+.bin
abi-3.2.0-27-generic         memtest86+_multiboot.bin
abi-3.2.0-29-generic         System.map-3.2.0-23-generic
abi-3.2.0-30-generic         System.map-3.2.0-24-generic
abi-3.2.0-31-generic         System.map-3.2.0-25-generic
config-3.2.0-23-generic      System.map-3.2.0-26-generic
config-3.2.0-24-generic      System.map-3.2.0-27-generic
config-3.2.0-25-generic      System.map-3.2.0-29-generic
config-3.2.0-26-generic      System.map-3.2.0-30-generic
config-3.2.0-27-generic      System.map-3.2.0-31-generic
config-3.2.0-29-generic      vmlinuz-3.2.0-23-generic
config-3.2.0-30-generic      vmlinuz-3.2.0-24-generic
config-3.2.0-31-generic      vmlinuz-3.2.0-25-generic
grub                         vmlinuz-3.2.0-26-generic
initrd.img-3.2.0-23-generic  vmlinuz-3.2.0-27-generic
initrd.img-3.2.0-24-generic  vmlinuz-3.2.0-29-generic
initrd.img-3.2.0-25-generic  vmlinuz-3.2.0-30-generic
initrd.img-3.2.0-26-generic  vmlinuz-3.2.0-31-generic
initrd.img-3.2.0-27-generic

---

### Post by benjamin.s.vaccaro on 2012-11-18
I am also cautious not to purge my current grub using bashing's suggestion:

uname -a

I do not have any other OS installed. Just Ubuntu 12.04 with LVM and HDD Encryption.

---

### Post by darkod on 2012-11-19
I don't know what those abi- files are. The ubuntu kernel is the vmlinuz-XXXX so you need to try:
sudo apt-get purge linux-image-3.2.0-23-generic

Yes, the list in /boot says vmlinuz- but for the actual kernel package that is substituted with linux-image-....

Try that.

---

### Post by irishmick on 2013-02-14
Been running 12.04 for over a year now and just ran into this same problem today.

Synaptic Package Manager---FTW

Thanks guys worked perfectly!

---

