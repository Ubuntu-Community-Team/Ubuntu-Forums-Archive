---
title: "[SOLVED] Installing with /home on NTFS partition"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by Armaron on 2008-08-26
I've looked around and I've seen a lot of advice to put the /home folder on a diffrent partition. I want to do this, but I like to get 2 flies in 1 stroke.

Is it possible to put the /home folder on an NTFS partition? I know Ubuntu and Windows can both read and write to this type of partition. I prefer the NTFS over FAT32 that's been recommended all over the web because it's a bit friendlier with storing files.

The reason I ask is because I got quite the collection of films I want to share with the rest of my dorm. And I want to keep them all in my /home/movies/ folder. But seeing as the rest uses Windows (either XP or Vista), I want to make sure they can read my films. Don't want to format a big part of my drive as a partition they can't read (ext3).

Already thanks!

---

### Post by xdarkxanarchyx on 2008-08-26
You could use [Ext2 IFS]("http://www.fs-driver.org/") for reading/writing to an ext3. Or you should be able to edit your fstab. Do you already have everything installed and configured?
Anyway... ```
 sudo nano /etc/fstab 
``` then add ```
 /dev/sdXY   /home   ntfs  defaults  1 1 
```

You may have to use the UUID of the disk rather than /dev/sdXY so do ```
 blkid 
``` and that'll list all discs and partitions and give you the UUID.

Does the partition with the data already exist or are you making it?

---

### Post by Armaron on 2008-08-26
Nope, my new PC is comming in this week. Changing from Windows XP to Ubuntu.

Thanks for the info, this means I can put the /home on an NTFS volume.

Hmmm... I should really read up on file sharing in Ubuntu.

---

### Post by prshah on 2008-08-26
> **armaron said:**
> 
is it possible to put the /home folder on an ntfs partition? 

> **armaron said:**
> this means i can put the /home on an ntfs volume.


no no no no no no no no no no no no no no no no no no no no no

Nope you cannot put "/home" on an NTFS partition because of permissions issues. NTFS does not have unix-like ownership and permission systems.

However, you can put /home/movies on an NTFS partition and /home on a separate ext3 partition, there is no conflict. In this case, you will have to manually create the "/home/movies" directory after installation, and then add an fstab entry that will tell ubuntu which ntfs partition has to be mounted to "/home/movies"; be sure to include the umask (user mask) directive, otherwise only root (sudo) users will be able to access it.

btw, how are your dorm mates going to access this? Via the network? In which case there's no need to worry about NTFS/ext3, since network access will work irrelevant of the underlying storage system.

---

### Post by Armaron on 2008-08-26
> **prshah said:**
> btw, how are your dorm mates going to access this? Via the network? In which case there's no need to worry about NTFS/ext3, since network access will work irrelevant of the underlying storage system.

I knew I had to read up on sharing stuff. Thanks for clearing that up. After three years of computer science I (sometimes) still feel like a dumbass.

Well, that saves me a whole lot of hassle, thanks man.

---

### Post by prshah on 2008-08-26
> **Armaron said:**
> 
Well, that saves me a whole lot of hassle, thanks man.

Heh, I wish you luck with samba (windows network configuration); I've personally had no problems with it at all, but the forums are crawling with messages related to samba not working!

Cheers, post back if you need help with the networking part.

In the meantime, you should mark this thread as solved; near the top right hand side of the page, click on "Thread tools"-"Mark thread as solved".

---

### Post by mkoonstra on 2008-08-26
> **prshah said:**
> no no no no no no no no no no no no no no no no no no no no no

Nope you cannot put "/home" on an NTFS partition because of permissions issues. NTFS does not have unix-like ownership and permission systems.

However, you can put /home/movies on an NTFS partition and /home on a separate ext3 partition, there is no conflict. In this case, you will have to manually create the "/home/movies" directory after installation, and then add an fstab entry that will tell ubuntu which ntfs partition has to be mounted to "/home/movies"; be sure to include the umask (user mask) directive, otherwise only root (sudo) users will be able to access it.

btw, how are your dorm mates going to access this? Via the network? In which case there's no need to worry about NTFS/ext3, since network access will work irrelevant of the underlying storage system.

I have done this in another way. I wanted to share movies/music/data between windows and linux. So I mounted my data partition as /storage and deleted the folders in /home/<username> and made softlinks from within that folder to the data partition, this way I can quickly access them from within the file browser, like if they were in my home directory.

You can do something like:
ln -s Music /storage/Music
ln -s Movies /storage/Movies

But if the system is dedicated for running ubuntu only, I would suggest mounting a partition/hdd as /home instead.

---

### Post by unprinted on 2008-12-09
It *is* possible, but it means using a later version of the ntfs-3g drivers, and setting a compile-time option.

---

### Post by prshah on 2008-12-09
> **unprinted said:**
> It *is* possible, but it means using a later version of the ntfs-3g drivers, and setting a compile-time option.

