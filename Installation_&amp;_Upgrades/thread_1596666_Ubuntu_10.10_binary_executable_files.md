---
title: "Ubuntu 10.10 binary executable files"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by newbie2010 on 2010-10-11
Hi

Yesterday I upgraded from ubuntu 10.04 to 10.10. When I try to run a simple c program by typing ./a.out in the terminal, I get an error

bash: Permission denied!!!

I tried to change permissions of bit file and still it doesn't run. I tried . ./a.out, still it doesn't run. The program runs perfectly in my older version of 10.04. Please help!!

---

### Post by COmetLord on 2010-10-14
i encounter the same problem in maverick. i did a network update instead of a fresh install(as i usually did), and now i cant open any executable compiled by gcc, it would just show "bash: ****: Permission denied". this never happened b4 on other versions

---

### Post by newbie2010 on 2010-10-14
Could anyone please help me with this?

---

### Post by newbie2010 on 2010-10-14
HI,

I recently upgraded from Ubuntu 10.04 to 10.10. However I am facing problems, relating to executing files (say binary files like ./a.out which you get after compiling a "C program") which are present in mounted partitions. I tried to change permissions of the files, directories etc but all in vain! I also tried to (partition directory > right click > permissions > check out box execute :Allow executing files as a program) but the status again reverts back, and I am not able to execute the files at all!!!! All i get is

bash: ./a.out: Permission denied

PS: The files run perfectly in Ubuntu 10.04.

Please help,Thanks in advance.

---

### Post by sikander3786 on 2010-10-14
You mentioned that you upgraded, still at first I would like to know about your install's architecture.

You are using 32-bit or 64-bit Ubuntu? Are you sure the architecture of Ubuntu and those downloaded files is the same? Might be they were intended for 32-bit and you are now using 64-bit or vice versa.

---

### Post by newbie2010 on 2010-10-14
I am using a 32 bit machine. I just upgraded,from Ubuntu 10.04, directly from the network! Can you please tell me how can I check or know what version of Ubuntu 10.10 is installed in my system now?

---

### Post by sikander3786 on 2010-10-14
Are the files stored on another partition? If so, what File System on that partition? Are you sure it is mounted without the "noexec" flags? You can check in /etc/fstab.

You can easily check if it is a mount issue by moving the files to your /home directory and executing from there. If successful, then we can work on fstab.

---

### Post by newbie2010 on 2010-10-14
This is what i get when i type uname -a

"Linux username-laptop 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:24:00 UTC 2010 i686 GNU/Linux"

---

### Post by cyberkilla on 2010-10-14
Does the file have the executable flag set?

```
chmod +x a.out
```

That's what I do anyway.

---

### Post by newbie2010 on 2010-10-14
Yes I am able to execute the files from home directory, but not from the mount partition!

---

