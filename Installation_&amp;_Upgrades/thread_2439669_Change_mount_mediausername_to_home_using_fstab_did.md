---
title: "Change mount /media/username to /home using fstab didn't work"
date: 2020-03-30
forum: Installation &amp; Upgrades
---

### Post by qianian2 on 2020-03-30
Hi, I forgot to set my home partition to /home mount point during a clean reinstall so it automatically was mounted at /media/username. 

Instead of starting over the reinstall, I defined the UUID in fstab, mounted, then changed /media/username to /home in fstab and mounted again. At first all the files disappeared from all the directories involved. After reboot, I have the default empty directories in /home and nothing under /media. Even the partial backup I made in a new folder (/media/home) disappeared. 

I'd really appreciate an explanation of what might have happened. Please let me know any additional information I can post. 

Thanks and be safe, everyone.

---

### Post by TheFu on 2020-03-31
Post the fstab file and the passwd entry for the users of the system.

Also, the file system for HOME must be capable of supporting Unix permissions, so NTFS or any of the FAT-whatever file systems cannot be used.

Any existing files that were _under_ the /home/ directory will be hidden of another partition is mounted over it.

---

### Post by qianian2 on 2020-03-31
Thanks for the help. I'd appreciate step-by-step instructions for further action.

/etc/fstab follows. I added the last 2 lines. The home partition is ext4
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=39d20bad-b9bd-45ed-a709-531b9e3a5b66 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=af6172b2-c4a3-443b-8a40-b21fb3cb6a97 none            swap    sw              0       0
# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings)
UUID=18eecef8-913b-4019-abce-3e06f69b10df   /home    ext4          defaults       0       2


```

/etc/passwd

```
speech-dispatcher:x:111:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/falsewhoopsie:x:112:117::/nonexistent:/bin/false
kernoops:x:113:65534:Kernel Oops Tracking Daemon,,,:/:/usr/sbin/nologin
saned:x:114:119::/var/lib/saned:/usr/sbin/nologin
pulse:x:115:120:PulseAudio daemon,,,:/var/run/pulse:/usr/sbin/nologin
avahi:x:116:122:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/usr/sbin/nologin
colord:x:117:123:colord colour management daemon,,,:/var/lib/colord:/usr/sbin/nologin
hplip:x:118:7:HPLIP system user,,,:/var/run/hplip:/bin/false
geoclue:x:119:124::/var/lib/geoclue:/usr/sbin/nologin
gnome-initial-setup:x:120:65534::/run/gnome-initial-setup/:/bin/false
gdm:x:121:125:Gnome Display Manager:/var/lib/gdm3:/bin/false
keizen:x:1000:1000:Keizen,,,:/home/keizen:/bin/bash



```

---

### Post by TheFu on 2020-03-31
Does /home/keizen exist?  
is it owned by keizen?
Were the files in /home/ moved onto the new storage prior to the new storage being mounted over /home?

What does** ls -al /home/ s**how?  Please use *code tags* when posting that output.

---

### Post by qianian2 on 2020-03-31
```
~$ ls -al /home/total 12
drwxr-xr-x  3 keizen keizen 4096 Mar 30 17:48 .
drwxr-xr-x 24 root   root   4096 Mar 30 13:11 ..
drwxrwxrwx 19 keizen keizen 4096 Mar 31 09:40 keizen
```

> [COLOR=#000000]Where the files in /home/ moved onto the new storage PRior to the new storage being mounted over /home?[/COLOR]


Do you mean where did I move the default files in /home after clean reinstall? I didn't touch them. They were empty directories, same as what I see under /home/keizen now. 

Thanks again.

---

### Post by qianian2 on 2020-03-31
Iirc initially the permissions for /home/keizen were drwx------ and I used chmod to try to view hidden files. Obviously no luck.

---

### Post by TheFu on 2020-03-31
Those permissions are bad. You want:
```
/home$ ls -alF
total 44
drwxr-xr-x   5 root   root    4096 Sep 22  2019 ./
drwxr-xr-x  33 root   root    4096 Mar 21 09:12 ../
drwxr-xr-x   3 keizen keizen  4096 Sep 22  2019 keizen/
drwx------   2 root   root   16384 Feb 28  2019 lost+found/
```

See the root:root and permissions?
See the lost+found/ directory?  That gets created whenever a new file system gets created.  Not seeing one in the output above means that /home/ didn't get mounted.

On my box, using LVM, /home is mounted as, **df -Th**
```
/dev/mapper/ubuntu--vg-home--lv ext4   74G   20G   51G  28% /home
```

Because i use LVM, on an SSD, the fstab looks like this:
```
/dev/mapper/ubuntu--vg-home--lv /home  ext4 errors=remount-ro,noatime 0 2
```

i used **mkfs -t ext4** on the /dev/mapper/ubuntu--vg-home--lv to create the ext4 file system.  if the file system didn't get manually created, then that disk is probably formatted NTFS.  To check/verify, run 
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```

