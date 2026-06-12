---
title: "/home won't mount in fresh install"
date: 2019-08-21
forum: Installation &amp; Upgrades
---

### Post by MibunoOokami on 2019-08-21
Hi all.
 
 
 I need some help please.  
 
 
 After reinstalling Ubuntu, my /home partition isn’t being mounted and used. When I edited /etc/fstab to mount and use /home partition, then rebooted, I entered my password, the screen went blank for about a second, then came right back to the login screen. This happened a few times so I used tty2 to delete my entry in fstab, and now I can login normally, but no /home partition.
 
 
 This should’ve been straightforward but wasn’t, if you can tell me, I’d like to know why? But ultimately, I would like to know how to fix this so that /home will mount and I can login.

---

### Post by TheFu on 2019-08-21
Show output of
```
more /etc/fstab
df -hT
lsblk
sudo fdisk -l

```
to start after you boot into the OS.

If you use UUIDs in the fstab, **blkid **can help.

Also would be good to know the release and DE being used.

---

### Post by Bashing-om on 2019-08-21
MibunoOokami; Hello -

see TheFu's last.

for reference my working fstab with separate partitions:
```

sysop@x1804mini:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=1460de17-30e4-4566-b181-18c17b62887a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=5cd50446-1330-4130-a521-1ea936c9fc2a /home           ext4    defaults        0       2
# /var was on /dev/sdb3 during installation
UUID=69b1f02a-5e00-415e-ab75-78fdd63f72a3 /var            ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=8d4743bc-8e47-4650-b5fd-1ea904d4ecda none            swap    sw              0       0
sysop@x1804mini:~$ 

```