### Post by newbie2010 on 2010-10-14
Yes, i tried that too! Still i get permission denied!!! :(((

Please help. Thanks.

---

### Post by sikander3786 on 2010-10-14
Backup the fstab so you can revert to the original one if needed.

```
sudo cp /etc/fstab /etc/fstab.old
```

Edit fstab,

```
sudo gedit /etc/fstab
```

Look for the intended partition, it would look something like,

```
UUID=3f8c5321-7181-40b3-a867-9c04a6cd5f2f  /media/data  ext3  noexec  0  2
```

Your UUID, mount point and FS will not be the same.

Just delete "noexec", save and close and reboot.

Be cautious, don't touch anything other than "noexec" or you might be in trouble.

---

### Post by cyberkilla on 2010-10-14
> **newbie2010 said:**
> Yes, i tried that too! Still i get permission denied!!! :(((

Please help. Thanks.

Perhaps you are no longer the owner of the files? Sorry, I can't really think of anything else.

---

### Post by Vaphell on 2010-10-14
```
ls -l
``` to see permissions/ownership

do you have build-essential package installed?

---

### Post by ean5533 on 2010-10-14
Assuming that a.out really is a compiled executable program, it shouldn't matter at that point if (s)he has build-essential installed or not.

What does the program do? Is it safe to run it as root? Can you try that and see what happens?

---

### Post by newbie2010 on 2010-10-14
No still it doesn't work!!! I have pasted my old and new files of fstab here. Please have a look. The windows partition is mounted in "/media" location as in "/media/BECAD930CAD8E5A5" but /media is no where visible in fstab file!!!  Does this got to do something with my problem?


********************new file***************************** (after removing nonexec from line 8 of old file)

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=16a19e73-c25d-4d8a-bc68-572c69263b54 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=cbc3249c-341a-49a3-b499-0ce4eb1fc930 none            swap    sw              0       0

***************old file*******************

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=16a19e73-c25d-4d8a-bc68-572c69263b54 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=cbc3249c-341a-49a3-b499-0ce4eb1fc930 none            swap    sw              0       0

---

### Post by newbie2010 on 2010-10-14
No i do not have build essential package installed!

ls -l gives

-rw------- 1 'username' 'username' 7155 2010-10-14 20:04 ./a.out

bash: ./a.out: permission denied! That is what i get when i run as root!

---

### Post by The Cog on 2010-10-14
> **newbie2010 said:**
> 
ls -l gives

-rw------- 1 'username' 'username' 7155 2010-10-14 20:04 ./a.out

bash: ./a.out: permission denied! That is what i get when i run as root!

You need to mark it executable. Even root cannot execute files that are not executable. Use this command:
**chmod +x a.out**
and try again.

---

### Post by newbie2010 on 2010-10-14
No, that doesn't work!!! I tried chmod +x a.out. Still i get the same permission denied. I tried to change permissions of the files, directories etc but all in vain! I also tried to (partition directory > right click > permissions > check out box execute :Allow executing files as a program) but the status again reverts back, and I am not able to execute the files at all!!!! All i get is

bash: ./a.out: Permission denied

PS: The files run perfectly in Ubuntu 10.04.

---

### Post by ean5533 on 2010-10-14
Something doesn't add up. Please run this command and post all of the output.

> chmod +x a.out && ls -l

---

### Post by newbie2010 on 2010-10-14
No, I get the same thing.

Please see the screenshot!

---

### Post by CharlesA on 2010-10-14
Threads merged. Please don't crosspost, as it makes more work for those trying to help you.

---

### Post by ean5533 on 2010-10-14
Ah ha, so the file is on another partition. I'm betting that partition has been mounted as readonly, which prevents you from changing the file's permissions. The solution is to make sure it's being mounted correctly. 

How are you mounting the partition? Are you doing it through a line in /etc/fstab? If so, post the contents of your fstab file.

---

### Post by The Cog on 2010-10-14
> **newbie2010 said:**
> No, I get the same thing.

Please see the screenshot!

FAT and NTFS filesystems aren't able to store unix filesystem permissions and properties. The properties of all files in such removable media are set as a mount option when the media is mounted. Copy the file to a proper unix filesystem such as you would find in your home directory, and then mark it executable and run it.

P.S.
@ean5533: It's not a read-only problem, it's deeper than that. The executable bit cannot be set because the filesystem cannot store it. If the mount options were changed, then all files on the stick would be executable and you equally wouldn't be able to change them to not being executable. I think emulating the properties as not-executable is the right thing to do, for general security reasons.

---

### Post by newbie2010 on 2010-10-14
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=16a19e73-c25d-4d8a-bc68-572c69263b54 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=cbc3249c-341a-49a3-b499-0ce4eb1fc930 none            swap    sw              0       0

---

### Post by newbie2010 on 2010-10-14
> **CharlesA said:**
> Threads merged. Please don't crosspost, as it makes more work for those trying to help you.

Sorry! Will not repeat!

---

### Post by bolhach on 2010-10-16
I have the same problem, but I can run programs just in the User folder '~ /'
In units out of the same problem

---

### Post by COmetLord on 2010-10-16
> **bolhach said:**
> I have the same problem, but I can run programs just in the User folder '~ /'
In units out of the same problem

same problem here, i bet that its a problem associated with ubuntu 10.10

---

### Post by COmetLord on 2010-10-16
> **The Cog said:**
> FAT and NTFS filesystems aren't able to store unix filesystem permissions and properties. The properties of all files in such removable media are set as a mount option when the media is mounted. Copy the file to a proper unix filesystem such as you would find in your home directory, and then mark it executable and run it.

P.S.
@ean5533: It's not a read-only problem, it's deeper than that. The executable bit cannot be set because the filesystem cannot store it. If the mount options were changed, then all files on the stick would be executable and you equally wouldn't be able to change them to not being executable. I think emulating the properties as not-executable is the right thing to do, for general security reasons.

thanks for your help, but it seems like you dont understand our problem here. 

the exact same file works perfectly in previous ubuntu version. and we would very much wish to be able to continue our works at the same location and not wanting to shift the files anywhere else(hopefully)

---

### Post by COmetLord on 2010-10-16
> **ean5533 said:**
> Ah ha, so the file is on another partition. I'm betting that partition has been mounted as readonly, which prevents you from changing the file's permissions. The solution is to make sure it's being mounted correctly. 

How are you mounting the partition? Are you doing it through a line in /etc/fstab? If so, post the contents of your fstab file.

i have the exact same problem as newbie2010, i mount the partition by clicking the partition icon under "places". in other words, the system do the mounting in the default way(the same problem did not occur in lucid lynx when i mounted the partition using the same method). and im sure the partition is not read-only since i can create or paste any files into anywhere in the partition

---

### Post by Olmuz on 2010-10-18
I have exactly the same problem. I am sure is related with the 10.10 upgrade and with the mounting of my external drive. I can create and delete files in my hd but I can't change the permission of file to execute (not even with sudo). If I copy the files to any place inside my pc then I can change the permissions and run the file without a problem. 

Please someone.

---

### Post by krasny on 2010-10-19
Same problem here, i can't set executable bit on a ntfs filesystem :( I'm using ubuntu 10.10, and under ubuntu 10.04 it was working

---

### Post by Olmuz on 2010-10-21
Can't figure it out. Tried different options to mount my HD but nothing. The HD is in NTFS and it was working great before the 10.10 upgrade. Any idea about what change could make this to happen?

---

### Post by Olmuz on 2010-10-21
Finally, not the best solution but is working for me:
sudo mount -o remount,exec /media/Data
Just change your mounted folder

---

### Post by marianusc on 2010-10-26
Hi everyone

I have exactly the same problem: 
upgraded to 10.10 from 10.04, cant run C/C++ complied files on FAT32 partition with permission denied error, cant use chmod +x to make these files executable. 

Maybe It's even worse...


> **Olmuz said:**
> Finally, not the best solution but is working for me:
sudo mount -o remount,exec /media/Data
Just change your mounted folder

...because this procedure does not work for me...

I need really help

---

### Post by Stratok on 2010-10-26
Found a way to execute files.

They will run if you execute them through Playonlinux, So, I was thinking that maybe we could use some nautilus script to make it work or write a script ourselves using one of an already installed aplications. im not expert, but something like this may work:

1.-
make a new prefix in playonlinux using system or whatever wine version in you want.

2.-
Create a new nautilus script using this code:

#!/bin/bash
PATH="/home/REPLACEWITHUSER/.PlayOnLinux/WineVersions//usr/bin/:$PATH"
export WINEPREFIX="/home/REPLACEWITHUSER/.PlayOnLinux/wineprefix/REPLACEWITHPREFIXNAME"
export WINEDEBUG="-all"
cd $NAUTILUS_SCRIPT_CURRENT_URI
wine $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS


3.-
put on /home/REPLACEWITHUSER/.gnome2/nautilus-scripts



4.- run files using right click nautilus scripts...


script can be modified replacing $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
with "file path", "" included and $NAUTILUS_SCRIPT_CURRENT_URI with actual url, again includde ""...

---

### Post by Olmuz on 2010-10-26
My problem was that since ubuntu 10.10 I wasn't able to run C/C++ compiled files from my external hd (I got permission denied) and I wasn't able to change the permissions of the files either (even with sudo). I solved my problem by remounting my hd with execution permissions. So, if this is your problem you can temporary fixed by:
1.- Find where your HD is mounted. If it is done automatically, it should be inside /media/
2.- Remount your HD with execution permission using:

sudo mount -o remount, exec /media/your_old_mounted_folder

I hope this works for someone.


> **marianusc said:**
> Hi everyone

I have exactly the same problem: 
upgraded to 10.10 from 10.04, cant run C/C++ complied files on FAT32 partition with permission denied error, cant use chmod +x to make these files executable. 

Maybe It's even worse...




...because this procedure does not work for me...

I need really help

---

### Post by marianusc on 2010-10-27
Sorry Olmuz but simply typing that command ( sudo mount -o remount, exec /media/your_old_mounted_folder, with obviously my old mounted folder name instead of your_old_mounted_folder)
it does not work.
Nothing happens, nothing changes, neither errors!
As you say I mount automatically and the partition is in media folder (/media/STORAGE)


@Stratok

Thanks indeed but your procedure seems to be too complex and I will continue to use ubuntu if it simplifies my work

---

### Post by ydobon on 2010-10-30
For me worked, that I just mounted the device in another Folder.
```

umount /media/old_folder/
mount /dev/sda1 /media/new_folder/ -o ntfs
```yours mk



EDIT:
If you need more rights it gets more complicated:

Insert something like the folling line in your /etc/fstab (change your device names and the number after uid to your userId)
```

/dev/sda1       /media/win      ntfs    defaults,nls=utf8,umask=000,uid=1000    0       0
```
Then do the following
```
sudo mount /dev/sda1
```

---

### Post by jdforsythe on 2010-11-04
I had this issue..

I moved my home folder to a new partition, which had the noexec option set, although it wasn't explicitly set in /etc/fstab. The way I found this was by opening a terminal and:

mount

which displays a list of your mounted devices. It will look something like this:
/dev/sda7 on /home type ext4 (rw,noexec,nosuid,nodev,commit=0)

the /home is the path (so for some of you, this will be /media/drivename) and the /dev/sda7 is the device.

Then execute:
sudo mount DEVICE -o remount,exec

in my case:
sudo mount /dev/sda7 -o remount,exec

If your program now executes, just edit your /etc/fstab:
sudo cp /etc/fstab /etc/fstab.backup
sudo nano /etc/fstab

and find the device again, and add ",exec" to the end of the options. This will change that option automatically in the future.

---

### Post by nagra on 2010-11-15
hi, 
i am getting the same problem ,i want execute a shell file from the directory OS_
it is giving the error. 
here the thing which it displays after executing mount
/dev/sda7 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nagraj/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nagraj)
/dev/sda3 on /media/OS_ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

---

### Post by Kainous on 2010-12-03
Same problem as well. Can't open EXEs (or allow them to be opened) on my NTFS partition.

---

### Post by kageki on 2011-01-25
It`s already the end of January 2011 and there does not seem to be a solutions for this around. I am encountering this problem too. So what`s the progress?

---

### Post by hugomvera on 2011-02-18
I had the same problem.  My c programs were in a usb with a fat partition.
easy solution
*****************************
*************************


reformat the usb to ext2

hope this helps!

---

### Post by gepolv on 2011-04-08
Any progress? I am having the same problem and googled it for a while.
I hate Ubuntu 10.10!!!

---

### Post by garuhhh on 2011-04-08
i solved my problem by declaring my drives in fstab, and allowed them to be mounted during boot time.

---

### Post by gepolv on 2011-04-08
> **garuhhh said:**
> i solved my problem by declaring my drives in fstab, and allowed them to be mounted during boot time.


Would you like post your fstab here?
Thanks a lot
Deryk.

---

### Post by garuhhh on 2011-04-09
here is my fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=99dbc61b-4610-4304-a88e-fdb093a23d10       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
# Commented out by Dropbox
# UUID=a7809c5a-6623-4df1-ad19-d188614285d8 /home           ext3    defaults        0       2
UUID=23e50aa8-a041-476a-964b-ce06d41f1315       none            swap    sw              0       0

# ntfs partitions by garu
LABEL=disk1	/mnt/disk1	ntfs-3g	defaults,user,suid,dev,umask=000,locale=en_US.utf8,uid=1000,exec	0	0
LABEL=disk2	/mnt/disk2	ntfs-3g	defaults,user,suid,dev,umask=000,locale=en_US.utf8,uid=1000,exec	0	0
UUID=a7809c5a-6623-4df1-ad19-d188614285d8 /home ext3 defaults,user_xattr 0 2
```

---

