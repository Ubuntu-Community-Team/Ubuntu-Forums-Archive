---
title: "Replace disk with home dir on it"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by gmalac on 2007-03-10
Hello,
My Ubuntu 6.10 box has 2 hard disks, with the 2d, hdb, for the /home directory.
This disk is old and nearly full (80GB out of 100GB) and I bought a new hd to replace it.
How should I proceed? Is there an "easy" way to sort of keep the data on /home and then install the new drive and then get the data back?
I don't have enough space on the hda drive (30GB) but thru samba I can access an XP PC.
Thanks for any help!
Guy

---

### Post by colo on 2007-03-10
You should be able to temporarily attach the new harddisk alongside your current ones. Let's assume the device node assigned to it is "/dev/yourdisk" (of course, this will not be the case, as the Linux kernel names harddisks like "sda" or "hda" and so on, so you've got to determine the real name before actually proceding).

Once your box is booted up, DON'T log in graphically - switch to a VT (Ctrl+Alt+F1), log in, become root (`sudo su -`), create one partition on the drive (`cfdisk /dev/yourdisk`, the interface is self-explanatory. I'll assume that the partition you just created will be called "/dev/yourpart" from now on - whenever you shall replace it by the actual name, I've used a **bold**font) and fire off the following commands:
```

mkfs.ext3 -Tlargefile -Odir_index -m0 -LNEWHOME **/dev/yourpart**
mkdir /mnt/newhome
mount -t ext3 -o noatime **/dev/yourpart** /mnt/newhome
cd /home/ && tar -cp * | tar -xpf- -C /mnt/newhome
cd /
umount /mnt/newhome
cp /etc/fstab /root/fstab~
sed -i -r "s@^UUID=[^[:blank:]]+([[:blank:]]+.*/home)@LABEL=NEWHOME \1@" /etc/fstab
reboot

```

(Please note that as I did not test the above script I cannot take any responsibility if it hoses your system. If it does, reboot in single user "rescue" mode, log in, become root, issue `cp /root/fstab.bak /etc/fstab`, reboot, and everything _should_ be back to normal again. You can remove your smaller drive after once successfull login-attempt and power-cycle if everything else seems fine. Be sure to keep it for backup purposes, if possible.)

Hth.

---

### Post by geirha on 2007-03-10
In case you are unable to have three harddrives in your computer at the same time, then I would do the following to backup your homedirs to samba-share:

assuming your windows xp share is mounted in /mnt/samba:

```

cd /home
sudo tar jcvf /mnt/samba/homedir-backup.tar.bz2 .

```
the command will probably take alot of time, and result in a huge file, depending on how well bzip2 manages to compress. 

the v in jcvf is optional, it stands for verbose, and will print the file it's currently processing... this will give alot of output, so you might consider not using it. i.e. tar jcf /mnt/samba/homedi.....

Now, switch harddrives, but don't boot, use the Ubuntu CD to boot. When the CD is booted, go to system -> administration -> gnome partitioning (something) and create a partition with ext3fs (default).

mount your new partition, and the samba-share, and copy back the data:
```

sudo mkdir /mnt/home
sudo mkdir /mnt/samba
sudo mount -text3 /dev/hdb1 /mnt/home
sudo mount -tsmbfs //windows/share /mnt/samba
cd /mnt/home
sudo tar jxvf /mnt/samba/homedir-backup.tar.bz2

```
have som coffee, and reboot when it's done...

---

### Post by gmalac on 2007-03-13
Thanks for that!

As I can't attach a 3d drive, I went with geirha suggestion although I used part of the knowledge included in colo post.

I had problems, still have them actually, mainly with the mounting of the samba share. 

Finally I went around it using RescueCD and got back the data to a point where there is an error message related "fatal, unexpected end of file reached" or the like.

Also, the tar file is only 2GB in size while it should be some 80GB. I realize I forgot to mention that I had created a symlink to put on my hdb1 /home drive the content of my backuppc backups (version 2.12 store them in /var/lib/backuppc thus the symlink).

