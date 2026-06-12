---
title: "Using SD Card as /Home, or an Extension of /Home?"
date: 2011-07-01
forum: Installation &amp; Upgrades
---

### Post by Kixtosh on 2011-07-01
I have installed Ubuntu Lucid Lynx to dual boot with Vista Business on a Toshiba Portégé R500. Everything seems to be working great out of the box, but I have a problem with available space on the rather modest (but spectacular performance) 64GB SSD.

**1) Current Partitions:**

Toshiba includes three partitions on the new 64GB system, to which I have added one primary Linux container partition, enclosing two logical partitions. 

- /dev/sda1 TOSHIBA SYSTEM VOLUME: [COLOR=DarkRed]1.6GB[/COLOR], Partition type "Unknown (0x27)
- /dev/sda2 Windows Vista Business: [COLOR=DarkRed]49GB[/COLOR], NTFS
- /dev/sda3 HDDRECOVERY: [COLOR=DarkRed]6.5GB[/COLOR], Hidden HPFS/NTFS (0x17)
- /dev/sda4 Linux Container for sda5 & sda6: 7.6GB, Extended
- /dev/sda5 Ubuntu Filesystem: [COLOR=DarkRed]6.6GB[/COLOR], ext4
- /dev/sda6 Swap Space: [COLOR=DarkRed]1.0GB[/COLOR], Linux swap

I'm sure I'll remove Vista eventually, but in the meantime, (along with MS Office) it requires a whopping 32GB just to admire itself, after all the updates and security upgrades have been applied. I shrunk the partition to 49GB to leave space for future updates and upgrades.

Right now, Ubuntu only occupies 2.4GB of it's allocated partition, leaving 3.6GB free (I know, that doesn't add up to 6.6GB, but that must be something to do with GiB vs. GB, ... or magic, maybe). Swap is only 1.0GB, with 2.0GB of RAM, but I don't use Hibernate.

**2) Installing /Home on SD Card**

Well, I tried this first, since I have a nice 8GB, Class 10 SD Card, and a built in SD Card reader. With the SD Card inserted during installation, I was able to select it and designate it as /Home, but when I tried to restart after insallation was complete, I got an error message before the Ubuntu login screen could appear. 

I think what is happening is that it doesn't mount normally when booting. It's not listed as a bootable device in BIOS, but there is a Toshiba Bootable SD Card utility included with Windows, which needs a bootable floppy or something to work. There must be something that allows the BIOS to recognize it as a floppy during boot, or whatever, but any Toshiba Utility isn't going to work with a Linux file system. Puppy doesn't like it either for the Puppy sfs saved user file (although it will usually work if I copy them there manually, rather than allow them to save automatically).

**3) Extending /Home to the SD Card**

I thought I'd just have to copy stuff to the SD Card manually, as extra storage, when /Home got too crowded and cosy. Then I noticed that as soon as I inserted the SD Card it immediately got added to the total space avaialable shown by the Disk Usage Analyser accessory (which just happened to be open at the time). So now I see 10.8GB total, which is plenty to start out with for me. I assume this is because the SD Card had been formatted to mount as /Home when I first tried that solution, and got recognized as soon as it was inserted in the slot.

**Questions:**

a) Will this work? Will /Home really use the extra space, or is it just "pretending"?
b) Is there anything special I might need to do?
c) What do I do with the three folders already on the SD Card, obviously put there during the failed attempt to install /Home on the card? (The third folder is hidden: ".ecryptfs".)?
d) Is it acceptable to leave swap with just 1.0GB, since I don't need to hibernate?
e) Anything else I need to consider?

---

### Post by Kixtosh on 2011-07-02
Aw dang! 

I thought this was probably going to be fairly simple, but guess I gave a bit TMI for everyone, and all of them fell asleep before reaching the end of my first post. Let me try to rephrase that more simply:

**1) Can I get an SD Card to install as my /Home partition,** using a built-in SD Card reader that cannot normally be used as a boot device?

