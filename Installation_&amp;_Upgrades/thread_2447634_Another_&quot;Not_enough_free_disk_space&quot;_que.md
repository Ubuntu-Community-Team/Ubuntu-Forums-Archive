---
title: "Another &quot;Not enough free disk space&quot; question"
date: 2020-07-22
forum: Installation &amp; Upgrades
---

### Post by osp001 on 2020-07-22
I'm not new to Ubuntu, but I'm certainly no pro. I've tried to update several times, done the usual (sudo apt-get autoremove, sudo apt autoremove --purge, sudo apt-get autoremove --purge, run Janitor in Tweak), and, well- here's the dpkg --list 'linux-*'. Any advice?

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  linux-base     4.5ubuntu1.1 all          Linux image base package
un  linux-doc-4.15 <none>       <none>       (no description available)
ii  linux-firmware 1.173.18     all          Firmware for Linux kernel drivers
un  linux-firmware <none>       <none>       (no description available)
ii  linux-generic  4.15.0.101.9 amd64        Complete Generic Linux kernel and
un  linux-headers  <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
ii  linux-headers- 4.15.0-101.1 all          Header files related to Linux ker
ii  linux-headers- 4.15.0-101.1 amd64        Linux kernel headers for version 
un  linux-headers- <none>       <none>       (no description available)
ii  linux-headers- 4.15.0.101.9 amd64        Generic Linux kernel headers
un  linux-image    <none>       <none>       (no description available)
ii  linux-image-4. 4.15.0-101.1 amd64        Signed kernel image generic
un  linux-image-4. <none>       <none>       (no description available)
ii  linux-image-ge 4.15.0.101.9 amd64        Generic Linux kernel image
un  linux-image-un <none>       <none>       (no description available)
ii  linux-image-un 4.15.0-76.86 amd64        Linux kernel image for version 4.
un  linux-initramf <none>       <none>       (no description available)
un  linux-kernel-h <none>       <none>       (no description available)
un  linux-kernel-l <none>       <none>       (no description available)
ii  linux-libc-dev 4.15.0-109.1 amd64        Linux Kernel Headers for developm
ii  linux-modules- 4.15.0-101.1 amd64        Linux kernel extra modules for ve
ii  linux-modules- 4.15.0-76.86 amd64        Linux kernel extra modules for ve
ii  linux-modules- 4.15.0-101.1 amd64        Linux kernel extra modules for ve
un  linux-restrict <none>       <none>       (no description available)
ii  linux-sound-ba 1.0.25+dfsg- all          base package for ALSA and OSS sou
un  linux-source-4 <none>       <none>       (no description available)
un  linux-tools    <none>       <none>       (no description available)
```

I hope I'm doing this right, my apologies if not.

---

### Post by deadflowr on 2020-07-22
We'd need to know more about the space allocated.
Post back the results of both these
```
df -h
df -i
```
The first will give the actual space,
but the the other will give the inodes used.
It's rare, but it has happen where the inodes have been used up.
They should give an idea of what you're working with, and perhaps some common areas to look at to reduce the used space.

Use code tags whenever posting output from a terminal,
as code tags will keep the proper formatting.
More on code tags here: [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

---

### Post by ActionParsnip on 2020-07-23
Try:
```

sudo apt update 
sudo apt --purge autoremove 
sudo apt clean 

```

---

### Post by TheFu on 2020-07-23
> **ActionParsnip said:**
> Try:
```

sudo apt update 
sudo apt --purge autoremove 
sudo apt clean 

```

The OP already did.   See the #1 post.

---

### Post by osp001 on 2020-07-23
Output of ```
df -h
```

```

