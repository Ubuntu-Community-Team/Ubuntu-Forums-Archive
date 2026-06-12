---
title: "Paritions Make Sense?"
date: 2011-09-08
forum: Installation &amp; Upgrades
---

### Post by dedukes on 2011-09-08
Hi.

I just did a fresh install to 11.04.

When creating my partitions I followed, as best I could, [this post]("http://ubuntuforums.org/showthread.php?t=1828751&highlight=swap") from oldfred (third post down).

When I looked at my partitions (see attached) the first thing I noticed is that the swap is a sub of sda/2.  On 10.04 my swap was between my / and /home partitions.

Is this an issue?

Another issue: my / partition filled up very fast!  I'm surprised, but I have fewer downloaded applications than I did with 10.04.  As I was going through this [to-do list]("http://theindexer.wordpress.com/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/") I got a memory warning.  I deleted some, but I'm still surprised I ate up 20 GB so fast.

Thanks for your help.

---

### Post by YesWeCan on 2011-09-08
Hi. No the location of the partitions doesn't matter.

Your root partition is plenty big enough and should not be filling up. So I am concerned that your /home partition has not been mounted.

Would you please post the outputs of:
[COLOR="DarkSlateBlue"]mount
cat /etc/fstab[/COLOR]


Also, how much RAM do you have?

---

### Post by dedukes on 2011-09-08
Okay.  Here's what I got:



dare@dare-Satellite-A135:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda5 on /home type ext3 (rw,user_xattr,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dare/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dare)
dare@dare-Satellite-A135:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=96b94abc-3807-4fd4-919c-25444adfb0b5 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=0a01d6cc-f67a-455b-8a14-5d9d046c1ca8 /home           ext3    defaults,user_xattr        0       2
# swap was on /dev/sda6 during installation
UUID=862639c4-d441-4e75-ac5e-53f585a6e7f1 none            swap    sw              0       0
dare@dare-Satellite-A135:~$

---

### Post by Hakunka-Matata on 2011-09-08
> **dedukes said:**
> Hi.

I just did a fresh install to 11.04.

When creating my partitions I followed, as best I could, [this post]("http://ubuntuforums.org/showthread.php?t=1828751&highlight=swap") from oldfred (third post down).

[COLOR=Red]When I looked at my partitions (see attached) the first thing I noticed is that the swap is a sub of sda/2.  On 10.04 my swap was between my / and /home partitions.[/COLOR]

Is this an issue?

Another issue: my / partition filled up very fast!  I'm surprised, but I have fewer downloaded applications than I did with 10.04.  As I was going through this [to-do list]("http://theindexer.wordpress.com/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/") I got a memory warning.  I deleted some, but I'm still surprised I ate up 20 GB so fast.

Thanks for your help.
[COLOR=Red]No, it's not an issue, sda2 is an Extended partition (it is a primary partition):  swap and /home can live happily in Logical partitions, it's better to do it this way, you save the other two primary partitions for later use, if needed.

Inside the Extended container, you may create many Logical partitions.  Ubuntu works fine in Logical partitions, Windows needs a Primary for it's root / partition.  [/COLOR]

---

### Post by flemur13013 on 2011-09-08
> **dedukes said:**
> ...
Is this an issue?


Theoretically, swapping wil be slower if the partition is near the end of the drive.  In practice I bet there's no noticeable difference, depending on how much you swap.

You might run ```
sudo computer-janitor-gtk
``` to free up some space.
and run ```
baobab
``` to see which files are using disk space.

---

### Post by dedukes on 2011-09-08
And here's my memory profile (attached)

---

### Post by YesWeCan on 2011-09-08
You can run this to see where all the space is going in your root partition:

sudo du -sh /*

---

### Post by Hakunka-Matata on 2011-09-08
Is /home mounted?  Does not the "KEY" icon showing in the gparted graphic mean that /home - sda5 is mounted?  
Not arguing, just highlighting the meaning of the "KEY" icon showing up in GParted.
sda6 might be mounted for some other reason than getting mounted through  /etc/fstab.

---

### Post by YesWeCan on 2011-09-08
> **dedukes said:**
> Okay.  Here's what I got:
That all looks good.
I guess you just have a whole load of application stuff. Wow.
My root is about 5.5GB and I thought I had a lot of software installed.

---

### Post by YesWeCan on 2011-09-08
> **Hakunka-Matata said:**
> Is /home mounted?  Does not the "KEY" icon showing in the gparted graphic mean the /home - sda6 is mounted?  
Not arguing, just highlighting the meaning of the "KEY" icon showing up in GParted.
sda6 might be mounted for some other reason than getting mounted through  /etc/fstab.
Good question. I think the extfs superblock contains an entry for where the partition is meant to be or was last mounted or such like. So I'm not sure GParted is reporting what is actually mounted or what the recorded mount is. Eg: if one booted live CD and ran GParted I suspect the mount keys would be the same even tho none of the partitions would be mounted.

**[edit]** No, you are absolutely right! :) The mount column is for currently mounted partitions. Noted. Thanks for pointing that out.

---

### Post by dedukes on 2011-09-08
> **YesWeCan said:**
> You can run this to see where all the space is going in your root partition:

sudo du -sh /*

Here are the results:


6.8M	/bin
42M	/boot
4.0K	/cdrom
816K	/dev
15M	/etc
du: cannot access `/home/dare/.gvfs': Permission denied
20G	/home
0	/initrd.img
0	/initrd.img.old
259M	/lib
16K	/lost+found
4.0K	/media
4.0K	/mnt
98M	/opt
du: cannot access `/proc/4848/task/4848/fd/4': No such file or directory
du: cannot access `/proc/4848/task/4848/fdinfo/4': No such file or directory
du: cannot access `/proc/4848/fd/4': No such file or directory
du: cannot access `/proc/4848/fdinfo/4': No such file or directory
0	/proc
13G	/root
8.1M	/sbin
4.0K	/selinux
4.0K	/srv
4.0K	/swap
0	/sys
288K	/tmp
2.4G	/usr
313M	/var
0	/vmlinuz
0	/vmlinuz.old

---

### Post by YesWeCan on 2011-09-08
```
13G	/root
```
This is not right.
Are you somehow installing apps as the root user as opposed to installing as a non-root user using sudo?

If so, all the files that should be going in to your /home/you directory are ending up in /root.

---

### Post by dedukes on 2011-09-08
> **YesWeCan said:**
> ```
13G	/root
```
This is not right.
Are you somehow installing apps as the root user as opposed to installing as a non-root user using sudo?

If so, all the files that should be going in to your /home/you directory are ending up in /root.

As ignorant as I am, I saw that and scratched my head.  Anything is possible.  

I've been installing applications via the Software Center and terminal using sudo.  But, I guess it's possible I misinterpreted some instructions somewhere along the line.  Is there a command I can run that will list applications in / root that will show us?

---

### Post by YesWeCan on 2011-09-08
> **dedukes said:**
> As ignorant as I am, I saw that and scratched my head.  Anything is possible.  

I've been installing applications via the Software Center and terminal using sudo.  But, I guess it's possible I misinterpreted some instructions somewhere along the line.  Is there a command I can run that will list applications in / root that will show us?
[COLOR="DarkSlateBlue"]ls -alh /root[/COLOR]  (that shouldn't work unless you are root. Instead try [COLOR="DarkSlateBlue"]sudo ls -alh /root[/COLOR] )

What is the prompt you see at your terminal, is it something like
root@host:~#

---

### Post by dedukes on 2011-09-08
> **YesWeCan said:**
> [COLOR="DarkSlateBlue"]ls -alh /root[/COLOR]  (that shouldn't work unless you are root. Instead try [COLOR="DarkSlateBlue"]sudo ls -alh /root[/COLOR] )

What is the prompt you see at your terminal, is it something like
root@host:~#


My prompt is (and has always been): dare@dare-Satellite-A135:~$ 

Here's the output for the first one:
dare@dare-Satellite-A135:~$ ls -alh /root
ls: cannot open directory /root: Permission denied
dare@dare-Satellite-A135:~$ 


Here's the output for the second one:

dare@dare-Satellite-A135:~$ sudo ls -alh /root
[sudo] password for dare: 
Sorry, try again.
[sudo] password for dare: 
total 84K
drwx------ 18 root root 4.0K 2011-09-08 00:10 .
drwxr-xr-x 23 root root 4.0K 2011-09-08 10:11 ..
drwxr-xr-x  3 root root 4.0K 2011-09-08 00:09 .adobe
drwx------  3 root root 4.0K 2011-09-08 00:10 .appdata
-rw-r--r--  1 root root 3.1K 2010-10-21 08:47 .bashrc
drwx------  6 root root 4.0K 2011-09-07 23:55 .config
drwx------  3 root root 4.0K 2011-09-07 01:28 .dbus
drwxr-xr-x  4 root root 4.0K 2011-09-07 23:55 Desktop
drwx------  3 root root 4.0K 2011-09-08 01:09 .gconf
drwx------  2 root root 4.0K 2011-09-08 01:11 .gconfd
drwxr-xr-x  4 root root 4.0K 2011-09-07 23:55 .gnome2
drwxr-xr-x  2 root root 4.0K 2011-09-07 01:48 .gstreamer-0.10
drwxr-xr-x  3 root root 4.0K 2011-09-08 00:10 .local
drwxr-xr-x  3 root root 4.0K 2011-09-08 00:09 .macromedia
drwxr-xr-x  2 root root 4.0K 2011-09-07 01:28 .nautilus
-rw-r--r--  1 root root  140 2010-10-21 08:47 .profile
drwx------  2 root root 4.0K 2011-09-08 09:20 .pulse
-rw-------  1 root root  256 2011-09-07 00:48 .pulse-cookie
drwx------  3 root root 4.0K 2011-09-08 00:21 .synaptic
drwx------  4 root root 4.0K 2011-09-07 01:48 .thumbnails
drwxr-xr-x  2 root root 4.0K 2011-09-08 00:03 .xine
dare@dare-Satellite-A135:~$ 


Um, only 84k?  Isn't this supposed to add up to 13GB?

---

### Post by dedukes on 2011-09-08
Okay, I may be onto something.

I got in the habit of using Nautilus as root (not sure if this is the right description--but in the application launcher I used the command: gksudo nautilus) when I was trying to backup my /home folder after I crashed trying to upgrade from 10.04 to 10.10.

Using Nautilus I dragged a very large media file (with videos of TV shows) onto my desktop.  I know realize this is the root desktop, which is different than my home desktop.  Right?  So now i'm moving that folder onto my /home desktop.

Another question.  I also dragged another big folder of videos that i'd put on my root desktop into the trash (there was a duplicate on my home desktop).  But Nautilus won't allow me to view the contents of the trash to empty it.  Does root have it's own trash bin?  If yes, how can I empty it?

---

### Post by YesWeCan on 2011-09-08
I'm back. The root trash is possibly in /root/.local/share/Trash

To list the files sizes in /root you need to become root
sudo -i
cd /root
du -ah

See also: [http://www.codecoffee.com/tipsforlinux/articles/22.html](http://www.codecoffee.com/tipsforlinux/articles/22.html)

---

### Post by dedukes on 2011-09-08
> **YesWeCan said:**
> I'm back. The root trash is possibly in /root/.local/share/Trash

To list the files sizes in /root you need to become root
sudo -i
cd /root
du -ah

See also: [http://www.codecoffee.com/tipsforlinux/articles/22.html](http://www.codecoffee.com/tipsforlinux/articles/22.html)

Yeah, it's all in the root trash now, right?  here's the output:

4.3M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0079.JPG
3.9M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0035.JPG
3.0M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0142.JPG
322M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/Union_Pool_02-26-10--From_a_Plane.MP4
3.6M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0120.JPG
4.1M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0037.JPG
4.6M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0101.JPG
3.6M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0183.JPG
4.6M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0094.JPG
4.3M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0145.JPG
3.5M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0117.JPG
2.3M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0048.JPG
4.6M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0165.JPG
4.2M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0068.JPG
4.5M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0013.JPG
3.9M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0038.JPG
2.7M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0047.JPG
4.2M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0083.JPG
3.6M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0116.JPG
4.3M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0113.JPG
4.4M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0096.JPG
3.7M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0093.JPG
3.9M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0090.JPG
3.4M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0122.JPG
3.6M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0044.JPG
4.2M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0132.JPG
3.9M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0121.JPG
381M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/Union_Pool_02-26-10--Old_West_Broad.MP4
4.4M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/union pool 2-26-10--02.JPG
3.8M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0179.JPG
332M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/Union_Pool_02-26-10--Subway_Rider.MP4
245M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/Union_Pool_02-26-10--Jim_Eggers.MP4
4.7M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0103.JPG
3.5M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0050.JPG
4.3M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0141.JPG
2.7M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0046.JPG
4.5M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0156.JPG
3.6M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0017.JPG
3.6M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0064.JPG
3.6M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0182.JPG
3.2M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0173.JPG
4.5M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0114.JPG
4.4M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0123.JPG
4.6M	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10/DSC_0102.JPG
1.5G	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos/union pool 2-26-10
2.2G	./.local/share/Trash/files/Desktop misc/xtian photos--xtian photos
648K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2196.JPG
872K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2133.JPG
768K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2084.JPG
1.6M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMAG0152.jpg
576K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2195.JPG
816K	./.local/share/Trash/files/Desktop misc/Zimri Photos/BABY9.jpg
928K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2203.JPG
1020K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMAG0127.jpg
1.1M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2101.JPG
864K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2160.JPG
1.5M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMAG0126.jpg
368K	./.local/share/Trash/files/Desktop misc/Zimri Photos/BABY3.jpg
932K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2206.JPG
1000K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2184.JPG
1.1M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMAG0130.jpg
948K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2127.JPG
1.4M	./.local/share/Trash/files/Desktop misc/Zimri Photos/10-11-10.jpg
780K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2113.JPG
1.1M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2068.JPG
988K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2128.JPG
468K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2199.JPG
12K	./.local/share/Trash/files/Desktop misc/Zimri Photos/Picasa.ini
1.3M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMAG0133.jpg
992K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2202.JPG
1016K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2095.JPG
908K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2121.JPG
616K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2102.JPG
820K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2081.JPG
732K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2166.JPG
1004K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2064.JPG
972K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2161.JPG
820K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2082.JPG
768K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2104.JPG
1016K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2216.JPG
808K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2114.JPG
356K	./.local/share/Trash/files/Desktop misc/Zimri Photos/BABY6.jpg
940K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2075.JPG
916K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2098.JPG
492K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2066.JPG
816K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2112.JPG
888K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2092.JPG
1000K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2185.JPG
1.4M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2181.JPG
776K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2222.JPG
1.0M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2218.JPG
968K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2100.JPG
852K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2105.JPG
1.4M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2177.JPG
928K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2204.JPG
856K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2164.JPG
400K	./.local/share/Trash/files/Desktop misc/Zimri Photos/BABY15.jpg
412K	./.local/share/Trash/files/Desktop misc/Zimri Photos/BABY13.jpg
732K	./.local/share/Trash/files/Desktop misc/Zimri Photos/ZimColorCoordinated.jpg
920K	./.local/share/Trash/files/Desktop misc/Zimri Photos/BABY2.jpg
1.6M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMAG0136.jpg
840K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2123.JPG
1020K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2219.JPG
912K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2208.JPG
40K	./.local/share/Trash/files/Desktop misc/Zimri Photos/24776733727_ORIG.jpeg
392K	./.local/share/Trash/files/Desktop misc/Zimri Photos/BABY4.jpg
872K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMAG0128.jpg
908K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2109.JPG
804K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2103.JPG
872K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2090.JPG
1.6M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMAG0153.jpg
796K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2155.JPG
1004K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2125.JPG
956K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2107.JPG
728K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2158.JPG
1.3M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2063.JPG
1.3M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2170.JPG
928K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2111.JPG
864K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2143.JPG
468K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2070.JPG
1.2M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2141.JPG
968K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2162.JPG
368K	./.local/share/Trash/files/Desktop misc/Zimri Photos/BABY8.jpg
840K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2131.JPG
640K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2165.JPG
688K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2226.JPG
908K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2094.JPG
908K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2132.JPG
816K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2156.JPG
808K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2136.JPG
872K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2153.JPG
1016K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2212.JPG
648K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2071.JPG
964K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2085.JPG
384K	./.local/share/Trash/files/Desktop misc/Zimri Photos/BABY1.jpg
1.2M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2168.JPG
844K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2076.JPG
1.4M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMAG0151.jpg
872K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2144.JPG
540K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2140.JPG
936K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2205.JPG
1.1M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2213.JPG
824K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2079.JPG
852K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMAG0129.jpg
1.4M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2178.JPG
720K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2198.JPG
716K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2200.JPG
1.1M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2138.JPG
620K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2225.JPG
824K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2116.JPG
1020K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2210.JPG
1.0M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2065.JPG
924K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2108.JPG
840K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2157.JPG
888K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2091.JPG
900K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2119.JPG
940K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2201.JPG
868K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2129.JPG
408K	./.local/share/Trash/files/Desktop misc/Zimri Photos/BABY10.jpg
1.3M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2192.JPG
1.6M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2073.JPG
824K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2072.JPG
1016K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2211.JPG
968K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2142.JPG
840K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2122.JPG
856K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2145.JPG
916K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMAG0131.jpg
1020K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2221.JPG
1.1M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2220.JPG
872K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2086.JPG
396K	./.local/share/Trash/files/Desktop misc/Zimri Photos/BABY12.jpg
1016K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2169.JPG
408K	./.local/share/Trash/files/Desktop misc/Zimri Photos/BABY11.jpg
748K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2151.JPG
936K	./.local/share/Trash/files/Desktop misc/Zimri Photos/BABY14.jpg
1.1M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMAG0139.jpg
1.1M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2215.JPG
852K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2146.JPG
8.1M	./.local/share/Trash/files/Desktop misc/Zimri Photos/photos1011.zip
944K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2120.JPG
916K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMAG0132.jpg
380K	./.local/share/Trash/files/Desktop misc/Zimri Photos/BABY7.jpg
860K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2150.JPG
940K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2099.JPG
1.3M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2148.JPG
784K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2078.JPG
1.2M	./.local/share/Trash/files/Desktop misc/Zimri Photos/2010-10-12 17.50.07
736K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2152.JPG
764K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2159.JPG
564K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2139.JPG
868K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2124.JPG
892K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2193.JPG
872K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2117.JPG
1.4M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2179.JPG
616K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2194.JPG
756K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2106.JPG
912K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2209.JPG
6.8M	./.local/share/Trash/files/Desktop misc/Zimri Photos/1013photos.zip
828K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2087.JPG
1.1M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2137.JPG
912K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2134.JPG
1.1M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2214.JPG
724K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2077.JPG
1000K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2183.JPG
1004K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2182.JPG
896K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2135.JPG
856K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2088.JPG
952K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2126.JPG
1.1M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2069.JPG
924K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2130.JPG
792K	./.local/share/Trash/files/Desktop misc/Zimri Photos/BABY5.jpg
1016K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2217.JPG
1000K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2074.JPG
1.3M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2062.JPG
1.3M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMAG0135.jpg
1.6M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMAG0148.jpg
832K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2115.JPG
836K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2083.JPG
1.3M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2067.JPG
996K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2110.JPG
912K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2207.JPG
44K	./.local/share/Trash/files/Desktop misc/Zimri Photos/zim for family/IMG_2104.JPG
32K	./.local/share/Trash/files/Desktop misc/Zimri Photos/zim for family/IMG_2092.JPG
88K	./.local/share/Trash/files/Desktop misc/Zimri Photos/zim for family/IMG_2141.JPG
72K	./.local/share/Trash/files/Desktop misc/Zimri Photos/zim for family/IMG_2142.JPG
40K	./.local/share/Trash/files/Desktop misc/Zimri Photos/zim for family/IMG_2106.JPG
76K	./.local/share/Trash/files/Desktop misc/Zimri Photos/zim for family/IMAG0148.jpg
356K	./.local/share/Trash/files/Desktop misc/Zimri Photos/zim for family
1.1M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2097.JPG
896K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2089.JPG
1.8M	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMAG0138.jpg
840K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2080.JPG
920K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2093.JPG
900K	./.local/share/Trash/files/Desktop misc/Zimri Photos/IMG_2118.JPG
173M	./.local/share/Trash/files/Desktop misc/Zimri Photos
104K	./.local/share/Trash/files/Desktop misc/gCalendar Backups/dare.dukes@gmail.com.ical.zip
108K	./.local/share/Trash/files/Desktop misc/gCalendar Backups
104M	./.local/share/Trash/files/Desktop misc/gparted-live-0.9.0-6.iso
551M	./.local/share/Trash/files/Desktop misc/Game of Thrones/Game.of.Thrones.S01E01.HDTV.XviD-FEVER.avi
551M	./.local/share/Trash/files/Desktop misc/Game of Thrones/Game Of Thrones Season 1 - Complete/S01E10 - Fire and Blood.avi
551M	./.local/share/Trash/files/Desktop misc/Game of Thrones/Game Of Thrones Season 1 - Complete/S01E08 - The Pointy End.avi
880K	./.local/share/Trash/files/Desktop misc/Game of Thrones/Game Of Thrones Season 1 - Complete/Game of Thrones Title.jpg
551M	./.local/share/Trash/files/Desktop misc/Game of Thrones/Game Of Thrones Season 1 - Complete/S01E01 - Winter Is Coming.avi
551M	./.local/share/Trash/files/Desktop misc/Game of Thrones/Game Of Thrones Season 1 - Complete/S01E09 - Baelor.avi
551M	./.local/share/Trash/files/Desktop misc/Game of Thrones/Game Of Thrones Season 1 - Complete/S01E07 - You Win or You Die.avi
551M	./.local/share/Trash/files/Desktop misc/Game of Thrones/Game Of Thrones Season 1 - Complete/S01E02 - The Kingsroad.avi
551M	./.local/share/Trash/files/Desktop misc/Game of Thrones/Game Of Thrones Season 1 - Complete/S01E06 - A Golden Crown.avi
551M	./.local/share/Trash/files/Desktop misc/Game of Thrones/Game Of Thrones Season 1 - Complete/S01E05 - The Wolf and the Lion.avi
551M	./.local/share/Trash/files/Desktop misc/Game of Thrones/Game Of Thrones Season 1 - Complete/S01E04 - Cripples, Bastards and Broken Things.avi
551M	./.local/share/Trash/files/Desktop misc/Game of Thrones/Game Of Thrones Season 1 - Complete/S01E03 - Lord Snow.avi
5.4G	./.local/share/Trash/files/Desktop misc/Game of Thrones/Game Of Thrones Season 1 - Complete
6.0G	./.local/share/Trash/files/Desktop misc/Game of Thrones
44K	./.local/share/Trash/files/Desktop misc/house party photos/unionpool.jpg
60K	./.local/share/Trash/files/Desktop misc/house party photos/houseparty2.jpg
76K	./.local/share/Trash/files/Desktop misc/house party photos/houseparty1.jpg
108K	./.local/share/Trash/files/Desktop misc/house party photos/sentientbean1.jpg
64K	./.local/share/Trash/files/Desktop misc/house party photos/livingroom2.jpg
40K	./.local/share/Trash/files/Desktop misc/house party photos/livingroom1.jpg
396K	./.local/share/Trash/files/Desktop misc/house party photos
1.9M	./.local/share/Trash/files/Desktop misc/random photos/IMAG0036.jpg
4.0K	./.local/share/Trash/files/Desktop misc/random photos/Picasa.ini
1.4M	./.local/share/Trash/files/Desktop misc/random photos/IMAG0123.jpg
1.6M	./.local/share/Trash/files/Desktop misc/random photos/IMAG0121.jpg
12K	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/MVI_3342.THM
8.7M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/MVI_3344.MOV
30M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/MVI_3341.MOV
12K	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/MVI_3345.THM
4.0K	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/Picasa.ini
12K	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/MVI_3341.THM
164K	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/photo.jpg
28M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/MVI_3342.MOV
12M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/MVI_3322.MOV
12K	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/MVI_3343.THM
76K	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/starbar--08-7-09/starbar--8-7-09--01.jpg
64K	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/starbar--08-7-09/starbar--8-7-09--02.jpg
4.0K	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/starbar--08-7-09/Picasa.ini
148K	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/starbar--08-7-09
30M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/MVI_3343.mov
5.8M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/DareDukes/Sef_3-12-11_DareDukes-4.jpg
6.4M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/DareDukes/Sef_3-12-11_DareDukes-9.jpg
6.1M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/DareDukes/Sef_3-12-11_DareDukes-3.jpg
6.3M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/DareDukes/Sef_3-12-11_DareDukes-13.jpg
6.2M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/DareDukes/Sef_3-12-11_DareDukes-22.jpg
6.1M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/DareDukes/Sef_3-12-11_DareDukes-21.jpg
6.4M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/DareDukes/Sef_3-12-11_DareDukes-8.jpg
5.9M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/DareDukes/Sef_3-12-11_DareDukes-16.jpg
6.8M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/DareDukes/Sef_3-12-11_DareDukes-2.jpg
5.9M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/DareDukes/Sef_3-12-11_DareDukes-11.jpg
6.4M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/DareDukes/Sef_3-12-11_DareDukes-15.jpg
6.4M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/DareDukes/Sef_3-12-11_DareDukes-10.jpg
6.2M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/DareDukes/Sef_3-12-11_DareDukes-7.jpg
6.9M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/DareDukes/Sef_3-12-11_DareDukes-1.jpg
6.3M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/DareDukes/Sef_3-12-11_DareDukes-12.jpg
6.4M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/DareDukes/Sef_3-12-11_DareDukes-17.jpg
5.9M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/DareDukes/Sef_3-12-11_DareDukes-6.jpg
5.1M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/DareDukes/Sef_3-12-11_DareDukes-19.jpg
5.8M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/DareDukes/Sef_3-12-11_DareDukes-5.jpg
6.5M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/DareDukes/Sef_3-12-11_DareDukes-18.jpg
6.0M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/DareDukes/Sef_3-12-11_DareDukes-20.jpg
5.3M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/DareDukes/Sef_3-12-11_DareDukes-14.jpg
134M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/DareDukes
29M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/MVI_3346.MOV
30M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/MVI_3345.MOV
12K	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/MVI_3344.THM
12K	./.local/share/Trash/files/Desktop misc/random photos/Photos--random/MVI_3321.THM
300M	./.local/share/Trash/files/Desktop misc/random photos/Photos--random
1.8M	./.local/share/Trash/files/Desktop misc/random photos/IMAG0124.jpg
1.4M	./.local/share/Trash/files/Desktop misc/random photos/IMAG0110.jpg
1.4M	./.local/share/Trash/files/Desktop misc/random photos/IMAG0125.jpg
1.2M	./.local/share/Trash/files/Desktop misc/random photos/IMAG0122.jpg
310M	./.local/share/Trash/files/Desktop misc/random photos
100K	./.local/share/Trash/files/Desktop misc/jen photos/DARE/IMG_4044.jpg
340K	./.local/share/Trash/files/Desktop misc/jen photos/DARE/johnny with camera.JPG
2.0M	./.local/share/Trash/files/Desktop misc/jen photos/DARE/IMG_0103.JPG
148K	./.local/share/Trash/files/Desktop misc/jen photos/DARE/irmp 6.jpeg
516K	./.local/share/Trash/files/Desktop misc/jen photos/DARE/IMG_2145.jpg
8.0K	./.local/share/Trash/files/Desktop misc/jen photos/DARE/.DS_Store
88K	./.local/share/Trash/files/Desktop misc/jen photos/DARE/2011gang.jpg
340K	./.local/share/Trash/files/Desktop misc/jen photos/DARE/YBB shooting No Safe Place.JPG
308K	./.local/share/Trash/files/Desktop misc/jen photos/DARE/jean shooting queer in the city.JPG
124K	./.local/share/Trash/files/Desktop misc/jen photos/DARE/39979_418765783926_92115098926_4880060_3692117_n.jpg
168K	./.local/share/Trash/files/Desktop misc/jen photos/DARE/Supafriends.JPG
220K	./.local/share/Trash/files/Desktop misc/jen photos/DARE/04grouppark.jpeg
1.8M	./.local/share/Trash/files/Desktop misc/jen photos/DARE/DSC09448.JPG
6.0M	./.local/share/Trash/files/Desktop misc/jen photos/DARE
5.9M	./.local/share/Trash/files/Desktop misc/jen photos/DARE.zip
4.0K	./.local/share/Trash/files/Desktop misc/jen photos/__MACOSX/DARE/._Supafriends.JPG
4.0K	./.local/share/Trash/files/Desktop misc/jen photos/__MACOSX/DARE/._04grouppark.jpeg
4.0K	./.local/share/Trash/files/Desktop misc/jen photos/__MACOSX/DARE/._IMG_4044.jpg
4.0K	./.local/share/Trash/files/Desktop misc/jen photos/__MACOSX/DARE/._irmp 6.jpeg
4.0K	./.local/share/Trash/files/Desktop misc/jen photos/__MACOSX/DARE/._2011gang.jpg
24K	./.local/share/Trash/files/Desktop misc/jen photos/__MACOSX/DARE
28K	./.local/share/Trash/files/Desktop misc/jen photos/__MACOSX
220K	./.local/share/Trash/files/Desktop misc/jen photos/04grouppark.jpeg
13M	./.local/share/Trash/files/Desktop misc/jen photos
1.8M	./.local/share/Trash/files/Desktop misc/Athens Americana Photos/AthensAmericana2011-02.jpg
1.8M	./.local/share/Trash/files/Desktop misc/Athens Americana Photos/AthensAmericana2011-01.jpg
1.8M	./.local/share/Trash/files/Desktop misc/Athens Americana Photos/AthensAmericana2011-04.jpg
1.8M	./.local/share/Trash/files/Desktop misc/Athens Americana Photos/AthensAmericana2011-03.jpg
7.1M	./.local/share/Trash/files/Desktop misc/Athens Americana Photos
20K	./.local/share/Trash/files/Desktop misc/dave dondero.odt
180K	./.local/share/Trash/files/Desktop misc/hearing.jpg
686M	./.local/share/Trash/files/Desktop misc/ubuntu-11.04-desktop-i386.iso
689M	./.local/share/Trash/files/Desktop misc/ubuntu-10.04.3-desktop-i386.iso
11G	./.local/share/Trash/files/Desktop misc
351M	./.local/share/Trash/files/breaking bad/season 4/Breaking.Bad.S04E02.HDTV.XviD-ASAP.avi
351M	./.local/share/Trash/files/breaking bad/season 4/Breaking.Bad.S04E03.Open.House.HDTV.XviD-FQM.avi
351M	./.local/share/Trash/files/breaking bad/season 4/Breaking.Bad.S04E04.Bullet.Points.HDTV.XviD-FQM.avi
351M	./.local/share/Trash/files/breaking bad/season 4/Breaking.Bad.S04E06.HDTV.XviD-ASAP.avi
351M	./.local/share/Trash/files/breaking bad/season 4/Breaking.Bad.S04E07.Problem.Dog.HDTV.XviD-FQM.avi
351M	./.local/share/Trash/files/breaking bad/season 4/Breaking.Bad.S04E05.Shotgun.HDTV.XviD-FQM.avi
351M	./.local/share/Trash/files/breaking bad/season 4/(download at superseeds.org) breaking.bad.s04e01.hdtv.xvid-fqm.avi
2.4G	./.local/share/Trash/files/breaking bad/season 4
2.4G	./.local/share/Trash/files/breaking bad
4.0K	./.local/share/Trash/files/sources.list
13G	./.local/share/Trash/files
4.0K	./.local/share/Trash/info/sources.list.trashinfo
4.0K	./.local/share/Trash/info/Desktop misc.trashinfo
4.0K	./.local/share/Trash/info/breaking bad.trashinfo
16K	./.local/share/Trash/info
13G	./.local/share/Trash
0	./.local/share/.converted-launchers
4.0K	./.local/share/applications/mimeapps.list
8.0K	./.local/share/applications
13G	./.local/share
13G	./.local
24K	./.xine/catalog.cache
28K	./.xine
4.0K	./.adobe/Flash_Player/AssetCache/87CVDZA7
8.0K	./.adobe/Flash_Player/AssetCache
12K	./.adobe/Flash_Player
16K	./.adobe
0	./.pulse/efc8f3d9fb4042b33f23dec40000000c-runtime
0	./.pulse/ubuntu-runtime
4.0K	./.pulse
4.0K	./.bash_history
13G	.
root@dare-Satellite-A135:~#

---

### Post by YesWeCan on 2011-09-08
Thanks for sharing your trash :P

How much RAM has your system got? Just thinking about your swap size.

---

### Post by dedukes on 2011-09-08
> **YesWeCan said:**
> Thanks for sharing your trash :P

How much RAM has your system got? Just thinking about your swap size.

You're welcome.;)

How do I empty it?

the "top" command says this is my total memory:

Mem:   2050840k total

My swap is too small?

---

### Post by YesWeCan on 2011-09-08
As root:
```
rm -r /root/.local/share/Trash/*
```

[COLOR="Red"]warning:[/COLOR] don't mistype this.


There is no right amount of swap...depends on your applications. But I like to see RAM+swap 4GB+ for typical usage. So you're fine.

---

### Post by dedukes on 2011-09-08
> **YesWeCan said:**
> As root:
```
rm -r /root/.local/share/Trash/*
```

[COLOR="Red"]warning:[/COLOR] don't mistype this.



This is what happened:

dare@dare-Satellite-A135:~$ rm -r /root/.local/share/Trash/*
rm: cannot remove `/root/.local/share/Trash/*': Permission denied
dare@dare-Satellite-A135:~$ sudo rm -r /root/.local/share/Trash/*
[sudo] password for dare: 
rm: cannot remove `/root/.local/share/Trash/*': No such file or directory
dare@dare-Satellite-A135:~$

---

### Post by YesWeCan on 2011-09-08
[COLOR="DarkSlateBlue"]sudo -i[/COLOR] first and [COLOR="DarkSlateBlue"]exit[/COLOR] afterwards. Never linger as root user.

---

### Post by dedukes on 2011-09-08
> **YesWeCan said:**
> [COLOR="DarkSlateBlue"]sudo -i[/COLOR] first and [COLOR="DarkSlateBlue"]exit[/COLOR] afterwards. Never linger as root user.

The trash is empty!  See attached.

Thanks for all your help.  I appreciate it.)

:P

---

### Post by YesWeCan on 2011-09-08
Pleasure. 3.6GB root looks much better to me. Mine is 6GB so now I don't feel so inadequate. ;)

---