Source? The only possible way is to use a loopback file device which can be placed on an NTFS drive; but the loopback device will be ext2/3 formatted (mkfs'd). Further, the loopback drive cannot be accessed in WinXP/Vista without third party software.

..but I'm open to corrections.

---

### Post by Mark Phelps on 2008-12-09
Aramaron:

I would strongly advise to NOT use an NTFS partition to store a file system that is actively going to change on a daily basis.  I tried doing that, even using NTFS-3G, and discovered that it is very easy to accidentally "break" the NTFS partition -- without any indication that it was happening.

I would discover the breakage when, upon a subsequent reboot, my machine would hang on loading FSTAB because the NTFS partition would not mount.  I would then have to boot into Windows, run chkdsk (sometimes more than once), and then reboot into Ubuntu.  This happened often enough that I eventually created a FAT32 partition, moved the shared files there, and changes my FSTAB to NOT mount the NTFS partition on startup.

If you use an NTFS partition to house a critical portion of your filesystem (like /home) you won't have the 'don't-mount-on-startup option and are asking for trouble.

I have found that FAT32 can be mounted by either Windows or Ubuntu, and doesn't present anywhere near the breakage rate of NTFS.

Also, if the NTFS partition houses Vista, especially if that is your "C" drive, then do NOT mount it automatically in Ubuntu.  If you do that, and it "breaks", you will have to use a Vista DVD or Vista Recovery, boot into one of them, and run Startup Repair in order to get Vista working again.

---

### Post by unprinted on 2009-01-05
> **prshah said:**
> Source? The only possible way is to use a loopback file device which can be placed on an NTFS drive; but the loopback device will be ext2/3 formatted (mkfs'd). Further, the loopback drive cannot be accessed in WinXP/Vista without third party software.

..but I'm open to corrections.

There is obviously a risk of losing data, but all I can say is that it's working here. 

**You need:**

[LIST]
[*]a system that will happily dual boot into Windows 2000/XP/Vista and Ubuntu.
[*]an NTFS partition for Windows' system files
[*]an ext3 or other format partition for Ubuntu's / partition
[*]an NTFS partition, preferably freshly formatted, to share between the two and which you can currently read/write to under Ubuntu
[*]an Ubuntu user account for all Windows user accounts who may wish to access the /home partition and vice versa
[*]printed instructions for moving /home onto a new partition. Various tutorials exist - I used [this one on psychocats]("http://www.psychocats.net/ubuntu/separatehome")
[*]an up to date backup (see warning on top!)
[*]to read all these instructions - if you don't feel able to do any of them, stop now!
[/LIST]

1. The ntfs drivers we will be using use a file, /.NTFS-3G/UserMapping, to tell it how to convert the Windows permissions system into the *ix one and vice versa. You can download Windows and Linux programs to generate the file [here]("http://pagesperso-orange.fr/b.andre/usermap.html").

You will end up with something like:

```

# Generated by usermap for Windows, v 1.1.0
:ian:S-1-5-21-3746740168-3059144531-1038510649-513
ian:ian:S-1-5-21-3746740168-3059144531-1038510649-1002

```

So 'ian', the Ubuntu user (and group) will be writing files with Windows permissions for user 1002 (as it happens, the Windows 'ian' account) with the Security Identifier (SID) of that long number.

There should be one line per user, typically in the order the accounts were created.

The usermap utilities are not particularly helpful in showing which named account uses which SID - if necessary, look at the Windows registry to map names to SIDs and edit the UserMapping file as necessary.

The resulting info which needs to go in /.NTFS-3G/UserMapping for each of the partitions you want to be able to use. 

2. Download the advanced ntfs-3g driver source code [from the ntfs-3g site]("http://pagesperso-orange.fr/b.andre/advanced-ntfs-3g.html"). As of writing, the latest version is 1.5130AR.1 - note the AR! Without that, you will have the standard drivers, without the permissions code.

3. Expand the zipped tarball - if you need to be told how, you should probably not try to do this, so stop now! - and change to the ntfs-3g-1.5130AR.1 directory (the name of this will change when the driver version number changes).

4. Even the advanced drivers do not have the necessary options installed by default, so you need to change

```
#define POSIXACLS 0
```

to

```
#define POSIXACLS 1
```

in include/ntfs-3g/security.h and src/secaudit.h

5. Remove the existing ntfs drivers

```
sudo aptitude purge ntfs
```

6. Install the new ntfs-3g drivers

```
./configure
make
sudo make install
```

7. Edit /etc/fstab (again, if you need to be told how, stop now)

The current driver for the partition you want to use (mine was previously mounted as '/data') will probably be ntfs, change it to ntfs-3g with options 'defaults,nodev,nosuid'

```
UUID=(16 digit hex number) /data ntfs-3g defaults,nodev,nosuid 0 1

```

8. Reboot back into Ubuntu. You should be able to access the same ntfs partitions as before.

9. Follow the 'move /home to a new partition' instructions, from the point where you have created the new partition. You will need to change lines like

```
sudo mount -t ext3 /dev/sda3 /new
```

to

```
sudo mount -t ntfs-3g /dev/sda3 /new
```

(As mentioned on that how-to, your device will probably be different - mine is /dev/sda6, for example)

You will know if something has gone wrong if

```
find . -depth -print0 | cpio --null --sparse -pvd /new/
```

produces pages of errors. Permission errors probably point to a problem with your UserMapping file or a failure to edit the ntfs-3g source code.

---

