---
title: "Moving Data from old partitions to new failed 24.04 install"
date: 2024-11-07
forum: Installation &amp; Upgrades
---

### Post by wcalvert on 2024-11-07
This is a follow on question from another post attempting to fix a failed install of 24.04.  In the end there are two installations of  24.04 on my machine, along with an existing Windows boot option.  The two 24.04 boot options exist on two different partitions, but one does not appear to be viable.  Neither will access any data on the other partitions (data meaning documents, files, configurations, etc.), nor have I been able to determine if any data still exists on those partitions.

You can wade through all the painful details of the last post if you prefer, there is some useful information there:  Corrupted Boot partition after upgrade to 24.04 ([https://ubuntuforums.org/showthread.php?t=2502153](https://ubuntuforums.org/showthread.php?t=2502153)).  It's marked "solved" but not really!

I do have an image file of the entire drive in question, but unfortunately no backup I can return to.  If we can't reproduce the system as it was, I would at least like access to the data that remains.

[U]So my question is: how could I proceed to "connect" "link" (I'm a beginner) the old partitions to the new install in order to restore access to the data?

[/U]
I appreciate the help, and am amazed at the willingness of the volunteers (OldFred, Yancek, grahammechanical and many others) to help a flailing beginner!  
Ready to listen.  Cheers

---

### Post by oldfred on 2024-11-07
File browser should let you click on partition and browse folders.
If an install you would need to drill down from / to /home to /home/$USER where that is your name in that system.

Part of reason I prefer to always label partitions. You can use Disks, Gparted, or terminal.
Then default mount by file browser is by label, not some very long UUID that may be confusing. I do not know one UUID from another, but labels let me know what partition I am temporarily mounting.

---

### Post by wcalvert on 2024-11-07
Just to be clear, "File browser" refers to the icon on the left (my  screen) that looks like a file folder, correct?  If that's so, I am  unable to find any option to look at a partition, only the default  options like downloads, documents, etc ...

I'm clearly missing something and need a low altitude explanation, maybe  pictures.  This could just be a matter of slang language, but I'm stuck  from moving ahead.

Then you say:  > "If an _install_ you would need to .. "  You lost me on that comment too.   Can you explain by what you mean by "install"?


Thanks

---

### Post by oldfred on 2024-11-07
I have not use Nautilus, the file browser for Ubuntu for ages, so it has lots of changes.
I now use Kubuntu which uses the Dolphin file browser. Functions are similar but details are different.
You should also have a way to open all other partitions.

Post this:
lsblk -e 7 -o name,fstype,size,fsused,label,UUID,mountpoint

---

### Post by wcalvert on 2024-11-07
Here it is ...

> ID,mountpoint 

NAME  FSTYPE   SIZE FSUSED LABEL UUID                                 MOUNTPOINT
sda          931.5G                                                   
&#9500;&#9472;sda1
&#9474;     vfat     499M  54.2M ESP   EEDC-1691                            /boot/efi
&#9500;&#9472;sda3
&#9474;     ntfs   442.7G  36.7G OS    2E38DFD638DF9B63                     /media/wil
&#9500;&#9472;sda5
&#9474;     ext4   196.1G              2e8a4205-058b-44bc-810a-910260e478f3 
&#9492;&#9472;sda6
      ext4   291.7G  11.8G       1aceb469-c683-41a0-81e3-ede8fe0ff4b4 /

---

### Post by tea for one on 2024-11-08
> **wcalvert said:**
> Just to be clear, "File browser" refers to the icon on the left (my  screen) that looks like a file folder, correct?  If that's so, I am  unable to find any option to look at a partition, only the default  options like downloads, documents, etc ...
I'm clearly missing something and need a low altitude explanation, maybe  pictures.  This could just be a matter of slang language, but I'm stuck  from moving ahead.
Using Ubuntu 24.04 (either a live session or installed OS)
Open the file manager (Files also known as nautilus)
Do you see "+ Other Locations"?

---

### Post by oldfred on 2024-11-08
Your lsblk shows no sdb drive?

Is this an internal drive?
And is it shown in UEFI/BIOS settings. Under drives or similar settings somewhere should be a list of connected drives/devices.
If not shown, software will never find drive. Then check connections both power & signal.

---

### Post by TheFu on 2024-11-08
```

NAME FSTYPE SIZE FSUSED LABEL UUID MOUNTPOINT
sda 931.5G
&#9500;&#9472;sda1 &#9474; vfat 499M 54.2M ESP EEDC-1691 /boot/efi
&#9500;&#9472;sda3 &#9474; ntfs 442.7G 36.7G OS 2E38DFD638DF9B63 /media/wil
&#9500;&#9472;sda5 &#9474; ext4 196.1G 2e8a4205-058b-44bc-810a-910260e478f3
&#9492;&#9472;sda6 ext4 291.7G 11.8G 1aceb469-c683-41a0-81e3-ede8fe0ff4b4 / 
```

Looks to me like sda5 isn't mounted. Could that 196GB have the data you seek?
Because you didn't use forum code-tags, this looks ugly when it shouldn't.

---

### Post by oldfred on 2024-11-08
Sorry thought data was on separate drive, ignore that post.

Can you manually mount sda5 when booted in sda6?
from terminal
sudo mkdir /media/$USER/tempdata
sudo mount /dev/sda5 /media/$USER/tempdata -o umask=000

---

### Post by wcalvert on 2024-11-08
Yes, one internal drive, and I've tried mounting sda5 on Gparted and the option is not available.  From you request:

> $  sudo mount /dev/sda5 /media/$USER/tempdata -o umask=000 
mount: /media/wilson/tempdata: wrong fs type, bad option, bad superblock on /dev/sda5, missing codepage or helper program, or other error.
       dmesg(1) may have more information after failed mount system call.


---

### Post by wcalvert on 2024-11-08
> Using Ubuntu 24.04 (either a live session or installed OS)
Open the file manager (Files also known as nautilus)
Do you see "+ Other Locations"?                 

Other Locations is there but does not show the drive that is sda5 (196G), only sda3 (OS) and sda6 (Ubuntu)

---

### Post by tea for one on 2024-11-08
If you open Disks, is sda5 listed?

---

### Post by wcalvert on 2024-11-08
> If you open Disks, is sda5 listed?                 

Yes, and I can mount it from Disks.  That's the firs time I've been able to do so!  

Now when I 'drill down" as Oldfred mentioned, I can see the files!  Brilliant

[B][SIZE=3]I feel like I owe the group a Scotch!
[/SIZE][/B]
So now, any "easy" way to move ahead with reconstruction?

---

### Post by TheFu on 2024-11-09
Easy is subjective.
I'd use **rsync**.  

```
sudo rsync -avz  {SOURCE} {TARGET}
```

Both the source and target file systems must be mounted.  
```
NAME FSTYPE SIZE FSUSED LABEL UUID MOUNTPOINT
sda 931.5G
&#9500;&#9472;sda1 &#9474; vfat 499M 54.2M ESP EEDC-1691 /boot/efi
&#9500;&#9472;sda3 &#9474; ntfs 442.7G 36.7G OS 2E38DFD638DF9B63 /media/wil
&#9500;&#9472;sda5 &#9474; ext4 196.1G 2e8a4205-058b-44bc-810a-910260e478f3
&#9492;&#9472;sda6 ext4 291.7G 11.8G 1aceb469-c683-41a0-81e3-ede8fe0ff4b4 /
```

So, which is the SOURCE and which is the TARGET?  You'll need to mount sda5 somewhere - I'd put it somewhere temporary, like /mnt/a5 (mkdir /mnt/a5) first.  Then I'd carefully decide what I want to copy from there.  rsync is a tool for copying files.

OR you can be smarter and turn sda5 into the /home/ for the computer.  You'll just modify the fstab to add it there, but there are some details that need to be handled, like deleting the old files you don't want, moving the stuff you do want to the correct relative location (moves are instantaneous inside the same file system) and you'll likely want to clean-up or merge any new files on sda6 in the HOME there.  Of course, permissions need to be maintained too. There are lots of How-To guides for moving HOME directories to a different partition.  [https://www.howtogeek.com/442101/how-to-move-your-linux-home-directory-to-another-hard-drive/](https://www.howtogeek.com/442101/how-to-move-your-linux-home-directory-to-another-hard-drive/) is one.   The overview is to add the new storage/partition/file system to where you need it to appear in the storage layout.  This is really easy, since in Linux, we can mount file systems exactly where we need them - no "drive letters".  

I'd show examples, but that might just confuse you.  Skim that HowToGeek article and see if that is something you'd understand and can do. "Easy" is subjective.  Only you can decide.

There are other techniques to add large areas of storage for use to a system as well.  They leverage symbolic links.  Lots and lots of people here use them to make storage that happens to be mounted elsewhere seem to be part of their HOME.  Remember, the OS doesn't care were data is actually stored. It just wants it to APPEAR to be where it is expected.  Symbolic links can make storage "appear" to be in the expected location.   [https://en.wikipedia.org/wiki/Symbolic_link](https://en.wikipedia.org/wiki/Symbolic_link)  Unix has had symlinks for many, many, decades.  Linux has this same type. There is also a "hard link", but that's different and typically used in Unix/Linux versioned backups - Back-In-Time - uses hardlinks, for example.    Anyway, I think Oldfred uses this technique for making extra storage easily available but appears to be in a HOME directory.

---

### Post by oldfred on 2024-11-09
Did not the file browser give the same errors?
That would have been good to know.

Make sure partition is not mounted.
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/sda5
# -y auto answers yes for fixes needing response,
sudo e2fsck -f -y -v /dev/sda5
 also see:
man e2fsck

---

### Post by TheFu on 2024-11-09
I've never, ever, used **e2fsck** directly.  What's wrong with using **fsck** and letting it choose the correct program based on the file system?

---

### Post by wcalvert on 2024-11-09
Guys, thanks for the ideas.  I'll do some reading while you two battle it out about the best approach!  Always another way to skin the rat

---

### Post by wcalvert on 2024-11-09
> Did not the file browser give the same errors?
That would have been good to know.

so the question is ... why is it that Disks and File Browser are not behaving the same way, as in one would mount the partition but the other did not offer the option?

---

### Post by TheFu on 2024-11-09
> **wcalvert said:**
> so the question is ... why is it that Disks and File Browser are not behaving the same way, as in one would mount the partition but the other did not offer the option?

Because a File Browser doesn't do local mounts.
Mounting storage is a big deal.  The power to mount is the power to destroy, but lots of Linux people either never realized that or decided to forget it.

Because we can't see what sda5 actually holds, I'll make some huge assumptions which are probably true, but may not be.  Hopefully, if others think I'm incorrect, they will point it out. Wouldn't be the first time I was wrong.  Mainly, I'm assuming there's a prior Linux install, including another HOME directory, under sda5.  _**[COLOR="#FF0000"]So, DOES sda5 HAVE THE OLD INSTALL?[/COLOR]**_  That's the main question we need answered.

For you, I think the best option is to mount sda5 under /media/DATA using the fstab method, then inside your HOME directory, create a symbolic link with 
```
ln -s  /media/DATA/home/wcalvert ~/data
```

In this way, you'll be able to access YOUR old data in sda5 in the older HOME directory as ~/data/ from any program you like (snap packaged programs might need some coaxing), and you don't need to move anything at all.  Over time, you can clean up/remove all the other directories in /media/DATA as you like.

---

### Post by wcalvert on 2024-11-09
TheFu

Thanks for your suggestion.  I like the ability to get the system back up without a bunch of Terminal work that makes me a bit nervous.  

For an update, I restarted the system and let it boot per it's default path, and once it did, the sda5 partition was once again not mounted.  Obviously that will need to be reconciled before this system works properly (my thoughts only).

And you write:

> I'm assuming there's a prior Linux install, including another HOME directory, under sda5.  _**[COLOR=#FF0000]So, DOES sda5 HAVE THE OLD INSTALL?[/COLOR]**_  That's the main question we need answered.

I looked under sda5 and only found 1 home, dated 2018, about when this computer was first commissioned.

and ...

> Because we can't see what sda5 actually holds 

I can see what is in sda5 once I mount it thru DIsks, and it looks to be all my own data.  

So does your recommendation still hold?  If so, I'll need another question answered before proceeding.

---

### Post by wcalvert on 2024-11-09
I just opened the fstab file to compare it to the article   [https://www.howtogeek.com/442101/how...er-hard-drive/]("https://www.howtogeek.com/442101/how-to-move-your-linux-home-directory-to-another-hard-drive/")
Anything interesting here?  Looks like a mess to me

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during curtin installation
/dev/disk/by-uuid/1aceb469-c683-41a0-81e3-ede8fe0ff4b4 / ext4 defaults 0 1
# /boot/efi was on /dev/sda1 during curtin installation
#/dev/disk/by-uuid/EEDC-1691 /boot/efi vfat defaults 0 1
/swap.img    none    swap    sw    0    0
UUID=EEDC-1691  /boot/efi       vfat    defaults      0       1
```

---

### Post by TheFu on 2024-11-09
These are all 1-time commands.

Run this:
```
sudo mkdir  /media/DATA
```

Then add this line to the bottom of your /etc/fstab (use **sudoedit /etc/fstab** as the command)
```
UUID=2e8a4205-058b-44bc-810a-910260e478f3   /media/DATA    ext4  defaults   0     2
```
If you are interested in some more secure options, ask. I seldom use "defaults" when I mount storage.  I tend to use *nodev,nofail,noatime,errors=remount-ro* for base options of data-only areas.

Now run these commands to mount the storage:
```
sudo systemctl daemon-reload
sudo mount -a
```

The storage should be mounted in /media/DATA now.  Check this with 
```
ls -l /media/DATA 
```
Only "home" should be there, if what you've said already is true. If you see more stuff there, stop.

Take ownership of the HOME under that location AND set reasonable permissions:
```
sudo     chown      -R      wcalvert:wcalvert       /media/DATA
chmod     -R      ug+w,o-w       /media/DATA
```

Those 2 commands may not be necessary if the uid/gid currently used AND used before on the other storage match.  Allso, that **chmod** command might break some picky security-related things, like ssh, so if you use/used ssh previously, you may not want to run the **chmod** at all.  See if not having that works for your needs for a few days.  I think the **chown** command should be safe and may actually fix a few things. There's a risk in trying to be complete, but not seeing what the truth is.

Don't worry about the extra spaces, 1 is enough between the different parts of those command. I was just trying to be VERY obvious.

And lastly, to create the symlink in your current HOME directory, run 
```
ln -s  /media/DATA/home/wcalvert ~/data
```

I've made assumptions about your username and groupname. All but the last command use sudo.  After running the last command you should be able to use ~/data whenever you want to open any file or save any file and it will end up on sda5, which we mounted under /media/DATA.

Since this is your machine, you can mount it almost anywhere, but the command above will need to be tweaked for any changes. I tried to be consistent.

And you can look up what every command does and what that fstab line does. Please do.

Hopefully, others will see any problems here and provide corrections.

---

### Post by TheFu on 2024-11-09
> **wcalvert said:**
> I just opened the fstab file to compare it to the article  .... Looks like a mess to me

```

/dev/disk/by-uuid/1aceb469-c683-41a0-81e3-ede8fe0ff4b4 / ext4 defaults 0 1
/swap.img    none    swap    sw    0    0
UUID=EEDC-1691  /boot/efi       vfat    defaults      0       1
```

are the only real lines. The others are all comments.

**Nothing odd, not really.**  I don't do things the way the installer did. I hate extra characters that are meaningless and I despise using a swap file (I much prefer swap partitions), but that's the normal expectations in Ubuntu these days.  I do lots of things different than the defaults so useful information that means something is in my fstab for mounts.  UUIDs are fine for computers, but suck for humans.  There are other options, but those other options to safely denote which partition is which partition aren't programmatically easy, I guess.

I wouldn't bother changing those lines ... unless you want to make each field line up for all 4 lines you'll have after you add the line I provided above.

BTW, in my most recent post, I hope it is clear, doing that stuff will make the storage all there after reboots too. It really is a 1-time thing.

---

### Post by wcalvert on 2024-11-09
Dang, I feel like I'm listening to my old college roommate who could diagnose an old Windows computer by laying his hands on it, and then explaining the fix in a foreign language while reducing wasted memory and unnecessary code, typing it all in at the same time!!

I do appreciate the detailed instructions ... I fly big planes for a living, computers left me behind decades ago.  Time to press on and get this thing fixed.

Cheers

---

### Post by wcalvert on 2024-11-09
Oh geez ...  you say > Only "home" should be there, if what you've said already is true. If you see more stuff there, stop.
There is a "home" there, but a lot of other stuff .  Stopped ...


```
lson@wilson-Inspiron-5770:~$ ls -l /media/DATA
total 947272
lrwxrwxrwx   1 root root         7 Jun 10  2023 bin -> usr/bin
drwxr-xr-x   2 root root      4096 Mar 31  2024 bin.usr-is-merged
drwxr-xr-x   5 root root      4096 Oct 30 09:26 boot
drwxrwxr-x   2 root root      4096 Mar 18  2018 cdrom
drwxr-xr-x   4 root root      4096 Jan  5  2018 dev
drwxr-xr-x 159 root root     12288 Oct 30 09:19 etc
drwxr-xr-x   2 root root      4096 Apr 23  2021 hdd
drwxr-xr-x   3 root root      4096 Mar 18  2018 home
lrwxrwxrwx   1 root root        34 Nov 18  2020 initrd.img -> boot/initrd.img-4.15.0-124-generic
lrwxrwxrwx   1 root root        34 Nov 18  2020 initrd.img.old -> boot/initrd.img-4.15.0-123-generic
lrwxrwxrwx   1 root root         7 Jun 10  2023 lib -> usr/lib
lrwxrwxrwx   1 root root         9 Jun 10  2023 lib32 -> usr/lib32
lrwxrwxrwx   1 root root         9 Jun 10  2023 lib64 -> usr/lib64
drwxr-xr-x   2 root root      4096 Feb 14  2024 lib.usr-is-merged
lrwxrwxrwx   1 root root        10 Jun 10  2023 libx32 -> usr/libx32
drwx------   2 root root     16384 Mar 18  2018 lost+found
drwxr-xr-x   5 root root      4096 Apr 23  2021 media
drwxr-xr-x   2 root root      4096 Jan  5  2018 mnt
drwxr-xr-x   7 root root      4096 Oct 21 17:56 opt
drwxr-xr-x   2 root root      4096 Mar 20  2018 pia
drwxr-xr-x   2 root root      4096 Oct 16  2017 proc
drwx------  10 root root      4096 Oct 30 09:57 root
drwxr-xr-x  10 root root      4096 Jan  5  2018 run
lrwxrwxrwx   1 root root         8 Jun 10  2023 sbin -> usr/sbin
drwxr-xr-x   2 root root      4096 Feb 14  2024 sbin.usr-is-merged
drwxr-xr-x  35 root root      4096 Jul  5 18:22 snap
drwxr-xr-x   2 root root      4096 Jan  5  2018 srv
-rw-------   1 root root 969815040 Mar 18  2018 swapfile
drwxr-xr-x   2 root root      4096 Oct 16  2017 sys
drwxrwxrwt   7 root root     69632 Nov  6 18:47 tmp
drwxr-xr-x  16 root root      4096 Jun 10  2023 usr
drwxr-xr-x  15 root root      4096 Oct 30 09:19 var
lrwxrwxrwx   1 root root        31 Nov 18  2020 vmlinuz -> boot/vmlinuz-4.15.0-124-generic
lrwxrwxrwx   1 root root        31 Nov 18  2020 vmlinuz.old -> boot/vmlinuz-4.15.0-123-generic
wilson@wilson-Inspiron-5770:~$ 
```

---

### Post by TheFu on 2024-11-10
> **wcalvert said:**
>  I do appreciate the detailed instructions ... I fly big planes for a living, computers left me behind decades ago.  Time to press on and get this thing fixed.

Everyone has their areas of expertise.  I used to write code for avionics systems. Trained as an ASE in CFD.  My father was a pilot - 8-engine jets (you can probably name that plane), a few others (some supersonic) and flew a single engine O-1 in SE Asia as a FAC (ever see BAT-21?).  I grew up around aircraft and worked in the space industry, but realized the opportunities for my specific love were more generic and could include non real-time systems too. ;)

As for what you are seeing under /media/DATA .... you probably weren't using anything except the data files in /media/DATA/home, so it should be safe to delete everything else.  Then you can move on and decide about the stuff under /media/DATA/home/ that you want to keep.  I'd just keep the actual data files, not any of the other stuff if it were me.  Getting fresh settings and initialization files is something I like to force every 3-5 yrs.

And then you can continue with the instructions from where you left off.  Only you will know which data files are important or not below there.

---

### Post by wcalvert on 2024-11-10
TheFu, thanks for the confirmation and some of your history.

So the rest of the instructions did what they needed to do and I have access to my data.  That was the goal and it worked (with a bit of cleanup to do now!)  Now I'm looking to do some more restoration work like settings and preferences that were in place for browsers etc. before the crash.  Specifically the tool bar in Ubuntu and the short cut links in my browsers.  Is that something you 'll remark on or should it be started in a new thread?

---

### Post by TheFu on 2024-11-11
I know little about web browsers. You might be able to just copy/move those settings from the old HOME directory structure into the new one and it will probably work.  OTOH, migrating old settings from many releases prior to the current release for any program may break some things in the program.  YMMV.

---

### Post by oldfred on 2024-11-11
If you copy everything from old /home to new /home, it should include all your user settings and hidden (.) configuration files.
Firefox & Thunderbird by default with pre-snap versions kept all data in /home. Not sure about snap version where data is stored as I do not use snaps.

Probably first thing you need to do is set up a good backup procedure, then you can restore /home, list of installed apps & any other system settings you may have changed back into new install easily.

---

### Post by wcalvert on 2024-11-11
Guys, I was thinking the same about moving stuff to the home folder.  I'll give it a try.  Thanks

---

### Post by wcalvert on 2024-11-11
TheFu
I'm revisiting an earlier post and trying use rsync to clean up the long path to sda3 where my data resides. I would also like to attempt to move all the configuration files for browsers etc. to the highest "home" directory.

My old home is backed up outside the system, so I'm ready to try.

You mentioned using rsync, and you posted:

> I'd use **rsync**.  

     Code:
     sudo rsync -avz  {SOURCE} {TARGET} 
Both the source and target file systems must be mounted.  
     Code:
     NAME FSTYPE SIZE FSUSED LABEL UUID MOUNTPOINT
sda 931.5G
&#9500;&#9472;sda1 &#9474; vfat 499M 54.2M ESP EEDC-1691 /boot/efi
&#9500;&#9472;sda3 &#9474; ntfs 442.7G 36.7G OS 2E38DFD638DF9B63 /media/wil
&#9500;&#9472;sda5 &#9474; ext4 196.1G 2e8a4205-058b-44bc-810a-910260e478f3
&#9492;&#9472;sda6 ext4 291.7G 11.8G 1aceb469-c683-41a0-81e3-ede8fe0ff4b4 / 


I did one rsync and it moved the whole home, but I don't know where it went!  You'd probably puke if you looked into the bowels of my system!

Going to the old home on sda5, the path appears to be /media/data/home/wcalvert/ ... ?  So the command would be:

sudo rsync -avz  /media/data/home/wcalvert/  /home/

I'm doing something wrong since it says it can't find the directory but that path is what Disks shows.   Anyhow, can you give me an example of the proper syntax for the rsync command?  Too many /? missing a comma ?
Thanks

---

### Post by TheFu on 2024-11-12
rsync doesn't move anything. It copies it.  Now you have 2 or 3 COPIES of all that data.  Fine if you want a backup, but most of the time, we want backups to be on external storage devices and organized by the backup tool (not rsync).

```
sudo rsync -avz /media/data/home/wcalvert/ /home/
```
I suspect you've just got either the wrong target OR the wrong source.  Try 
```
sudo rsync -avz /media/data/home/wcalvert[COLOR="#FF0000"]/[/COLOR] /home/wcalvert[COLOR="#FF0000"]/[/COLOR]
```
***_OR_***
```
sudo rsync -avz /media/data/home/wcalvert   /home[COLOR="#FF0000"]/[/COLOR]
```

BTW, **rsync** behaves different when it does copies between two different computers and all inside the same computer.  In short, the "z" option says to use compression for the transfers.  When the data is all being copies inside 1 computer, asking for compression will was time.  And yes, I realize the -avz options are what I posted.  please, please, always review every command and learn what each option actually does. It is common for people to type things from memory that don't necessarily fit your situation completely.  The local manpage for rsync would be the best place to check options, since it will match the exact version of rsync you have installed.  Minor rsync options change all the time, but the major ones haven't changed in 25 yrs, so it isn't terrible to use tools like _explainshell.com_ to have that webpage look at the command with all options and only show the explanation of the relevant options.

Also, if getting everything correct in a terminal makes your brain freak out, there is a simplistic GUI for rsync - **grsync**.  It actually doesnt many anything easier or cleaner, but for some reasons it makes people afraid of CLI commands happier.  I'm at a loss for why.

---

### Post by wcalvert on 2024-11-12
Thanks!  I did review your -avz modifiers and they all make sense.  One little twist is that my old data uses a different name (wcalvert vs wilson) and that just makes it all the more confusing.  I'll sort it out.

and you comment: 

> it makes people afraid of CLI commands happier.  I'm at a loss for why.                 

is great.  I'm more comfortable flying my 777 across the pond!
Cheers

---

### Post by TheFu on 2024-11-12
username doesn't matter.  The uid and gid DO matter.
Those **chmod** and **chown** commands posted above should have addresses 99% of any issues.

And 777 for people lazy about file permissions. Don't use it if you care anything about security.  Unless you are talking about a B772-ER or B773-LR. ;)  Being correct and specific matters with permissions.  I get confused as to which sub-models have both ER and LR variants.

---

### Post by wcalvert on 2024-11-12
>  _explainshell.com_

This rocks, thanks

---

### Post by wcalvert on 2024-11-12
Here's another conundrum.  I did the rsync and believe the source/target are correct.  All the files moved across the screen on the terminal, I recognize the files names etc.   Source lookin' good at least.

Now the issue, the Target home folder has not changed.  This is a similar result from the first time I did the copy.  Looked around and can't find it anywhere.  Stumped ...

---

### Post by wcalvert on 2024-11-12
Update ... found the folder the rsync created in the new home folder, so that's progress.  But all the files are inside a folder labeled "wcalvert", (the source is correct), but have not replaced the folders they were meant to replace one for one.

How do I do this rsync copy so that each folder/file is replaced by the old version?

The command I used:

```
sudo rsync  -avz  /media/data/home/wcalvert/  /home/wilson/
```

---

### Post by TheFu on 2024-11-12
> **wcalvert said:**
>  How do I do this rsync copy so that each folder/file is replaced by the old version?

```
sudo rsync  -avz  /media/data/home/wcalvert/  /home/wilson/
```

I wouldn't want to replace the new with the old myself. There are likely going to be inconsistencies due to versioning.  You could move the old stuff out of the way and move the new stiff into that location.  Note - I'm using "move", not "copy".  rsync is a "copy", not a "move".

Trial and error?  Be certain you have backups of both sides so when you screw up the first few times, you'll be able to put things back as they were to try again.

Think about WHAT the *source* and the *target* options really say.  You may be off by 1 character. hint: learn about the trailing slash and what that means to rsync.

---

### Post by oldfred on 2024-11-12
When setting up a new rsync command I have to review this. And still often get it wrong & have to redo something.

man rsync has explanation of trailing /. these are the same, trailing / copies contents:
[https://wiki.archlinux.org/title/Rsync#Trailing_slash_caveat](https://wiki.archlinux.org/title/Rsync#Trailing_slash_caveat)

---

### Post by wcalvert on 2024-11-12
I discovered the importance of the trailing / while reading a tutorial ... so many of those powerful tidbits to learn.  Keep on

---

### Post by wcalvert on 2024-11-16
To close out this thread, here was my final epiphany:  Since 24.04 was not compatible with all my profiles in firefox etc, I just reverted the install to 22.xx and moved the profile files over as required.  Now when the time comes and I'm brave enough to upgrade to 24, everything will be in place.  Thanks for all your education along the way, getting smarter.

---

### Post by TheFu on 2024-11-16
> **wcalvert said:**
> I discovered the importance of the trailing / while reading a tutorial ... so many of those powerful tidbits to learn.  Keep on

Yes, handy when the directory has lots of .dotfiles inside it that would be missed otherwise.

---