Also when restarting with the new drive, Linux complains and fsck fail on hdb1...

Any idea?

---

### Post by Jonne on 2007-03-13
Your Windows disk doesn't happen to be formatted FAT32, right? FAT32 has a filesize limit of 2GB. 

If you're running win9x-ME, you definately have FAT32. XP can be both FAT and NTFS, so you'll have to check in your drive properties to find out.

If you run XP, you can convert from FAT32 to NTFS from within the OS without any data loss.

There's probably an easy way to split the file bz2 file up in chunks of 2GB too, but I don't know by heart what it should be. Try looking up in google, or wait for somebody else to tell you what to use ;).

---

### Post by geirha on 2007-03-13
1. What problems are you having with mounting samba shares? do you get any meaningful errors?

2. How old is the rescueCD? the 2GB limit is an old problem that I thought was sortof extinct by now... I think it's the version of tar you've used that is too old, but I'm not sure. Anyway... you could of course just copy the files via either samba or ssh, but then you'll lose the ownership and permissions of the files :/

3. as for the symlink, I'm guessing /var isn't on hdb, so you don't really need to copy that one... or?

4. Have you partitioned and formatted the drive? how does **fdisk -l /dev/hdb** look like?

The best option I can think of however, is to put the new harddrive into the windows-box (possibly replacing the windows-harddrive), boot with the ubuntu CD, and copy the files with ssh, directly to your new harddrive:
```

mount /dev/hdb1 /mnt
cd /mnt
ssh username@ubuntubox.ip tar jc /home | tar jx 
```
you would need to install an ssh-server on your ubuntubox first of course.
```
sudo aptitude install openssh-server
```
**EDIT:** on second thought, you'll probably need root privileges to access all the files in the other users homes, so for this to work you'll need to log in as root. That means you hafto give your root user a password (sudo passwd). And you'll also need root privileges on the windows box, so:
```
ssh root@ubuntubox tar jc | sudo tar jx
```

---

### Post by gmalac on 2007-03-15
Thanks for there input and here some answers:
- The WinXP PC has NTFS on it
- Samba error was related to the version? (wrong version?)

Actually the problem comes right from step one, I guess, because no matter what (I deleted some files in the meantime for example) the file I create with the instruction:
sudo tar jcvf /mnt/samba/homedir-backup.tar.bz2 .
is 2GB on size! 
The data on hdb1 is some 80GB, big chunk of it already compressed (backup data from Backuppc).

So when I try do proceed anyway (switch to new disk) and copy back the tar file I have the error "unexpected eof reached".

Could it be that tar files are limited to 2GB?

If yes, any other idea to solve the problem?

Thanks!

---