**2) How would I set up an SD Card** (using a built-in SD Card reader) **as a seamless extension of an existing /Home on my hard drive?** Since the hard drive is bootable, I don't get any error messages when doing it this way, but the space left on the hard drive is very limited for a useful /Home.

Do I hear snoring this time ...? ... Hmmm ... nope! ... Don't think so ... Maybe there is still some hope for an easy way to do this.

---

### Post by oldfred on 2011-07-02
I like to keep a fully bootable system on a drive, including the hidden user files in /home. But I do not have (much) of my data in /home but in another partition sometimes on another drive (I boot 3 drives and have data linked into all my Ubuntu installs and a NTFS /shared linked into /home and XP.

I have not move .wine, yet, but I believe it is a bit more complicated to move than just linking. I have moved my Firefox & Thunderbird profiles that were . files into /shared so I can use them in everything and most of the rest of my info is in /data. System should then mount and only give errors if it cannot find /data or /shared.

sudo mkdir /mnt/data
sudo chown -R fred:fred /mnt/data
sudo chmod -R 766 /mnt/data
#Edit fstab with your UUID:
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /mnt/data    ext3         auto,users,rw,relatime               0  2 
#Verify entry is ok, if no errors it is:
sudo mount -a
#from home so default location of link is in /home/fred
mv Music oldMusic
# Music is a folder in the partition mounted as /mnt/data
ln -s /mnt/data/Music
#Or link all folders with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

Shared /data -see post #4 oldfred
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by moore.bryan on 2011-07-02
Yeah, I'd go with a link -s to folders/files on your SD card that you mount automatically at boot through /etc/fstab.

---

### Post by Kixtosh on 2011-07-02
Ah, yes! That looks nice! I don't understand most of it yet, but it looks nice!

What you are suggesting, if I follow you, is to create a /data folder on the SD Card, and then link everything from /home to there. The hard drive /home would then contain only links, so it would never get full. I could allocate a bit more space to swap and Ubuntu O.S. on the hard drive and keep my 8GB SD Card for all my /home stuff stored, via links, in /data.

I'll read those threads you mentioned, and try to figure out what the commands you used were, including what my UUID might be!

Would this part just link all /home folders to /data?
```
#Or link all folders with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done
```

---

### Post by moore.bryan on 2011-07-02
Personally, I've deleted almost all the folders in my /home and sym-linked new ones to those folders I keep on my always-attached external hd.

---

### Post by Kixtosh on 2011-07-02
Alrighty then! How does this look?

My SD Card is identified as /dev/mmcblk0p1. It's currently mounted at /media/627ba658-bla bla bla bla bla ...

I could just format it normally, as ext4, and modify this procedure from bodhi.zazen

```
sudo mkdir /mnt/data 
sudo mount /dev/[COLOR=DarkRed]mmcblk0p1[/COLOR] /mnt/data 
sudo chown root:users /mnt/data 
sudo chmod 770 /mnt/users
```Fstab (/etc/fstab):

```
/dev/[COLOR=DarkRed]mmcblk0p1[/COLOR] /mnt/data [COLOR=DarkRed]ext4[/COLOR] defaults 0 0
```Then, for my /home folder, assuming my login name is "kixtosh":

```
mkdir /mnt/data/[COLOR=DarkRed]kixtosh[/COLOR] ln -s /mnt/data/[COLOR=DarkRed]kixtosh[/COLOR] /home/[COLOR=DarkRed]kixtosh[/COLOR]/data
```Would that do it?! 

P.S. What does the chmod 770 mean?

---

### Post by oldfred on 2011-07-03
You may have to umount it from /media to be able to remount it.

I do not think you mkdir & link in one line as you have shown. I link to folders in the /data partition like Music, Documents, Video - all the one's normally in /home that I moved the actual data into the folders of the same name in the data partition. 

I also create my actual mounts in fstab as permanent mounts, but with you flash drive I am not sure what happens if it is not there when you boot. And then what happens to links. Mine work since it is fix drive that is there all the time.

The 777 or 766 or what ever are permissions for owner, user, other which set read, write or execute.

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Kixtosh on 2011-07-03
Thanks oldfred, I think I've made some progress, but I'm probably not quite all there yet. I've figured some stuff out in the meantime though. Here's where I've got to, a few error messages later!

I formatted the SD Card as ext4, and unmounted it.

I figured out permissions, from 0 to 7, **one digit** each for **user**, **group**, and **all**. So if the first digit is 7, then the user has all permissions to read, write and execute. If the last digit is 0, then all have no permissions. The middle digit is for the group. Something like that, I think, with varying permissions for everything in between those two extremes. 

So, in terminal, I tried the following:

```
sudo mkdir /mnt/data
```No problem. Success, I think.
```
sudo mount /dev/mmcblk0p1 /mnt/data
```Seems fine as well.
```
sudo chown root:users /mnt/data
```Worked fine too.
```
chmod 770 /mnt/users
```Oops, first bit of trouble:
```
chmod: cannot access `/mnt/users': No such file or directory
```So I took a peek at the /mnt directory, and found nothing in there but a folder with a X on it, called "data". So, consequently, tried the following (bold move, I know ... maybe stupid even):
```
sudo chmod 770 /mnt/data
```No error message, but then:
```
/dev/mmcblk0p1 /mnt/data ext4 defaults 0 0
```Which returned:
```
bash: /dev/mmcblk0p1: Permission denied
```I did figure out **the UUID thing**, using:
```
sudo blkid
```With this result:
```
/dev/sda1: LABEL="TOSHIBA SYSTEM VOLUME" UUID="F07A64F77A64BBCA" TYPE="ntfs" 
/dev/sda2: LABEL="SQ004490V02" UUID="8EDA6D8FDA6D747D" TYPE="ntfs" 
/dev/sda3: LABEL="HDDRECOVERY" UUID="BC90BDCD90BD8E80" TYPE="ntfs" 
/dev/sda5: UUID="1a061e2e-6e46-4f05-912d-2f60e64e0c17" TYPE="ext4" 
/dev/sda6: UUID="a4f36bf3-647d-43de-bb74-984aecea02d4" TYPE="swap" 
/dev/mmcblk0p1: LABEL="PortM-CM-)gM-CM-)_R500" UUID="50843ba5-7315-445e-b235-95d733d69719" TYPE="ext4"
```The label seems messed up, but that's because it includes funky characters for "Portégé", of course (a Toshiba brand name for some of their laptops).

I'm more or less stuck at that. If I boot up:

1) No error messages.
2) No SD Card icon on the desktop any more.
3) Disk Usage Analyser still shows "Home" as having 13GB or so of total space (so includes the SD Card in the total, I think).
4) Disk Utility (Administration menu) shows SD Card as present, and mounted at /mnt/data.
5) Home folder in Nautilus properties show only 3.3GB of available space, so not including SD Card, it seems.

How do you think I'm doing so far, and how should I proceed? I'm guessing I'm not quite where I want to be, even if I can still boot up, at least. Exciting stuff!

---

### Post by wcj786 on 2011-07-03
> **Kixtosh said:**
> No error message, but then:
```
/dev/mmcblk0p1 /mnt/data ext4 defaults 0 0
```Which returned:
```
bash: /dev/mmcblk0p1: Permission denied
```

This may be a dumb reply, but did you make sure you ran this as administrator?  The "PERMISSION DENIED" reply seems to indeicate that the system did not recognize you as an authorized person to edit that file.

---

### Post by Kixtosh on 2011-07-03
> **wcj786 said:**
> This may be a dumb reply, but did you make sure you ran this as administrator?  The "PERMISSION DENIED" reply seems to indeicate that the system did not recognize you as an authorized person to edit that file.You might be right. I was logged in normally (with my "username" profile) the whole time, and using "sudo" commands in Terminal, but it's probably not possible to modify a username's /home while that username is logged in. Then again, maybe it is, since we're just adding a link to /data on the SD Card - not resizing a mounted /home partition, for example.

Maybe some of these commands have to be run when logged into the root profile?

---

### Post by oldfred on 2011-07-03
Sorry, I copied those commands from my script that I run when I do a new install to semi-automate the process. You do need sudo for just about everything as my script is run as root.

For my data, I want to be the owner and have very permissive permissions, but it is a desktop where I do not have to worry about losing the memory card.

If you created a partition in your card, do you not want to mount that? Not the card. Some say you can use an entire drive that way but I have always formated my flash drives and mount sdd1 not sdd?

What does these show?

sudo fdisk -lu
sudo blkid

This is my mount:

```
fred@fred-MavericDT:/mnt/data$ ls -l
drwxrw-rw- 10 fred fred  4096 2011-07-01 14:14 Documents
drwxrwxrw-  5 fred fred 16384 2011-06-29 16:10 Downloads
drwxrwxrw-  7 fred fred  4096 2009-04-10 22:42 eclipsetrader
drwxrwxrw-  3 fred fred  4096 2010-12-13 13:23 gnu
drwxrwxrw-  9 fred fred  4096 2006-12-24 11:35 google-earth
drwxrwxrw-  4 fred fred  4096 2010-08-31 17:44 grampsdb
drwxrwxrw-  3 fred fred  4096 2011-06-29 14:30 ISO
drwxrwxrw- 18 fred fred  4096 2009-04-08 17:13 itrade
drwxrwxrw-  8 fred fred  4096 2010-10-06 12:43 jstock
drwxrw-rw-  2 fred fred  4096 2011-05-21 16:17 kmymoney
drwxrwxrw-  8 fred fred  4096 2011-04-02 11:14 Music
drwxrw-rw-  4 fred fred 12288 2011-05-26 22:33 PDF
drwxrwxrw-  5 fred fred  4096 2006-12-24 11:41 PicasaDocuments
drwxrwxrw- 12 fred fred  4096 2011-05-21 09:51 Pictures
drwxrw-rw- 31 fred fred  4096 2011-05-23 23:55 Projects
drwxrwxrw-  8 fred fred  4096 2010-06-21 14:19 Videos


```

---

### Post by Kixtosh on 2011-07-03
Well ... ahem ... I totally screwed something up.

I was trying to figure out the symlink thing, and the fstab, but whatever I did, I couldn't boot Ubuntu any more. Something to do with ICE Authority and Nautilus not being able to create /home. Anyway, since there's nothing on this laptop yet, I just wiped it off and I'll start over when it's finished installing again. I had encrypted the /home directory, but I'll just leave it unencrypted this time until I figure this sh*t out.

I know: it sounds as though I dropped an atomic bomb to get rid of a pesky dandelion on my lawn, but I don't always know how to undo something I did which created an issue, which is why I try this more ambitious stuff (for me, anyway) on a new system that can be just wiped with no gnashing of teeth. I'm not very good at using the recovery environment either (I've never actually succeeded in recovering anything that way yet).

Oh well, there goes my reputation! Any suggestions on what I should do first and/or different this time? 

Regarding:

```
sudo fdisk -lu
sudo blkid
```I'll post that information later, when I've made some progress again.

---

### Post by moore.bryan on 2011-07-04
I know I'm coming-back to this discussion a little late, but I'm wondering why you didn't go a simpler route:
[list=1]
[*]Make a folder in your /home to which to mount the sd card so you don't have to worry about permissions:
```
mkdir ~/Data
```
[*]Edit /etc/fstab to automatically mount your sd card at boot and add this line:
```
/dev/mmcblk0p1   /home/$USER/Data   ext4   defaults   0   0
```
[*]Mount your sd card
```
sudo mount -a
```
[*]Add the folders to your sd card you want to "mirror;" e.g., Documents, Pictures, etc.:
```
cd ~/Data
mkdir Documents
...
```
[*]Delete the original /home folders:
```
rm -r ~/Documents
...
```
[*]Make symlinks to the new folders you created in the Data folder
```
ln -s ~/Data/Documents ~/Documents
...
```
[/list]

Now, anything you save in ~/Documents will save on the sd card... oh, and make sure to replace the $USER in step 2 with your username. Also, the elipses in the steps means creating/linking other folders...

---

### Post by Kixtosh on 2011-07-04
> **moore.bryan said:**
> I know I'm coming-back to this discussion a little late, but I'm wondering why you didn't go a simpler route: ...Not at all late ... you're timing is perfect. The laptop is back in business, minty fresh and clean and ready for me to break it again!

I'll be ready to have another go at this a little later (when I'm less busy). I think some of what I might have done wrong was creating the /mnt/data folder initially in the wrong place, but I'm not sure exactly. As you suggest, it seems as though there should be a fairly simple answer to this. The main thing is getting the SD card to be used as /home, not the hard drive.

---

### Post by moore.bryan on 2011-07-04
> **Kixtosh said:**
> Not at all late ... you're timing is perfect. The laptop is back in business, minty fresh and clean and ready for me to break it again!
Excellent!

[QUOTE=Kixtosh]I think some of what I might have done wrong was creating the /mnt/data folder initially in the wrong place, but I'm not sure exactly.[/quote]
I don't think it's "in the wrong place," but placing the mount point in your /home may solve some of the more irritating permission issues.

[quote=Kixtosh]The main thing is getting the SD card to be used as /home, not the hard drive.[/QUOTE]
Now, I'm a little confused. Are you looking to have your *entire* /home be housed on your sd card or just the folders in it? With the method I outlined above, anything saved to the folders--usually, larger files--will be on the sd card, but your "." files--configs--will still reside on your /home partition. That's usually preferable because read/write to an sd card can be slow.

---

### Post by Derek Karpinski on 2011-07-04
I think you're going to run into problems with an encrypted /home.

If you do use an encrypted /home, you're going to have to get your symlinks out of fstab which runs at boot time, and into a start-up script.  Because your /home directory at boot is an encrypted folder, and your 'home' doesn't really exist at this point.  When you log in, then your encrypted files are mounted on /home (through some kind of magic I assume) and it looks seamless.

Just my take on it.  I bet what you're trying to do will work easier without an encrypted home.

---

### Post by Kixtosh on 2011-07-04
> **moore.bryan said:**
> ... Now, I'm a little confused. Are you looking to have your *entire* /home be housed on your sd card or just the folders in it? With the method I outlined above, anything saved to the folders--usually, larger files--will be on the sd card, but your "." files--configs--will still reside on your /home partition. That's usually preferable because read/write to an sd card can be slow.Well, I was (sort of) but it's not crucial. If I get the "main" folders, such as "documents", "downloads" and "pictures" on the SD Card, that should keep me happy, and I think I rather just keep it simple for now in any case, at least until I get the ball rolling, as it were.

Actually, though, this SD card tests with the Ubuntu Disk Utility at an average read time of almost 17MB/s, and an access time of 1.2ms. That compares to the 4,200 rpm 1.8" HDD in my older Portégé (R205) at just 1MB/s faster, and 19.9ms access time! These results were what convinced me to try this "experiment" in the first place. The Portégé R205 might not be a speed demon, but it's still a wonderful, super slim, super lightweight and dependable travel machine without Windows (just too slow, and too vulnerable with public networks). Boot time, for example, is about 50-55 seconds, including BIOS boot time. The newer (and even lighter) Portégé R500, the subject of our "experiment", boots Ubuntu in 22-23 seconds, including about 5 seconds of BIOS stuff. Traveling with this is going to be close to perfection and it's why I'm willing to devote so much effort into trying to make it work.

> **Derek Karpinski said:**
> I think you're going to run into problems with an encrypted /home.
... Just my take on it.  I bet what you're trying to do will work easier without an encrypted home.That makes just loads of sense to me, and I bet it's what caused me to run into problems before, that eventually drove me to use the nuclear option to get things back up and running.

---

### Post by Kixtosh on 2011-07-04
Ahem ... errr ... guys ... **[COLOR=DarkRed]this[/COLOR]** is rather embarassing (see EDIT 2 below):

Well, it hasn't taken me long to get stuck! When I try
```
sudo mount -a
```I get a message:
```
mount point /home/**[COLOR=DarkRed]$[/COLOR]**kixtosh/Data does not exist
```Just when I was starting to feel clever about all this, I get bumped all the way down to stupid again!

EDIT: I tried to mount the SD card using the Disk Utility from the Administration menu, and got this error message:
```
Error mounting: mount exited with exit code 1:
helper failed with:
mount: only root can mount /dev/mmcblk0p1 on /home/$kixtosh/Data
```Furthermore: when I restart, I get a message that halts booting:
```
An error occurred while mounting /home/$kixtosh/Data
Press S to skip mounting or M for manual recovery
```

EDIT 2: I just removed that $ and I'm back in business. More later.

---

### Post by Kixtosh on 2011-07-04
Output of **sudo fdisk -lu**
```
Disk /dev/sda: 64.2 GB, 64156073984 bytes
255 heads, 63 sectors/track, 7799 cylinders, total 125304832 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3a44ac04

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     3074048    97806327    47366140    7  HPFS/NTFS
/dev/sda3       112654336   125304831     6325248   17  Hidden HPFS/NTFS
/dev/sda4        97819783   112647779     7413998+   5  Extended
/dev/sda5        97819785   108551204     5365710   83  Linux
/dev/sda6       108551268   112647779     2048256   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/mmcblk0: 7960 MB, 7960264704 bytes
4 heads, 16 sectors/track, 242928 cylinders, total 15547392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00056d5a

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1              16    15547391     7773688   83  Linux

```Output of **sudo blkid**
```
/dev/sda1: LABEL="TOSHIBA SYSTEM VOLUME" UUID="F07A64F77A64BBCA" TYPE="ntfs" 
/dev/sda2: LABEL="SQ004490V02" UUID="8EDA6D8FDA6D747D" TYPE="ntfs" 
/dev/sda3: LABEL="HDDRECOVERY" UUID="BC90BDCD90BD8E80" TYPE="ntfs" 
/dev/sda5: LABEL="Ubuntu" UUID="7a071688-afeb-4da6-a15e-a5515097398e" TYPE="ext4" 
/dev/sda6: LABEL="Swap" UUID="1f445ab9-44c4-4dc6-a38a-84b50f59b295" TYPE="swap" 
/dev/mmcblk0p1: LABEL="Home Data" UUID="1282eaa5-d2ff-4b1d-8bce-0e005a67f1b4" TYPE="ext4" 
```

---

### Post by Kixtosh on 2011-07-04
Got to > **moore.bryan said:**
> 
6. Make symlinks to the new folders you created in the Data folder
 ```
ln -s ~/Data/Documents ~/Documents
...
``` Now, anything you save in ~/Documents will save on the sd card... oh, and make sure to replace the $USER in step 2 with your username. Also, the elipses in the steps means creating/linking other folders...

In the meantime, I unfortunately tried solving this by changing permissions. How do I get those back to default, or do I have to nuke myself again to avoid leaving clutter on my system?! These are the two lines I used in Terminal:
```
sudo chown -R kixtosh:kixtosh /home/kixtosh.data
sudo chmod -R 770 /home/kixtosh/Data
```C'mon now guys, stop laughing already. It's not nice!

---

### Post by oldfred on 2011-07-04
sudo chown -R kixtosh:kixtosh /home/[COLOR=Red]kixtosh.data[/COLOR]
sudo chmod -R 770 /home/kixtosh/Data

Change your . to / and it looks like it should work. 

Is kixtosh your login?
```

echo $USER
```All your issues are why I converted mine to script as I had similar issues at first. And redoing I learned to make fewer errors but still some. By doing a script then every 6 months with a new install I did not have to remember all the details. if you type this you can see what you have done and copy the commands that worked to a script:
```

history
```If you change to your data directory what permissions does it show?

```
fred@fred-MavericDT:~$ cd /mnt/data
fred@fred-MavericDT:/mnt/data$ ls -l
total 92
drwxrw-rw- 10 fred fred  4096 2011-07-01 14:14 Documents
drwxrwxrw-  5 fred fred 16384 2011-07-04 14:55 Downloads
drwxrwxrw-  7 fred fred  4096 2009-04-10 22:42 eclipsetrader
drwxrwxrw-  3 fred fred  4096 2010-12-13 13:23 gnu

```

---

### Post by Kixtosh on 2011-07-05
> **oldfred said:**
> sudo chown -R kixtosh:kixtosh /home/[COLOR=Red]kixtosh.data[/COLOR]
sudo chmod -R 770 /home/kixtosh/Data

Change your . to / and it looks like it should work.  ...Sorry, that was a typo, so I had typed "/Data" where it should have been ... sorry! I was typing from the "other" Portégé, so I couldn't copy & paste. The question was whether I should leave that as it was, or should I set it back to "default", whatever that may be, and if so: how I should do it. The "history" command is great at showing up all the silly things I do and/or did, but I don't actually know how to undo most of them once I know that I did them in the first place. Sigh!

Kixtosh is the login, as you guessed.

> ...If you change to your data directory what permissions does it show? ...```
kixtosh@R500-laptop:~/Data$ ls -l
total 20
drwxr-xr-x 2 kixtosh  kixtosh   4096 2011-07-04 18:46 Documents
drwx------ 2 root root 16384 2011-07-04 17:49 lost+found

```

---

### Post by oldfred on 2011-07-05
It looks ok. I think your permission are 755. The default for /home is 644, but I tend to more permissive since my system is a desktop at home.

I just learned something - see post #8 by morbius1. Seems like a better way as you have more control over what is executable.

[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)

---

### Post by Kixtosh on 2011-07-05
I'm having another little issue that it would be nice to fix (especially on a laptop). It seems that the SD Card is not mounting when waking up from standby, for some reason, and everything freezes (including networking). Is there a way to make sure the SD Card is mounting after standby? Otherwise, I have to force quit by holding down the power button for five seconds, and start up again. If I can't fix this, I'll have to completely disable standby to make the laptop usable.

---

### Post by oldfred on 2011-07-05
I do not know the solution to your problem but do not force quit which can cause other problems. Get the system to shutdown normally.

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown

A good way to remember it is.
OR RSEIUB _ order of eis does not seem important.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by Kixtosh on 2011-07-05
Ah yes! I knew of the "Raising Elephants Is So Utterly Boring", but when the Toshiba freezes up, that doesn't seem to do anything.

Well, in the meantime, I read the Portégé R705 thread (it's a much newer model, and much faster CPU & HDD, but mine is lighter, was cheaper to buy, and does have the advantages of an SSD, motion detector working or not). It seems this SD Card and standby thing can be an issue on that model as well, but it was resolved for the R705 (according to information in that thread) with "**Fixed in 2.6.35**". I'm guessing that refers to a Maverick Meerkat kernel maybe? Just about everything else worked on my R500 out of the box, so maybe it might be worth a shot for my situation to try a newer release? I usually stick to LTS. I had been hoping there was a way to "force" Ubuntu to "wake up" the SD Card on resume from standby. Maybe that's not possible.

[http://ubuntuforums.org/showpost.php?p=9704287&postcount=1](http://ubuntuforums.org/showpost.php?p=9704287&postcount=1)

Another option would be a CF adapter in the PCMCIA slot, and use a Compact Flash card instead. I think those can be cheaper and faster than SD cards as well. I don't need lightning fast speeds to get equal performance to the Portégé R205 with a regular 4,200 rpm HDD. For browsing while traveling, checking e-mails and the occasional OpenOffice document, that's more than acceptable when compared to any Windows solution I've tried ... in terms of speed or security, especially if I get to keep my 22 second boot and 3 second shut down.

---