Filesystem                   Size  Used Avail Use% Mounted on
udev                         3.8G     0  3.8G   0% /dev
tmpfs                        784M  3.5M  781M   1% /run
/dev/mapper/ubuntu--vg-root  102G   41G   57G  42% /
tmpfs                        3.9G   81M  3.8G   3% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop0                   161M  161M     0 100% /snap/gnome-3-28-1804/116
/dev/loop2                   384K  384K     0 100% /snap/gnome-characters/550
/dev/loop1                    97M   97M     0 100% /snap/core/9665
/dev/loop3                   2.5M  2.5M     0 100% /snap/gnome-calculator/730
/dev/loop5                   2.3M  2.3M     0 100% /snap/gnome-system-monitor/148
/dev/loop6                    63M   63M     0 100% /snap/gtk-common-themes/1506
/dev/loop8                   1.0M  1.0M     0 100% /snap/gnome-logs/100
/dev/loop4                    37M   37M     0 100% /snap/remmina/4267
/dev/loop7                   256M  256M     0 100% /snap/gnome-3-34-1804/36
/dev/loop9                   141M  141M     0 100% /snap/gnome-3-26-1604/100
/dev/loop10                  256M  256M     0 100% /snap/gnome-3-34-1804/33
/dev/loop11                   55M   55M     0 100% /snap/core18/1880
/dev/loop13                  1.0M  1.0M     0 100% /snap/gnome-logs/93
/dev/loop14                  2.5M  2.5M     0 100% /snap/gnome-calculator/748
/dev/loop12                  384K  384K     0 100% /snap/gnome-characters/539
/dev/loop16                   55M   55M     0 100% /snap/gtk-common-themes/1502
/dev/loop18                   55M   55M     0 100% /snap/core18/1754
/dev/loop20                  2.3M  2.3M     0 100% /snap/gnome-system-monitor/145
/dev/loop15                  162M  162M     0 100% /snap/gnome-3-28-1804/128
/dev/loop17                  141M  141M     0 100% /snap/gnome-3-26-1604/98
/dev/loop19                   97M   97M     0 100% /snap/core/9436
/dev/loop21                   37M   37M     0 100% /snap/remmina/4260
/dev/sda1                    236M  120M  105M  54% /boot
tmpfs                        784M   20K  784M   1% /run/user/124
tmpfs                        784M   48K  784M   1% /run/user/1000
/home/aaron/.Private         102G   41G   57G  42% /home/aaron

```

Output of ```
df -i
```

```

Filesystem                   Inodes  IUsed   IFree IUse% Mounted on
udev                         995355    549  994806    1% /dev
tmpfs                       1003498   1122 1002376    1% /run
/dev/mapper/ubuntu--vg-root 6799360 252927 6546433    4% /
tmpfs                       1003498     87 1003411    1% /dev/shm
tmpfs                       1003498      6 1003492    1% /run/lock
tmpfs                       1003498     18 1003480    1% /sys/fs/cgroup
/dev/loop0                    27755  27755       0  100% /snap/gnome-3-28-1804/116
/dev/loop2                      230    230       0  100% /snap/gnome-characters/550
/dev/loop1                    12862  12862       0  100% /snap/core/9665
/dev/loop3                     1318   1318       0  100% /snap/gnome-calculator/730
/dev/loop5                      784    784       0  100% /snap/gnome-system-monitor/148
/dev/loop6                    62342  62342       0  100% /snap/gtk-common-themes/1506
/dev/loop8                      355    355       0  100% /snap/gnome-logs/100
/dev/loop4                     4224   4224       0  100% /snap/remmina/4267
/dev/loop7                    24339  24339       0  100% /snap/gnome-3-34-1804/36
/dev/loop9                    27624  27624       0  100% /snap/gnome-3-26-1604/100
/dev/loop10                   24339  24339       0  100% /snap/gnome-3-34-1804/33
/dev/loop11                   10756  10756       0  100% /snap/core18/1880
/dev/loop13                     353    353       0  100% /snap/gnome-logs/93
/dev/loop14                    1351   1351       0  100% /snap/gnome-calculator/748
/dev/loop12                     230    230       0  100% /snap/gnome-characters/539
/dev/loop16                   47984  47984       0  100% /snap/gtk-common-themes/1502
/dev/loop18                   10764  10764       0  100% /snap/core18/1754
/dev/loop20                     784    784       0  100% /snap/gnome-system-monitor/145
/dev/loop15                   27798  27798       0  100% /snap/gnome-3-28-1804/128
/dev/loop17                   27631  27631       0  100% /snap/gnome-3-26-1604/98
/dev/loop19                   12780  12780       0  100% /snap/core/9436
/dev/loop21                    4224   4224       0  100% /snap/remmina/4260
/dev/sda1                     62248    313   61935    1% /boot
tmpfs                       1003498     26 1003472    1% /run/user/124
tmpfs                       1003498     43 1003455    1% /run/user/1000
/home/aaron/.Private        6799360 252927 6546433    4% /home/aaron

