---
title: "not enough Free space in boot, have tried a few things."
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by nicklikesfire on 2008-11-18
Hello,

So I'm trying to upgrade to 8.10, and I've got the problem where I get a message:

> Not enough free disk space

The upgrade aborts now. The upgrade needs a total of 88.1M free space on disk '/boot'. Please free at least an additional 88.1M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

when I try to upgrade from 8.04

df -h gives me:

> nick@nick-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc2              39G   32G  6.4G  84% /
varrun               1008M  220K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M   84K 1008M   1% /dev
devshm               1008M  232K 1008M   1% /dev/shm
lrm                  1008M   44M  964M   5% /lib/modules/2.6.24-21-generic/volatile
/dev/sdc1             118M  113M     0 100% /boot
/dev/sda1             466G  330G  137G  71% /media/sda1
/dev/sdb1             466G  309G  157G  67% /media/sdb1
/dev/sdc4             145G  3.0G  142G   3% /usr
/dev/scd0             1.5G  1.5G     0 100% /media/CIGAR_BOXES


I'm not sure where to go from here. Anything anyone can tell me would be appreciated.

---

### Post by Pumalite on 2008-11-18
Post a screenshot of Gparted

---

### Post by sisco311 on 2008-11-18
post:
```
ls -alh /boot
```
and
```
uname -r
```

---

### Post by nicklikesfire on 2008-11-18
> nick@nick-desktop:~$ ls -alh /boot
total 52M
drwxr-xr-x  5 root root 2.0K 2008-11-18 19:44 .
drwxr-xr-x 23 root root  736 2008-11-05 02:53 ..
-rw-r--r--  1 root root 409K 2008-02-11 23:30 abi-2.6.22-14-generic
-rw-r--r--  1 root root 411K 2008-04-10 11:12 abi-2.6.24-16-generic
-rw-r--r--  1 root root 411K 2008-05-01 12:37 abi-2.6.24-17-generic
-rw-r--r--  1 root root 411K 2008-05-28 19:56 abi-2.6.24-18-generic
-rw-r--r--  1 root root 411K 2008-08-20 18:15 abi-2.6.24-19-generic
-rw-r--r--  1 root root 411K 2008-10-21 21:49 abi-2.6.24-21-generic
-rw-r--r--  1 root root  67K 2008-02-11 23:30 config-2.6.22-14-generic
-rw-r--r--  1 root root  73K 2008-04-10 11:12 config-2.6.24-16-generic
-rw-r--r--  1 root root  73K 2008-05-01 12:37 config-2.6.24-17-generic
-rw-r--r--  1 root root  73K 2008-05-28 19:56 config-2.6.24-18-generic
-rw-r--r--  1 root root  73K 2008-08-20 18:15 config-2.6.24-19-generic
-rw-r--r--  1 root root  73K 2008-10-21 21:49 config-2.6.24-21-generic
drwxr-xr-x  2 root root 1.0K 2008-11-05 02:53 grub
-rw-r--r--  1 root root 7.8M 2008-08-27 07:16 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 7.8M 2008-08-12 22:29 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root 7.8M 2008-11-05 02:53 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7.8M 2008-11-05 02:53 initrd.img-2.6.24-21-generic.bak
drwxr-xr-x  2 root root  12K 2008-01-06 14:07 lost+found
-rw-r--r--  1 root root 101K 2007-09-28 07:03 memtest86+.bin
-rw-r--r--  1 root root 1.1M 2008-02-11 23:30 System.map-2.6.22-14-generic
-rw-r--r--  1 root root 1.1M 2008-04-10 11:12 System.map-2.6.24-16-generic
-rw-r--r--  1 root root 1.1M 2008-05-01 12:37 System.map-2.6.24-17-generic
-rw-r--r--  1 root root 1.1M 2008-05-28 19:56 System.map-2.6.24-18-generic
-rw-r--r--  1 root root 1.1M 2008-08-20 18:15 System.map-2.6.24-19-generic
-rw-r--r--  1 root root 1.1M 2008-10-21 21:49 System.map-2.6.24-21-generic
drwx------  4 root root 1.0K 2008-11-18 19:43 .Trash-0
-rw-r--r--  1 root root 1.7M 2008-02-11 23:30 vmlinuz-2.6.22-14-generic
-rw-r--r--  1 root root 1.9M 2008-04-10 11:12 vmlinuz-2.6.24-16-generic
-rw-r--r--  1 root root 1.9M 2008-05-01 12:37 vmlinuz-2.6.24-17-generic
-rw-r--r--  1 root root 1.9M 2008-05-28 19:56 vmlinuz-2.6.24-18-generic
-rw-r--r--  1 root root 1.9M 2008-08-20 18:15 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1.9M 2008-10-21 21:49 vmlinuz-2.6.24-21-generic


and

> nick@nick-desktop:~$ uname -r
2.6.24-21-generic
nick@nick-desktop:~$ 


Thanks for the quick replies.

So, I know this is silly, but I don't even know what Gparted is. I'll work on finding that out and hopefully get back to this soon.

---

### Post by sisco311 on 2008-11-18
to free up some space:

1.) try to empty the /boot/.Trash-0 folder.
to open the file manager as root press Alt+F2 and type:
```
gksu nautilus
```
navigate to the /boot folder and press Ctrl+H 
and delete the content of the .Trash-0 folder.

2.) remove the old kernels:
open Synaptic and remove:

linux-image-2.6.22-14-generic
linux-image-2.6.24-16-generic
linux-image-2.6.24-17-generic
linux-image-2.6.24-18-generic

**DON'T REMOVE** linux-image-2.6.24-21-generic (the current kernel)

try to upgrade again.

---

