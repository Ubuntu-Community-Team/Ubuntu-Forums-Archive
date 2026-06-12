---
title: "/boot too small for Upgrad to Feisty"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by amsch on 2007-04-21
Hi!

I tried to upgrade to Feisty today, but I get the following error message:

"...Free at least 16M of disk space on /boot..."

At the moment /boot boot is 37 MB big and 11 MB are used - so I can free at the maximum 11 MBs but not 16 MBs. How can I solve this? Is it possible to resize /boot partition?

Thanks!

---

### Post by Karl S. on 2007-04-21
There's a solution, of sorts, in [this thread]("http://ubuntuforums.org/showthread.php?t=414639&highlight=%2Fboot+space").

In the hopes of getting an answer, I'll post my problem, again, here:

I had the problem of the feisty install first telling me that I needed 8258K more in boot. I deleted material (about 9M) relating to old kernels, and then tried again. Now it tells me I need 8446K more. When I tried the third time, it said I needed 10.3M space free in /boot

For what it's worth:
karl@karl-laptop:~$ df -h /boot.
Filesystem Size Used Avail Use% Mounted on
/dev/hda2 4.6G 2.8G 1.6G 64% /
karl@karl-laptop:~$

Any idea why the amount of space I have to free keeps changing? I sudo apt-get clean between every failed attempt to install feisty.

==

You may also wish to look [here.]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/104337") Whatever the problem is, it looks as though it won't be fixed until Feisty +1.

What's a mystery to me is: a) why I should need more space in boot when I seem to have 1.6G available (or am I reading that wrong?); b) and why the amount of space I supposedly need keeps changing (usually for the worse, i.e., requiring more space).

---

### Post by a-musing amazon on 2007-04-21
FWIW I've just done a new install of Feisty Desktop on a second PC (I'm stil run Edgy on my main PC). In doing this I've followed good practice and put /boot on a separate partition (I also put /home in a separate partition too). In my case I allocated 64Mb and it has used 16.6Mb with a 'clear' install.

If you do automatic install it will put everything except swap into a single partition. If you have done this then you are unlikely to run out of boot space unless you fill the entire disk. However it sounds like you have sepearate partition for /boot.

You will find that boot does fill up as you get sent updated kernels, this will include those left over from Edgy and/or Dapper which you will also still see on your grub menu. The efficient way to remove these - i.e. remove all the associate files as well as the kernel itself - is to remove the surplus kernels in synaptic. Its normally good practice to keep at least the last kernel in case you have to regress (if its the same distribution it should more or less work if you choose it in grub). Obviouysly if you upgrading you wil need space for the Feisty as well as the Edgy kernel while it is updating.

use the df command to check your used/available space.

If, even after cleaning up your boot partition it is still too small then you may need to use gparted to move/resize the partitions. This can only be done if the partitions are not mounted, so you will need to burn and then boot from a gparted CD having downloaded the gparted .iso.

---

### Post by Karl S. on 2007-04-21
a-musing amazon: I presume you're addressing amsch and not me? 

Again, I just don't see how I don't have enough room in boot (1.6G available, unless I'm misreading it radically). I've deleted all the old kernels, so that shouldn't be a problem.

---

### Post by a-musing amazon on 2007-04-21
Karl,

if you type df in a terminal window, what is the output?

This is what I get on my main PC:

marjorie@erewhon:~$ df
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/sda2             10186840   5251976   4521032  54% /
varrun                  771092       132    770960   1% /var/run
varlock                 771092         4    771088   1% /var/lock
procbususb               10240       132     10108   2% /proc/bus/usb
udev                     10240       132     10108   2% /dev
devshm                  771092         0    771092   0% /dev/shm
lrm                     771092     20044    751048   3% /lib/modules/2.6.17-11-generic/volatile
/dev/sda1                60185     31176     25798  55% /boot
/dev/sda3             20153172  10180772   8948660  54% /home
/dev/hda1              7158976   5821204   1337772  82% /media/hda1
/dev/hda5              5116508   5099576     16932 100% /media/hda5
/dev/hda6              6136576   3059328   3077248  50% /media/hda6

i.e on this Machine /boot is on a separate partition and (/dev/sda1) and is 55% full, with ~32Mb used and ~26Mb free.

---

### Post by Karl S. on 2007-04-21
Looks as though boot's not on a separate partition for me:


karl@karl-laptop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda2              4806936   2888700   1674048  64% /
varrun                  972576       156    972420   1% /var/run
varlock                 972576         4    972572   1% /var/lock
procbususb               10240       108     10132   2% /proc/bus/usb
udev                     10240       108     10132   2% /dev
devshm                  972576        16    972560   1% /dev/shm
lrm                     972576     20564    952012   3% /lib/modules/2.6.17-11-386/volatile
/dev/hda5              6728280   3963064   2423436  63% /home
/dev/hda1             10008456   9524552    483904  96% /media/hda1
/dev/hda6             35928576  33533728   2394848  94% /media/hda6
karl@karl-laptop:~$ 

hda1 is Windows XP
hda6 is all my music and other files (dissertation &c.)

Here's df -h
karl@karl-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             4.6G  2.8G  1.6G  64% /
varrun                950M  156K  950M   1% /var/run
varlock               950M  4.0K  950M   1% /var/lock
procbususb             10M  108K  9.9M   2% /proc/bus/usb
udev                   10M  108K  9.9M   2% /dev
devshm                950M   16K  950M   1% /dev/shm
lrm                   950M   21M  930M   3% /lib/modules/2.6.17-11-386/volatile
/dev/hda5             6.5G  3.8G  2.4G  63% /home
/dev/hda1             9.6G  9.1G  473M  96% /media/hda1
/dev/hda6              35G   32G  2.3G  94% /media/hda6
karl@karl-laptop:~$ 


Judging by this [thread,]("http://ubuntuforums.org/showthread.php?t=414639&page=3&highlight=%2Fboot+size") I'm S.O.L.

EDIT

As it turns out, I figured it out. Look [here]("http://ubuntuforums.org/showpost.php?p=2508277&postcount=28") .

---

### Post by amsch on 2007-04-23
Actually Im using kubuntu and I cant find DistUpgradeController.py.

Can anybody help?

---

### Post by dlangeliers on 2007-04-27
I have the same problem using the update-manager. My /boot is a separate partition. Here's the 'df -h' output.

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             9.8G  4.2G  5.2G  45% /
varrun               1014M  160K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb             10M  180K  9.9M   2% /proc/bus/usb
udev                   10M  180K  9.9M   2% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   20M  994M   2% /lib/modules/2.6.17-11-386/volatile
/dev/sda2              45M   11M   32M  25% /boot
/dev/sda6             7.8G  2.6G  4.8G  35% /home
/dev/sda5              77G   63G   14G  82% /media/storage
/dev/disk/by-uuid/808C35A38C35951E
                       19G   12G  7.0G  63% /media/windows
/dev/sdb1             276G   89G  179G  34% /media/storage2

```

The update manager tells me that I need to free up about 9MB to install, and I supposedly have 32 MB available.

*Update
I've decided to update manually, hopefully all goes well :)

---

### Post by Saubazi on 2007-04-27
I used LiveCD and Gnome disk manager in order to increase the size of /boot to 100 MB.
It wasn't that straight forward since somehow the new space did not get freed. The partition got 100 MB big but it was all the sudden 72 MB used or something.

I then temporarily stored the real content of /boot to a temporary directory running still under LiveCD and formatted the /boot, which in turn caused problems later with grub since the partition got a new UUID but now it works, although I sorely regret upgrading.

---