```

Let's see if I got the code thing right.

---

### Post by TheFu on 2020-07-23
A+ on the code tags.

Not showing cruft makes finding what's important easier for you and us.  We care about real storage, not fake/virtual file storage, right?  Some better commands that don't include the cruft ... 

This command hides non-storage-impacting mounts:
```
 $ df -**hT** -x squashfs -x tmpfs -x devtmpfs
```

This command shows inode use:
```
 $ df -**iT** -x squashfs -x tmpfs -x devtmpfs
```

And when you just want to find large files, use:
```
 $ find **/** -type f -size **+1G**
```
Tweak the size for your needs. I start big, perhaps 3G and move lower, 1G, 600M, 300M, ...  of course, if you mix video files in with all the other files on the system, this won't be too useful.  I keep all media files in specific storage, not connected to the OS, so when it fills up, the OS doesn't break.

And when you don't really know where all the storage being used is located, there are many, many, ways to get lists of directories by storage use below.  There are some tools specifically for that.  But because I work no servers and many aren't "mine", I need to use the built-in tools.
```
 $ sudo du -sh *|sort -h
```
That gets the list of storage used for the current directory in "human" readable output, then sorts it, also "human" format, so it knows 1G is larger than 999M.  Very handy.  The sort can be reversed, but usually I want to work on the major problem directories, which will be at the bottom of the list with that command.
For example:
```
 $ cd /var
 $ sudo du -sh *|sort -h
 0       lock
 0       run
 4.0K    crash
 4.0K    local
 4.0K    mail
 4.0K    opt
 1.1M    spool
 15M     backups
 161M    log
 167M    cache
 358M    tmp
** 24G     lib**

```
/var/lib/ is using 24G which is much larger than all the other areas in /var/.  Time to move down and repeat:
```
 $ cd /var/lib
 $ sudo du -sh *|sort -h
   ...
 86M     dpkg
 150M    dkms
 181M    apt
 **7.5G**    libvirt
 **16G**     lxd
```
lxd and libvirt using lots of storage makes perfect sense.  lxd holds containers and libvirt holds some virtual machines.  Last week, /var/log/ was using 6G.  THAT was a problem with a runaway log file. I have a daily task that reports on high disk usage - logwatch is the tool. At about 630am that same day, the log directory was about 200MB. By 11am, it was over 6GB.  Found the offending process and log file. Shutdown the process, compressed the log file ... it refused, not enough working space, so I tried to remove some older logs to make room for compression to work and failed.  That one log file was 1000x larger than all the others for the last 10 weeks. I didn't have much time to figure out the root cause, so I deleted the log, restarted the process and setup a monitor for every 15 minutes to let me know when/if that specific log file exploded again.  It has been at least 5 days without any issues.  Just checked it.
```
$ ll mailbox.log
-rw-r----- 1 zimbra zimbra 5041183 Jul 23 19:12 mailbox.log
```
It is 5MB, so whatever the issue was, it hasn't reoccurred.

---

### Post by Impavidus on 2020-07-24
Your /boot partition is only 236MB, which is tiny. I worked in the past, but the initramdisk image slowly gets larger over time, so there is a point when it no longer works. You may be able to remove kernel 4.15.0-76, then run the upgrade. The system keeps one old kernel and removes it after a new one is installed, so you temporarily have three. But you have to remove it before installing a new one, having just one when starting the upgrade.

The next time you install Ubuntu, make sure your /boot partition is larger.

---

### Post by TheFu on 2020-07-24
In my experience doing system release upgrades, the old kernel is retained forever, unless I manually remove it - usually 6-12 months later.  I just removed some kernels after doing a 16.04 HWE upgrade.  Also, 3 kernels in the current line are retained by APT.
```
$ ll /boot/vmlinuz*
lrwxrwxrwx 1 root root       24 Jul 22 06:35 /boot/vmlinuz -> vmlinuz-5.4.0-42-generic
-rw------- 1 root root 11662080 May 21 08:38 /boot/vmlinuz-5.4.0-33-generic
-rw------- 1 root root 11662080 Jun 22 17:07 /boot/vmlinuz-5.4.0-40-generic
-rw------- 1 root root 11662080 Jul  9 20:04 /boot/vmlinuz-5.4.0-42-generic
lrwxrwxrwx 1 root root       24 Jul 22 06:35 /boot/vmlinuz.old -> vmlinuz-5.4.0-40-generic
```
That is a 20.04 system, patched weekly.

```
$ ll /boot/vmlinuz*
-rw------- 1 root root 8199584 Jun  9 13:54 /boot/vmlinuz-4.15.0-106-generic
-rw------- 1 root root 8198944 Jun 13 10:08 /boot/vmlinuz-4.15.0-107-generic
-rw------- 1 root root 8181016 Sep 19  2019 /boot/vmlinuz-4.15.0-65-generic
```
16.04 HWE system, also patched weekly. No idea why "65" is still around. Seems there would have been lots of kernels since then.

And an other 16.04 which recently had the HWE upgrade performed:
```
$ ll /boot/vmlinuz-4.*
-rw------- 1 root root 8199584 Jun  9 13:54 /boot/vmlinuz-4.15.0-106-generic
-rw------- 1 root root 8198944 Jun 13 10:08 /boot/vmlinuz-4.15.0-107-generic
-rw------- 1 root root 7214112 Jun 10 10:08 /boot/vmlinuz-**4.4**.0-185-generic
```
Perhaps HWE has something to do with the kernel removal policies?

It is interesting to see the added bloat in the newer kernels.

If I remember during installation, I'll create /boot/ to be 700+MB.  I don't always remember to do that, but most of my systems are virtual machines which aren't THAT hard to fix later once an understanding of partitions and booting is known.  If booting is still magical, there's little chance to easily fix anything.

---

### Post by osp001 on 2020-07-24
Hmmm. I've always kept this laptop as a "sacrificial" computer, in case it got lost or stolen I wouldn't be very upset. When I installed Ubuntu originally, the partition was larger than was recommended at the time, but it's clearly time to upgrade- either a new computer, or just completely scrub this one with a much larger partition for /boot. I'm just not up to playing with partition sizes- a quick search shows this is fraught with peril.

Thanks to everyone for their insights; I appreciate your patience with this noob.

---

### Post by CatKiller on 2020-07-24
> **osp001 said:**
> I'm just not up to playing with partition sizes- a quick search shows this is fraught with peril.

There are failure modes that are a pain to recover from: formatting the partition that held the priceless data that you've never backed up, power cut in the middle of an operation, that kind of thing. 

If you know what you've already got, and you know what you're trying to achieve, and what you want to end up with, it's pretty straightforward. Drag some things around, hit apply, wait for it to finish. 

You can't fiddle with a mounted partition, so partition editing is best done from a live USB. All of the flavours come with a partition editor, since it's part of the install process. 

Backing up important data is essential even if you don't fiddle around with partitions: drives can die without any warning. If you've sensibly backed up your data anyway, there's nothing that can't be fixed if a partition edit goes awry.

Not that I'm saying you *should* fiddle with your partitions, just that you shouldn't fear doing so. Treat the process, and your data, with the appropriate level of respect.

---

### Post by pbear42 on 2020-07-24
> **osp001 said:**
> I'm just not up to playing with partition sizes- a quick search shows this is fraught with peril.
Modifying the boot partition would be trivial.  It's making room for its expansion which would be tricky.  This is encrypted system, right?  Besides, it's not necessary.  The boot partition is only 54% full according to your **df** report (and using only 1% of its inodes).  Whatever the problem, that's not it.

---