### Post by nicklikesfire on 2008-11-19
I still don't have enough free space:

> Not enough free disk space

The upgrade aborts now. The upgrade needs a total of 88.1M free space on disk '/boot'. Please free at least an additional 25.6M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

I think if I delete everything that doesn't end in 24-21 (the system map and vmlinuz files) I'll have enough, according to the message. Should I try it?

Thanks again for the replies, you all are very clear which helps me a lot. I really appreciate it.

---

### Post by sisco311 on 2008-11-19
did you try to run:
```
sudo apt-get clean
```as suggested in  the error message?

You can also delete the backup files(the files with the .bak extension).

if that doesn't work post the output of:
```
ls -alh /boot
```
and
```
df -h
```

---

### Post by Pumalite on 2008-11-19
Let's see if we can make your /boot bigger

---

### Post by nicklikesfire on 2008-11-19
I tried```

sudo apt-get clean
```
first thing, but I just tried it again anyways, still not enough space after that.

Here are the outputs of those commands:

> nick@nick-desktop:~$ ls -alh /boot
total 36M
drwxr-xr-x  5 root root 2.0K 2008-11-19 12:30 .
drwxr-xr-x 23 root root  736 2008-11-05 02:53 ..
-rw-r--r--  1 root root 409K 2008-02-11 23:30 abi-2.6.22-14-generic
-rw-r--r--  1 root root 411K 2008-04-10 11:12 abi-2.6.24-16-generic
-rw-r--r--  1 root root 411K 2008-05-01 12:37 abi-2.6.24-17-generic
-rw-r--r--  1 root root 411K 2008-05-28 19:56 abi-2.6.24-18-generic
-rw-r--r--  1 root root 411K 2008-08-20 18:15 abi-2.6.24-19-generic
-rw-r--r--  1 root root 411K 2008-10-21 21:49 abi-2.6.24-21-generic
-rw-r--r--  1 root root  67K 2008-02-11 23:30 config-2.6.22-14-generic
-rw-r--r--  1 root root  73K 2008-04-10 11:12 config-2.6.24-16-generic
-rw-r--r--  1 root root  73K 2008-05-01 12:37 config-2.6.24-17-generic
-rw-r--r--  1 root root  73K 2008-05-28 19:56 config-2.6.24-18-generic
-rw-r--r--  1 root root  73K 2008-08-20 18:15 config-2.6.24-19-generic
-rw-r--r--  1 root root  73K 2008-10-21 21:49 config-2.6.24-21-generic
drwxr-xr-x  2 root root 1.0K 2008-11-05 02:53 grub
-rw-r--r--  1 root root 7.8M 2008-11-05 02:53 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7.8M 2008-11-05 02:53 initrd.img-2.6.24-21-generic.bak
drwxr-xr-x  2 root root  12K 2008-01-06 14:07 lost+found
-rw-r--r--  1 root root 101K 2007-09-28 07:03 memtest86+.bin
-rw-r--r--  1 root root 1.1M 2008-02-11 23:30 System.map-2.6.22-14-generic
-rw-r--r--  1 root root 1.1M 2008-04-10 11:12 System.map-2.6.24-16-generic
-rw-r--r--  1 root root 1.1M 2008-05-01 12:37 System.map-2.6.24-17-generic
-rw-r--r--  1 root root 1.1M 2008-05-28 19:56 System.map-2.6.24-18-generic
-rw-r--r--  1 root root 1.1M 2008-08-20 18:15 System.map-2.6.24-19-generic
-rw-r--r--  1 root root 1.1M 2008-10-21 21:49 System.map-2.6.24-21-generic
drwx------  4 root root 1.0K 2008-11-19 12:31 .Trash-0
-rw-r--r--  1 root root 1.7M 2008-02-11 23:30 vmlinuz-2.6.22-14-generic
-rw-r--r--  1 root root 1.9M 2008-04-10 11:12 vmlinuz-2.6.24-16-generic
-rw-r--r--  1 root root 1.9M 2008-05-01 12:37 vmlinuz-2.6.24-17-generic
-rw-r--r--  1 root root 1.9M 2008-05-28 19:56 vmlinuz-2.6.24-18-generic
-rw-r--r--  1 root root 1.9M 2008-08-20 18:15 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1.9M 2008-10-21 21:49 vmlinuz-2.6.24-21-generic
nick@nick-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc2              39G   32G  6.4G  84% /
varrun               1008M  220K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M   84K 1008M   1% /dev
devshm               1008M  212K 1008M   1% /dev/shm
lrm                  1008M   44M  964M   5% /lib/modules/2.6.24-21-generic/volatile
/dev/sdc1             118M   37M   76M  33% /boot
/dev/sda1             466G  330G  137G  71% /media/sda1
/dev/sdb1             466G  309G  157G  67% /media/sdb1
/dev/sdc4             145G  3.0G  142G   3% /usr
nick@nick-desktop:~$ 

Hope that helps you help me, let me know if there's anything else.

Oh, and how do we go about making /boot bigger? That seems like it would be good, so I don't have this problem again, the next time I upgrade.

I tried adding gparted to my applications list, but everytime I click it I get the message:

> The list of applications is not availabe

Click on 'Reload' to load it. To reload the list you need a working internet connection. 

And then I click refresh (there is no reload button). At which point I have the chance to once again click on gparted, but the same thing happens again. (I figure this is an entirely separate issue though, so I didn't want to bring it up here).

Thanks!

---

### Post by nicklikesfire on 2008-11-20
anyone?

---

### Post by nicklikesfire on 2008-11-28
One more shot, I suppose. If anyone can help, that would be great, otherwise I'll just keep trying some things I guess.

Thanks!

---