### Post by geirha on 2007-03-15
Older versions of tar did have a limit of 2GB, but the version installed in ubuntu does not have this limit (I believe it's about 4TB now). You can easily test this if you like, find some dir that uses more than 2GB of space and make a tar, see if it gets more than 2GB. **du -s * | sort -g** gives you a good idea of how much space each directory uses, and just run **tar cf ~/temp-tar-file.tar some-dir/** and see how big the tar-file gets. (I checked on my ubuntu box, just to be sure)

So, the limitation seems to be in smb, so I would go for transfering them via ssh instead.
1. From the windows box, you can download the files from the ubuntubox. This requires that you - install openssh-server on the ubuntu-box, and give root a passwd.
- install and ssh-client on the windows-box. Either using [putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/"), or [cygwin]("http://cygwin.com/") are the easiest choices I know of.
The command would be something like ```
ssh root@ubuntu.box tar jc /home >backup-home.tar.bz2
```
Edit: in the case of putty, the ssh-client is called plink instead of ssh
2. From the ubuntu box, you can Upload the files to the windows box.
Basicly by installing some ssh-server on the windows-box. cygwin would be the easy choice for this.
Then the command would be something like ```
tar jc /home | ssh user@windows.box "cat >backup-home.tar.bz2"
```

---

### Post by gmalac on 2007-03-19
I have been trying every other way but I am afraid I don't really understand the steps geirha you mentioned. I have putty installed on the WinXP box but it can't find "plink".
So I will install cygwin. For your first instructions, do I need to mount the samba share?
Because it is mounted on start with smbfs, so???
Sorry I am very confused

---

### Post by Jonne on 2007-03-19
Maybe an easy solution could be the following:
remove the HD containing ubuntu (the 'OS'), and replace it with your new HD. Then boot the liveCD, mount both disks (if they aren't mounted automatically), and just copy everything over. When you're done, remove your old HD, put the new one where your old one was, and put the disk containing ubuntu where it was originally.

---

### Post by geirha on 2007-03-19
Jonne's solution sounds like the easiest, with the least fuzz. 

As for putty, I think you get plink if you use the putty-installer, but if you don't have it, you can just download plink.exe seperately, to the folder in question, then delete it when you're done...
[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

---

### Post by gmalac on 2007-03-23
Believe it or not, I'm still struggling with the problem... but made some progress! 

I tried Jonne' proposal because indeed it seems so simple.. but I could not mount the disks (errors with file system, bad superblock...).

Then went back to geihra' proposal and found out about plink and yesterday evening was able to start things moving. 

From within WinXp: 
> plink [email]root@ubuntu.box[/email] **_sudo_** tar jc /home >backup-home.tar.bz2 
It asked the root password and started building the file on the WinXp box. That was yesterday 11PM and now some 14 hours later the file is 36GB!

The good news is that it seems to work, it passed the limit of 2GB I had before (samba?), the less good news is the time it takes: should run another 20 hours at that rythm! Anyway I am happy if it works. Now assuming that it will, I'lll have to find out about the other part, switching disks and getting this back into Ubuntu, but that will be another story!

I'll keep you posted and thanks again for the support!

---

### Post by geirha on 2007-03-24
I knew it would take alot of time, but ~40 hours or so I wouldn't have expected. But anyway, sounds like you haven't formatted the new disk properly, since you are getting errors about bad superblocks. Perhaps you only partitioned it, but not formatted (created a filesystem on) it?

As for getting the stuff back to the ubuntu box, I would use pscp (also part of putty) to just copy the archive back, and then unpack it. Hopefuly that would be a bit faster than doing both at the same time. The command would be ```
pscp backup-home.tar.bz2 [email]root@ubuntu.box[/email]:/home/
```
and then on the ubuntu box:
```

cd /
tar xf /home/backup-home.tar.bz2

```

---

### Post by crouton on 2007-03-24
I have a foolproof way, but it requires two separate programs that boot from LiveCDs.

In short:
1) Download Ranish Partition Manager (either standalone or in a CD like SysRescCD)
2) Do a clone-drive from the smaller /home drive to the target (larger) drive.  Disconnect and remove the smaller drive when completed.
3) Download GParted LiveCD, boot, and expand the (Ext3/Reiser/etc) partition on the larger drive to fill the entire drive capacity.

That's it - you'll have a perfect copy of your existing /home structure, expanded to take advantage of the larger physical drive.  FYI, this is my preferred way to expand Windows system partitions - you can't do it while Windows is loaded (like you can with any other Windows partition) and NTFS is very cranky about mismatched partition sizes.

---

### Post by gmalac on 2007-03-27
OK, success at last but....
First for the time it took over 38 hours for some 87GB of data! 
As I could not manage to get this back into Ubuntu I lost patience and just deleted all my backup data to reduce the size to less than 2GB
I could then go it back into UBUNTU using SMB but not before experiencing a series of error of the like like UUID... (put a long number string here). 
I finally realized that something (RescueCD?, Ubuntu on LiveCD?) modified my /etc/fstab adding UUID ...... to hda and hdb. Removing that did the trick and now I am very happy to have the new bigger second hd installed (actually running full backuppc at that time to reconstruct the backup).
THANKS VERY MUCH to all of you who helped me one way the other!
Guy

---