Tutorials:
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
[https://ubuntuforums.org/showthread.php?t=2337233](https://ubuntuforums.org/showthread.php?t=2337233)

[INDENT][INDENT]my bit to try and help[/INDENT][/INDENT]

---

### Post by MibunoOokami on 2019-08-21
Thanks for the quick replies
 
 
 ```
more /etc/fstab
 # /etc/fstab: static file system information.
 #
 # Use 'blkid' to print the universally unique identifier for a
 # device; this may be used with UUID= as a more robust way to name devices
 # that works even if disks are added and removed. See fstab(5).
 #
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
 # / was on /dev/sda3 during installation
 UUID=2a4416e8-7ffa-4201-9ac3-eb9e67f571f9 /               ext4    errors=remount
 -ro 0       1
 # /boot/efi was on /dev/sda1 during installation
 UUID=D852-8D98  /boot/efi       vfat    umask=0077      0       1
 # swap was on /dev/sda2 during installation
 UUID=3c5b3476-f725-47e2-b593-1e2e1cf4f4a7 none            swap    sw             
   0       0
```
 ```
df -hT
 Filesystem     Type      Size  Used Avail Use% Mounted on
 udev           devtmpfs  3.7G     0  3.7G   0% /dev
 tmpfs          tmpfs     749M  1.8M  747M   1% /run
 /dev/sda3      ext4       29G  5.0G   22G  19% /
 tmpfs          tmpfs     3.7G     0  3.7G   0% /dev/shm
 tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
 tmpfs          tmpfs     3.7G     0  3.7G   0% /sys/fs/cgroup
 /dev/loop0     squashfs   87M   87M     0 100% /snap/core/4917
 /dev/loop1     squashfs   15M   15M     0 100% /snap/gnome-logs/37
 /dev/loop2     squashfs   13M   13M     0 100% /snap/gnome-characters/103
 /dev/loop3     squashfs  2.4M  2.4M     0 100% /snap/gnome-calculator/180
 /dev/loop4     squashfs   35M   35M     0 100% /snap/gtk-common-themes/319
 /dev/loop5     squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/70
 /dev/loop6     squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/51
 /dev/sda1      vfat      487M  6.1M  480M   2% /boot/efi
 tmpfs          tmpfs     749M   16K  749M   1% /run/user/121
 tmpfs          tmpfs     749M   44K  749M   1% /run/user/1000
```
 ```
lsblk
 NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
 loop0    7:0    0  86.9M  1 loop /snap/core/4917
 loop1    7:1    0  14.5M  1 loop /snap/gnome-logs/37
 loop2    7:2    0    13M  1 loop /snap/gnome-characters/103
 loop3    7:3    0   2.3M  1 loop /snap/gnome-calculator/180
 loop4    7:4    0  34.7M  1 loop /snap/gtk-common-themes/319
 loop5    7:5    0 140.9M  1 loop /snap/gnome-3-26-1604/70
 loop6    7:6    0   3.7M  1 loop /snap/gnome-system-monitor/51
 sda      8:0    0 931.5G  0 disk  
 &#9500;&#9472;sda1   8:1    0   487M  0 part /boot/efi
 &#9500;&#9472;sda2   8:2    0  15.3G  0 part [SWAP]
 &#9500;&#9472;sda3   8:3    0  28.6G  0 part /
 &#9492;&#9472;sda4   8:4    0 887.2G  0 part  
 sr0     11:0    1  1024M  0 rom 
```
 ```
sudo fdisk -l
 Disk /dev/loop0: 86.9 MiB, 91099136 bytes, 177928 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop1: 14.5 MiB, 15196160 bytes, 29680 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop2: 13 MiB, 13619200 bytes, 26600 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop3: 2.3 MiB, 2433024 bytes, 4752 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop4: 34.7 MiB, 36323328 bytes, 70944 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop5: 140.9 MiB, 147722240 bytes, 288520 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop6: 3.7 MiB, 3887104 bytes, 7592 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 Disklabel type: gpt
 Disk identifier: A33B5D56-DF82-40AF-B36C-554BB755AE12
 
 
 Device        Start        End    Sectors   Size Type
 /dev/sda1      2048     999423     997376   487M EFI System
 /dev/sda2    999424   32999423   32000000  15.3G Linux swap
 /dev/sda3  32999424   92999679   60000256  28.6G Linux filesystem
 /dev/sda4  92999680 1953523711 1860524032 887.2G Linux filesystem
```
 
 
 What I did the first time was add a line ```
/dev/sda4 / home ext4 defaults 0 2
``` and had the login problem, so deleted that line, rebooted then added ```
UUID=XXXXXXXXX /dev/sda4 / home ext4 defaults 0 2
``` same login problem so deleted that.
 
 
 The Xs are representative only, not the actual UUID.
 
 
 Details are Ubuntu 18.04 with default DE
 
 
 Looking at Bashing’s example, I take it I just need to remove /dev/sda4 from the equation? I’ll wait for confirmation first

---

### Post by Bashing-om on 2019-08-21
MibunoOokami; Well ...

and there is a space in "/ home" that is also to be removed.

Shoukd then

[INDENT][INDENT]workie great
[/INDENT][/INDENT]

---

### Post by MibunoOokami on 2019-08-21
> **Bashing-om said:**
> MibunoOokami; Well ...

and there is a space in "/ home" that is also to be removed.

Shoukd then
[INDENT][INDENT]workie great
[/INDENT]
[/INDENT]


  	 	 	 	   Oh, that was a typo just now that I copied and pasted :redface:. 

Will give that a go and report back. Thanks

---

### Post by MibunoOokami on 2019-08-21
Hmm… That reproduced the same problem. I notice in fstab I notice there’s quite a bit of space between the information, particularly between ```
<mount point> <type> <options> <dump> <pass>
``` does that actually make a difference since I’ve only used a single space between them?

---

### Post by TheFu on 2019-08-21
When posts aren't properly what is ACTUALLY on the system, it makes it impossible for us to figure out the truth.  Please be VERY careful and post exact data so we don't waste your time.

The number of spaces doesn't matter between different parts of the line, but the options CANNOT have any spaces.
Also, the paste above shows a line wrap problem.  1-line for 1 mount point.  Not 2.

```
UUID=2a4416e8-7ffa-4201-9ac3-eb9e67f571f9 /               ext4    errors=remount
 -ro 0       1
```
is wrong.
```
UUID=2a4416e8-7ffa-4201-9ac3-eb9e67f571f9     /    ext4    errors=remount-ro     0   1
```
is probably correct.

---

### Post by MibunoOokami on 2019-08-22
> **TheFu said:**
> When posts aren't properly what is ACTUALLY on the system, it makes it impossible for us to figure out the truth.  Please be VERY careful and post exact data so we don't waste your time.

Do you mean by not posting the actual UUID? With the exception of the lines which I added to fstab, everything else is pasted directly from terminal.
 
 
 Just so we’re all on the same page:
 
 
 The first time I edited fstab I added the line ```
/dev/sda4 /home ext4 defaults 0 2
``` in my post just before where there is a space between / and home, that was because I typed it by hand and accidentally put that space in there only in this thread not in the actual fstab file.
 
 
 The second time I edited fstab was after deleting the first line, then added this line ```
UUID=01662257-3f4b-4b0b-8fd3-31e663be117e /dev/sda4 /home ext4 defaults 0 2
``` again in my earlier post, I copied and pasted what I typed out for the thread and that’s why the space between / and home appeared again. That is the actual UUID.
 
 
 The third time I edited fstab, again after deleting the last entry, I tried it per Bashing’s suggestion and added the line ```
UUID=01662257-3f4b-4b0b-8fd3-31e663be117e /home ext4 defaults 0 2
```
 
 
 All three attempts produced the same login problem.

---

### Post by SeijiSensei on 2019-08-22
Do you have the same user ID now that you had before? 

Boot into recovery mode, then run
```

mount -o remount,rw /
mount /dev/sda4 /opt
ls -ln /opt

```

What user id (e.g., 1000) is assigned to your home directory?  Now run
```
grep yourusername /etc/passwd
```

Same ID or different?

If you were the first user, and the one with sudo privileges, on both installs you should have ID 1000.

---

### Post by TheFu on 2019-08-22
At the risk of having too many cooks, 
```
UUID=01662257-3f4b-4b0b-8fd3-31e663be117e /home ext4 defaults 0 2
```
could be correct, probably is. Cannot tell for certain without the **blkid** output.

I'm assuming there is an ext4 file system built on that device (the UUID).

There is an Ubuntu Guide for moving HOME directories.  [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) 
Perhaps those steps will be clearer?

The main things are:
[LIST=1]
[*]mount the device with a file system to the correct place.
[*]ensure there is a directory with the userid's HOME in the place that the /etc/passwd file shows for that specific userid.  Probably /home/mibuno  after the new partition is correctly mounted.
[*]ensure the HOME directory is owned by the userid.
[/LIST]
Even if the HOME directory isn't there, a correct userid login should still work and just drop the user into /.  Try logging in without using a GUI.  Pick a different tty - <cntl><alt>-F2  or <cntl><alt>-F3 should work. 
 
When you mount /dev/sda4 onto /home/ and of the files below /home/ that are on the old disk will still be there if you don't delete them. They will be inaccessible. If there are just a few files and they are tiny, I wouldn't worry about it.  The guide above addresses cleaning that up.

---

### Post by MibunoOokami on 2019-08-22
> **SeijiSensei said:**
> Do you have the same user ID now that you had before? 

Boot into recovery mode, then run...

                        This is probably a daft question, but when you say recovery mode, you mean a live session right?  
 I did use the same username and password, but will confirm with the output as soon as practicable.

> **TheFu said:**
> At the risk of having too many cooks, 
```
UUID=01662257-3f4b-4b0b-8fd3-31e663be117e /home ext4 defaults 0 2
```
could be correct, probably is. Cannot tell for certain without the **blkid** output.

I'm assuming there is an ext4 file system built on that device (the UUID).



Apologies for not posting the blkid output sooner, I had simply copied the info from the partition's properties.

```
sudo blkid /dev/sda4
/dev/sda4: UUID="01662257-3f4b-4b0b-8fd3-31e663be117e" TYPE="ext4" PARTUUID="43006698-a414-47ba-b469-ffdf5bb857e1"

```

I'll check that link and try those instructions soon.

---

### Post by TheFu on 2019-08-22
Looks like that mount should work fine.  Just need to fix the HOME directory, probably.

This is one of those tasks that conceptually is really easy, but there are 10 decision points along the way and explaining each step for all the different possible decisions is very hard.
The key for all Unix file system stuff is that as long as the new storage appears to be in the correct place, with the correct permissions, with the correct ownership and group, then everything will be fine. That is the task here.

You can ignore everything below ... 

Another option is to abandon /home/ completely and make a new place for the HOME of the few userids you care about and put those into /etc/passwd file entries for each userid, as needed.  That is a valid option too.  There's **nothing** special about the /home/ directory - nothing.  It is just very common for home installs.  Each userid can have their HOME on different storage, if you like. As long as the passwd entry for each userid points to filesystem/directory where there is a directory setup as a proper HOME, that's all that matters.  In specialized environments, sometimes having multiple userids sharing the same HOME makes sense - these would be non-graphical setups, but it is possible to handle those too with judicious environment variable management.

---

### Post by SeijiSensei on 2019-08-23
> **MibunoOokami said:**
> This is probably a daft question, but when you say recovery mode, you mean a live session right?
No, it's an [option in the boot menu]("https://wiki.ubuntu.com/RecoveryMode").  If you don't see the boot menu, hold down the Shift key while booting. Recovery mode will start Ubuntu in "single-user" mode and present a menu of options.  Choose the "root shell" option, and you'll end up at a prompt with root privileges.  The filesystem is mounted as read-only by default, so you need to make it writable with "mount -o rw,remount /".

---

### Post by MibunoOokami on 2019-08-24
I'm still currently reading the guide to moving /home directory, want to make sure I understand it properly.

> **SeijiSensei said:**
> No, it's an [option in the boot menu]("https://wiki.ubuntu.com/RecoveryMode").  If you don't see the boot menu, hold down the Shift key while booting. Recovery mode will start Ubuntu in "single-user" mode and present a menu of options.  Choose the "root shell" option, and you'll end up at a prompt with root privileges.  The filesystem is mounted as read-only by default, so you need to make it writable with "mount -o rw,remount /".

I’m glad I asked first.

After running those commands, the output of “la -ln /opt” is
```
total 20
drwx------ 2 0 0 16384 Aug 14 15:18 lost+found
dr-x------ 2 1000 1000 4096 Aug 21 23:27 username
```
Is that what we’re expecting to see?

The ID grep command produced the following
```
usernamex:1000:username,,,:/home/username:/bin/bash
```
The username appears the same three times in red lettering.

---

### Post by TheFu on 2019-08-24
usernamex seems to be yet another typo.  Typos are killing you, at least in this thread .... So you would login using 
"usernamex"
and be placed into /home/username as the PWD.

The normal permissions would be 775 on a HOME directory.  755, 750 would all be reasonable too.  The 500 permissions shown are unusual and I bet many Gnome programs would fail to work. They don't handle not being allowed to write to ~/.config/ well.

---

### Post by SeijiSensei on 2019-08-24
> **MibunoOokami said:**
> 
After running those commands, the output of &#8220;la -ln /opt&#8221; is
```
total 20
drwx------ 2 0 0 16384 Aug 14 15:18 lost+found
dr-x------ 2 1000 1000 4096 Aug 21 23:27 username
```
Is that what we&#8217;re expecting to see?
UID 1000 is the one assigned to the first user on the machine, so yes, it's probably correct.  However, as The Fu says, not having write privileges in your own home directory can cause lots of problems.  At a minimum you should have 750 permissions; the Ubuntu default is 755.  Either of those grants you as the owner full access to the directory.  The other two options grant read and list permissions to either other members of your user group (750), or all other users on the machine (755). Usually there isn't anyone other than you in your group unless you explicitly assign other users to it.

So if you follow those same steps to mount the partition to /opt, then run
```

cd /opt
chmod 755 username

```
I'd do a listing of the files in your home directory (ls -l username) to see if they have the wrong permissions as well. Or you can just run
```

chmod u+w username -R

```
to make all the files in the username directory writable by you.

---

### Post by TheFu on 2019-08-24
I don't know what 
```
$ la -ln
la: command not found
```
is supposed to return, but the number being shown for an** ls -al** means the password file and username can't be resolved from the passwd DB. Running from a *live-boot* or *rescue* environment, that is to be expected.  After correcting the permissions as SeijiSensei recommends and booting into the normal environment, it should be

```
drwxrwxr-x 2 usernamex username 4096 Aug 21 23:27 username
```
assuming the typo in the passwd file shown above is left there username**x**
Those would be the expected, normal, Ubuntu permissions.

Typos are killing me.

---

### Post by SeijiSensei on 2019-08-24
I told him to use "ls -ln" which generates the output he presented. The -n switch lists users and groups by numeric ID rather than name.

---

### Post by TheFu on 2019-08-24
> **SeijiSensei said:**
> I told him to use "ls -ln" which generates the output he presented. The -n switch lists users and groups by numeric ID rather than name.

More typos in  MibunoOokami posts.  Very frustrating.

---

### Post by MibunoOokami on 2019-08-24
I am sorry for the frustration I’m causing, I have some time constraints and chose to do this one late at night right before bed. I have no idea how to save the outputs so that I could copy and paste them here, so had to take them down by hand. Oddly enough, having run the commands again, then comparing my notes, I had them copied correctly, I just typed them incorrectly.

This time I spent a good thirty minutes triple checking that I’ve typed them without typos, and trust me when I say, typos frustrate me too because they’re wasting everyone’s time. 

Note: "lost+found" and "username" actually are coloured blue in ls -ln output. As said earlier "username" is coloured red in grep output.

```
root@username:~# ls -ln /opt
total 20
drwx------ 2 0 0 16384 Aug 14 15:18 lost+found
dr-x------ 2 1000 1000 4096 Aug 21 23:27 username
```
```
root@username:~# grep username /etc/passwd
username:x:1000:1000:username,,,:/home/username:/bin/bash
```

One question I have at the moment is, how would my permissions have changed without my permission? (no pun intended). 
In the past when I had encountered permissions issues it was because I was copying directories and files incorrectly, this is something I overcame with the help of the people on this forum, probably yourselves actually, some time ago now.

---

### Post by MibunoOokami on 2019-08-25
I allowed myself to get distracted by the different posts here that I hadn’t finished reading or trying the suggestions from the link in post #11. 

Given the time spent and frustrations caused, I figured I would give it a go and if I can’t get the partition to mount the way I expect, I’ll cut my losses and do a complete re-install…

Praise the Lord, the instructions in that thread worked perfectly for mounting the /home partition and letting me log in properly. What it seems to have boiled down to was moving the /home directory that got created at install into a renamed directory and then edit fstab the way I had in the first place and that’s it. I presume the login problem was the machine was trying to load the partition to the place where the directory was. 

Again I apologise for the typo frustrations. I don’t know what the story is with the permissions thing we saw earlier, here is the new output from /home, I notice there’s a “w” where a – was now.
```
ls -ln /home/
total 28
drwx------  2    0    0 16384 Aug 14 15:18 lost+found
drwx------ 32 1000 1000 12288 Aug 25 16:27 username
```

Thanks for your help everyone, and for bearing with me.

---