As you can guess, i'm using a shotgun method of troubleshooting.

---

### Post by qianian2 on 2020-03-31
> [COLOR=#000000]Not seeing one in the output above means that /home/ didn't get mounted.[/COLOR]

Is there a chance I can mount it after all? 

**/home$ df -Th**
```
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3.9G     0  3.9G   0% /dev
tmpfs          tmpfs     785M  1.7M  783M   1% /run
/dev/sda1      ext4       19G  6.5G   11G  38% /
tmpfs          tmpfs     3.9G  115M  3.8G   3% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop3     squashfs   92M   92M     0 100% /snap/core/8689
/dev/loop2     squashfs  1.0M  1.0M     0 100% /snap/gnome-logs/93
/dev/loop1     squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/135
/dev/loop0     squashfs   45M   45M     0 100% /snap/gtk-common-themes/1440
/dev/loop4     squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/127
/dev/loop5     squashfs  161M  161M     0 100% /snap/gnome-3-28-1804/116
/dev/loop7     squashfs   90M   90M     0 100% /snap/core/8268
/dev/loop6     squashfs   49M   49M     0 100% /snap/gtk-common-themes/1474
/dev/loop8     squashfs   15M   15M     0 100% /snap/gnome-characters/399
/dev/loop9     squashfs  1.0M  1.0M     0 100% /snap/gnome-logs/81
/dev/loop10    squashfs   55M   55M     0 100% /snap/core18/1668
/dev/loop11    squashfs  4.4M  4.4M     0 100% /snap/gnome-calculator/704
/dev/loop12    squashfs   55M   55M     0 100% /snap/core18/1705
/dev/loop13    squashfs  4.3M  4.3M     0 100% /snap/gnome-calculator/544
/dev/loop14    squashfs   15M   15M     0 100% /snap/gnome-characters/495
**/dev/sda5      ext4      202G  1.2G  191G   1% /home**
tmpfs          tmpfs     785M   48K  785M   1% /run/user/1000



```
My bolded line worries me because I should have way more than 1.2 G used in that 220 GB home partition. It is, however, ext4, so I still don't understand why my fstab procedure didn't work.
[B]
$ lsblk -e 7 -o name,size,type,fstype,mountpoint[/B]
```
NAME     SIZE TYPE FSTYPE MOUNTPOINT
sda    232.9G disk        
&#9500;&#9472;sda1  18.6G part ext4   /
&#9500;&#9472;sda2     1K part        
&#9500;&#9472;sda5   205G part ext4   /home
&#9492;&#9472;sda6   9.3G part swap   [SWAP]
sr0     1024M rom 
```

Thanks.

---

### Post by TheFu on 2020-03-31
> **qianian2 said:**
> Iirc initially the permissions for /home/keizen were drwx------ and I used chmod to try to view hidden files. Obviously no luck.

There aren't any hidden files on Unix, just files/dirs that begin with a . aren't displayed for convenience.  Seeing them is trivial.
ls -a

Looks like the missing lost+found/ is a 1-off.   The partition is definitely being mounted to /home/.
What, exactly, is the issue?  i seem to have lost track.  Appears that sda5 is mounted on /home/ from here.  i'm a little worried there isn't a lost+found directory in /home/lost+found.

Did you fix the permissions using the example provided?

---

### Post by TheFu on 2020-03-31
> **qianian2 said:**
>  
Do you mean where did I move the default files in /home after clean reinstall? I didn't touch them. They were empty directories, same as what I see under /home/keizen now. 

They aren't empty.  There are some .dotfiles and .dotdirs in there.  Don't trust any GUi. They lie.  Use** ls -a** to see what's in any directory.

To find missing files, use **ls -alR ** and** du -h *** to see where stuff is.  To see .dotfiles/.dotdirs, we need to use careful regex patterns.   **du -sh ~/.[a-Z]*** will show most of them.

---

### Post by qianian2 on 2020-03-31
If possible, I want to recover the contents of my home partition. It was mounted at /media/username by default and I used fstab to mount it at /home. If recovery is impossible, I want to know what I did to lose them. Thanks for any help.

[B]du -sh ~/.[a-Z]*
```
[/B]4.0K	/home/keizen/.bash_history427M	/home/keizen/.cache
564M	/home/keizen/.config
4.0K	/home/keizen/.gconf
16K	/home/keizen/.gnupg
4.0K	/home/keizen/.ICEauthority
1.6M	/home/keizen/.local
21M	/home/keizen/.mozilla
76K	/home/keizen/.pki
4.0K	/home/keizen/.ssh
0	/home/keizen/.sudo_as_admin_successful
2.4M	/home/keizen/.zoom


[B]
```

[/B]I used chmod again to get the following permissions, but there is still no lost + found.

```
/home$ ls -alFtotal 12
drwxr-xr-x  3 keizen keizen 4096 Mar 30 17:48 ./
drwxr-xr-x 24 root   root   4096 Mar 30 13:11 ../
drwxr-xr-x 19 keizen keizen 4096 Mar 31 09:40 keizen/



```

---

### Post by TheFu on 2020-03-31
> **qianian2 said:**
> If possible, I want to recover the contents of my home partition. It was mounted at /media/username by default and I used fstab to mount it at /home. If recovery is impossible, I want to know what I did to lose them. Thanks for any help.

Ah .... appears the error was that the HOME directory was mounted too high.

Needed .... 
/media/thefu ---->   /home/thefu
         but it appears this was done:
/media/thefu ---->   /home
    OR
mkdir /media/home ; mv /media/thefu /media/home/thefu
then mount it.

I’m  just guessing there.  Does that seem like what happened?  No idea what may have happened to the old files.  They should have been in /home/ somewhere.  Nothing automatic would delete them to my knowledge.

---

### Post by qianian2 on 2020-04-01
That's exactly what happened, thank you for explaining. So confusing -- I see /home/keizen but as we saw this is all that's in /home. Any possibility re-mounting it could give access to those contents?

```
keizen@Stonau:~$ ls -al ..total 12
drwxr-xr-x  3 keizen keizen 4096 Mar 30 17:48 .
drwxr-xr-x 24 root   root   4096 Mar 30 13:11 ..
drwxr-xr-x 19 keizen keizen 4096 Apr  1 08:32 keizen
```

---

### Post by TheFu on 2020-04-01
Can't hurt to try.

---

### Post by qianian2 on 2020-04-02
The output of TestDisk (sorry I only have [an image link]("https://drive.google.com/open?id=1DJaxXCZpoO_3eQ-dj7YdKvI-AUviHnID")) identifies two partitions that can't be recovered. They are identical in size (429786944) but the Start and End are off by 8 each. Does that mean there are two indices and can I recover my files?

Additionally TestDisk says The harddisk seems too small! Check the harddisk size: HD jumper settings, BIOS detection...

Is it possible mounting to /home without deleting the directories there by default caused my desired content to be hidden under the default ones? Any help is appreciated. Also should I clean up this post and re-post?

---

### Post by TheFu on 2020-04-02
i don't use testdisk.  i have "backups" instead, which seem to cause many fewer problems and less prayer is needed.
For dealing with file systems, sometimes it is easiest to boot from a "Try Ubuntu" flash installer and choose "Try Ubuntu" to look at the storage when it isn't actively being used by the running OS.

---

