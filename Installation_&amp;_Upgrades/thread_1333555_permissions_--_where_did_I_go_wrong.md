---
title: "permissions -- where did I go wrong?"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by linuxgrrl on 2009-11-21
hello,
I have a small-ish hard drive with mythbuntu 9.10rc1 installed, and a second, much larger drive with all my photos and songs on it.  The partitions of the larger drive are mounted under /media/photos and /media/music, using the following lines in /etc/fstab:

```
/dev/sdb1       /media/music            ext3    defaults 1  2
/dev/sdb2       /media/home_video       ext3    defaults 1  2
/dev/sdb3       /media/photos           ext3    defaults 1  2
```

I've made the permissions about as liberal as i know how:
```
mary@mythbox:~$ ls -la /media
total 32
drwxrwxrwx  8 mary root 4096 2009-11-09 19:58 .
drwxr-xr-x 23 root root 4096 2009-11-20 22:53 ..
lrwxrwxrwx  1 root root    6 2009-11-06 21:03 cdrom -> cdrom0
drwxrwxrwx  2 root root 4096 2009-11-06 21:03 cdrom0
lrwxrwxrwx  1 root root    7 2009-11-06 21:03 floppy -> floppy0
drwxrwxrwx  2 root root 4096 2009-11-06 21:03 floppy0
drwxrwxrwx 11 mary root 4096 2009-10-24 20:14 home_video
drwxrwxrwx 18 mary root 4096 2009-11-17 20:53 music
drwxrwxrwx  3 root root 4096 2009-11-20 22:30 mythvideo
drwxrwxrwx 12 mary root 4096 2009-11-19 13:41 photos

```

Yet none of my songs will play (neither rhythmbox nor banshee) and my photos are greyed out when I try to import into F-spot.  These collections were all created on a prior version of Ubuntu, then copied from an external drive to the local drive. 

Help!!  Is there something wrong with my /etc/fstab, those lines are examples I pulled from the web.

---

### Post by presence1960 on 2009-11-21
I would first mount the music and photo directories in file browser. Once mounted open a terminal and run ```
gksu nautilus
```. In nautilus go FileSystem> media. Right click each directory in question & choose properties. On the permissions tab check the permissions of the directory. Make sure it is not root. Change Owner to your user name & set permission to create & delete files.
Do the same for the other directory. You should now have read/write permissions.

If the above already has you as owner of those 2 directories I can think of another scenario. Are your files in those directories showing up in file browser with a lock? That sometimes happens when you copy over files from another media. if so use the chown command to take ownership of those files. Preface chown with sudo.

---

### Post by oldfred on 2009-11-21
I have a few more parameters on my /data fstab entry:

# Entry for /dev/sdc6 :
UUID=a55e6335-616f-4b10-9923-e963559f2b05 /home/fred/data ext3 auto,users,rw,relatime 0 2

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
# see above for labeling & mounting & permissions
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
see this for fstab info:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by linuxgrrl on 2009-11-22
It must be something other than permissions. 

presence, I tried what you said and all the owners and permissions were correct.  

oldfred, I unmounted the /media/music, edited /etc/fstab to match yours and re-mounted ... songs STILL will not play in any media player in linux.  

The player will appear to open the file, shows the correct song length but when I press play nothing happens (no elapsed time on the song).  Starting the players from the terminal yields no helpful error messages.  But when i use a friend's mac to access the songs via samba, they play just fine in itunes and VLC, so I know theres nothing wrong with the files.

What could possibly be wrong here?  I'm completely flummoxed.  I've just built a brilliant new media center that won't, er, play media.

I should mention the songs are all encoded in ogg so it's not a lack of decoders (at least I think not).

---

### Post by linuxgrrl on 2009-11-22
Okay, I'm partway there figuring it out.  Mythtv was open in another desktop ... when I close it, the songs will play.  Clearly myth is hogging the sound card ... I will head over to the proper forum to solve this. 

Although why none of the music players would provide a useful error message, even in debug mode, is beyond me.  I've been working on this problem for a while now.  Argh.

---

### Post by kedarm on 2009-11-23
Hi!

I'm having some problems with my partitions as well. I have a fat32 partition with the following fstab entry :
> /dev/sda9 /media/Dump  vfat	auto,users,exec,rw 	0	0

However, if I try to modify any contents on the drive, I get the following error -
> $ mkdir test
mkdir: cannot create directory `test': Permission denied

I have tried changing the permissions, but the permissions don't change at all! This was my original permissions (when I do ls -al) :
> drwxr-xr-x 13 root root    16384 1970-01-01 05:30 Dump
So, I gave the following command -
```
$ sudo chmod -R 777 /media/Dump
```
But, if I list the contents of /media, I get the same (unchanged) permissions -
> drwxr-xr-x 13 root root    16384 1970-01-01 05:30 Dump

How can I change the permissions of /media/Dump such that I can read/write/execute without becoming root each time?

Thanks
Kedar

---

### Post by oldfred on 2009-11-23
This is my entry for vfat and I have had no issues:

# Entry for /dev/sdc8 :
UUID=F6A6-705D                             /media/gdrive      vfat         user,auto,fmask=0111,dmask=0000      0  0  

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
# see above for labeling & mounting & permissions
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

HowTo Mount a Fat32 / Vfat Partition Read Write in Ubuntu & Kubuntu
[http://ubuntu.swerdna.org/ubufat32.html](http://ubuntu.swerdna.org/ubufat32.html)

see this for fstab info:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
 GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

---

