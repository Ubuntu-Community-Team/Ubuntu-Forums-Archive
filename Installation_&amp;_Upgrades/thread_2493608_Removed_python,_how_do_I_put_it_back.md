---
title: "Removed python, how do I put it back?"
date: 2023-12-19
forum: Installation &amp; Upgrades
---

### Post by goemonburo on 2023-12-19
I did a dumb thing, which was removing python2 and 3 from my Lubuntu 20.04LTS distro.  (After running a snap and "integrating it" icons on my system vanished, I followed a thread down the rabbit hole and it seemed like a good idea at the time.  Only it wasn't.)  

I did "sudo apt remove python3" and then the same for python2.  Dunce hat move, I know.

Now, it won't even boot...just hangs at the launch screen with the five little blue dots loading.  I tried accessing it via SSH to see if I could use a terminal, but no, it's totally bricked, apparently.

I'm running on a Live USB, but would love to know how I can restore this back to its normalness of a few days ago...if possible.  Is there a way to -- using a Live USB -- somehow run apt install?  Or, perhaps through dpkg?   

Thank you for any and all help or suggestions.  Alternately, if I can upgrade to 22.04LTS without risking losing my /home directory, I could do that too, but I'd rather just try to get the old system booting again.

---

### Post by ian-weisser on 2023-12-19
It's possible. I've done it.

For most users, it's much, much easier to use the Live environment to back up their data and then reinstall.

First, you need to know exactly which packages you removed. Exact versions help, too.
Second, you need to know how to chroot your broken system from the Live environment. If you are unfamiliar with chrooting, look it up.
Third, you need to understand how deb dependencies work, and how to use dpkg.

Those are all fairly easy. The critical skill that determines success or failure is reading and understand dpkg output in order to make the right choices.
Folks who don't read the output (or don't understand it) are almost certain to fail.
Your problem is that you *already* ignored that output at least once and made the wrong choice -- that's how you got into the current mess. 

The basic theory is that you download the python3, python3.x, python3-minimal, and python3.x-minimal packages from packages.ubuntu.com.
Make sure you download the correct versions.
Use dpkg (not apt) to install them. If you get a dependency error, then download and install that dependency.
After those four packages...and their dependencies...are successfully installed, apt should work again. Use apt to restore any other packages that you removed.

If you need more instruction than that, then you're not ready to do the repair. Go the backup-and-reinstall route instead.

---

### Post by MAFoElffen on 2023-12-19
If that is all you did, then first try
```

sudo apt install --reinstall -y python3

```
If that fails, then try
```

wget -N -t 5 -T 10 http://mirrors.kernel.org/ubuntu/pool/main/p/python3-defaults/python3_3.8.2-0ubuntu2_amd64.deb
sudo dpkg -i ./python3_3.8.2-0ubuntu2_amd64.deb

```
If that fails, then chroot into your installed system from a Focal Installer LiveUSB, then reinstall it using the first method above...

---

### Post by goemonburo on 2023-12-19
Thank you @MAFoElffen, can you quickly verify that what you're suggesting works when I'm running off a Live CD?  If I apt install something, won't that be into the Live CD environment?  Do I need to chroot first, then try what you suggest?

(Asking only because this looks vastly easier and I think all I did was remove python3 and python2, so hopefully I could just reinstall those as written instead of having to know the detailed info from the remove command.)

Thank you and @ian-weisser for the suggestions!  Really appreciate it.

---

### Post by ajgreeny on 2023-12-19
When you chroot into your installed OS the commands you run will act on that installed system, not the live system so any changes will be to that installed system.

---

### Post by MAFoElffen on 2023-12-19
Can you boot into the installed system still... If so, then try to do the first two from that.

If not, then do it from a LiveUSB. If from a LiveUSB, then yes, you would have to do everything "AFTER" chrooting into the installed system.

If you need help chrooting into your installed system, I would need to know some information from that system. If you use the UbuntuForums 'system-info' script in my signature line from a LiveUSB, then posted the URL of where the report uploads to a pastebin, then I could lead you through that on your system.

Most everything on Linux (Not just Ubuntu) depends very heavily from Python. This is something that needs to be restored. It can be done, without having to reinstall, as long as you don't make things worse. LOL.

---

### Post by ajgreeny on 2023-12-19
If I remember correctly an active python is required for apt to work so having removed it from your system the chroot method mentioned may be your only way to deal with the problem other than reinstalling.

---

### Post by MAFoElffen on 2023-12-19
I thought so to... But it actually worked for someone a few weeks ago... where it was removed but not purged. That surprised the heck out of me! 

Besides doing the second method (download and use dpkg) is outside of the apt system and will not hurt it any more than it already is. LOL

Worth a quick try before talking him through chroot'ing into his system.

---

### Post by guiverc on 2023-12-19
I would expect a system to boot normally even after removing python3/2; though you may find the GUI is not very usable (*if you can even achieve login**; it appears you cannot*), but text terminal should still operate.

I wouldn't expect `apt` to work, but if it doesn't, `dpkg` install (as suggested by MAFoElffen) will allow fixing the issue, with `python3-minimal` being all you should need installed before *normal operation* is returned.

You likely know, but Lubuntu 20.04 LTS is EOL - [https://lubuntu.me/lubuntu-20-04-lts-end-of-life-and-current-support-statuses/](https://lubuntu.me/lubuntu-20-04-lts-end-of-life-and-current-support-statuses/)

---

### Post by MAFoElffen on 2023-12-19
Dang. I keep forgetting that even though LTS, that flavors are only 3 years of support instead of 5 years like Ubuntu LTS.

---

### Post by goemonburo on 2023-12-20
Thank you all so much for the suggestions and info.  Yes, I do know that 20.04LTS is EOL, which is why I'm leaning heavily on just installing 22.04LTS, but those always come with a whole agony of different tweakings to settings, figuring out which new programs replace the ones that now no longer run, and so on.

Another question, though, since I'm trying to see whether I purged or just "removed" my pythons...and realized I have access to my user home directory but not the .bash_history file that's for sudo.  Is there a way to find that?  I thought I'd just cd into the root directory but it looks like I've been mounted into my user home only, without any root.  Is the .bash_history for "sudo apt-get remove python2" hiding somewhere that I don't realize?

Also, is there a good step-by-step out there for using chroot to accomplish this?  I've seen a number of things that seem to be using chroot to do the opposite: sandbox commands within a virtual environment so they're not affecting the system.

Lastly, will anything that was removed in the python mess be retained if I rsync my /home directory and rsync it back after I upgrade to 22.04LTS?  Like, I'm thinking things like VirtualBox, which I remember seeing vanish in the purge, among other things.  Am I going to be stuck with an unusable system AFTER upgrading if I use an archive of the existing drive?  (I'm asking because in a stroke of sheer luck, I have a backup that was made just a few days beforehand, so it would be pre-purge/remove, and I could use that...I may have a few files that get lost but nothing vital.)

Thank you again for all the help!

---

### Post by MAFoElffen on 2023-12-20
It's name is ".bash_history" and is located at the root of your User Home Folder...
```

mafoelffen@Mikes-ThinkPad-T520:~$ ls -l $HOME/.bash_history
-rw------- 1 mafoelffen mafoelffen 68876 Dec 20 10:44 /home/mafoelffen/.bash_history

```
Still waiting for information from you, such as the URL of your system-info report, so I can talk you through chrooting into this to fix this, or any feedback on whether you tried anything yet...

This can be fixed.

---

### Post by goemonburo on 2023-12-20
Hi again, yes, I can get the /home/user/.bash_history, but I can't see the /home/root/.bash_history if there is one.  Or is the "sudo" .bash_history file identical?  If so, when I do "cat .bash_history | grep python" nothing shows up.  I feel like it's because I need to be in the root, not the user directory.

And sorry to miss the request for that URL, I'll try to get that for you.  THANK YOU!

---

### Post by MAFoElffen on 2023-12-20
There is nothing such as /home/root. Root's user folder is /root, and there is for that at "/root/.bash_history". 

What "exactly" do you "think you need"? 

This could have been fix yesterday... Been bouncing between things, trying to get something else taken care of. Sorry, I guess I don't understand the holdup.

If you are searching for what you removed, that's the wrong place to look to see what else might have been removed... That would be in /var/log/apt/history.log

EDIT: Tell you want... Please post the results of this, posted within CODE Tags
```

lsblk -e7 -o name,label,size,fstype,type,mountpoint,model

```

---

### Post by Irihapeti on 2023-12-20
Should "lable" be "label" in the code line?

---

### Post by MAFoElffen on 2023-12-20
@irihapeti -- Yes, corrected, thank you for the other set of eyes!

---

### Post by guiverc on 2023-12-20
> **goemonburo said:**
> Thank you all so much for the suggestions and info.  Yes, I do know that 20.04LTS is EOL, which is why I'm leaning heavily on just installing 22.04LTS, but those always come with a whole agony of different tweakings to settings, figuring out which new programs replace the ones that now no longer run, and so on.


You can non-destructively re-install a Ubuntu system, which is actually even easier with the *flavors* like Lubuntu.

Lubuntu actually QA-test for it; with the [Understanding our Testing Checklist document here]("https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743") , with this install case allowing you to re-install a different release, which can achieve an *release-upgrade* in a fraction of the time of `do-release-upgrade` etc.


I last did it last night, so maybe 15 hours ago now, where I re-installed the Lubuntu 22.04.4 *daily* ISO as a QA test on an existing system of mine, which accomplished two things, it upgraded my packages (*I don't upgrade that box normally, but re-install it regularly using dailies to achieve the same thing*) plus did the QA test of that *unreleased* ISO. In the *testcase checklist* that install is "*Install using existing partition*"  where I re-install using the same partition without format, and my  prior used apps get auto-reinstalled as part of that upgrade, eg. after  install & reboot, and I've logged in, I start my `clementine` music  app & have it continue playing my playlist, as I perform the checks  of that system. As `clementine` is not included by default on a Lubuntu  install I confirm that app got re-installed, the fact that my music plays  confirms my files still exist etc.. I don't expect to really notice any  difference from my prior setup due to this install, except the system  won't report a week+ of upgrades are waiting to be installed (*which it did prior to re-install*)..  I thus  have to jump to terminal, check file-system meta data to confirm the  re-install did occur, that `/var/log/installer/media-info` contains the  ISO date I actually just QA-tested.. given in using the system via GUI  I can't  detect it was re-installed.

Of note:  My QA  re-installs do not include 3rd party applications generally; as we QA  only with Ubuntu repository software, and whilst it will work with some  3rd party, it may not work with all.  Regardless I use this on occasion to fix my own messes; in fact used it *long* ago to fix a uninstall of default python myself (*we all learn sometime; repeating the mistakes is what we shouldn't do*).

As for changing release, the box I performed the test on also contains *lunar* (23.04) & *mantic* (23.10) installs; the *lunar* will switch to be a *noble* or 24.04 install box rather soon, where I'll use this *non-destructive* re-install to have it switch releases.

---

### Post by TheFu on 2023-12-20
> it seemed like a good idea at the time. Only it wasn't.) 

We've all been there!  Sorry, I have nothing useful to add, but that I've done some bonehead things too, but never removed the system python.  I did specifically wipe a partition table and the backup, however.  I had a boot-sector virus and figured doing that was the easy solution.  Bonehead enough?  BTW, it did handle the virus nicely ...

---

### Post by goemonburo on 2023-12-21
Haha, @TheFu, thanks for the moral support.  I'm grateful to everyone for chipping in and helping...and yes, it could have been fixed, only I have a deadline for work I have to get done and once that's complete, I'll put in the hour or two needed to restore the system.  In the meantime, I'd love to know @guiverc about the non-destructive reinstall.  That sounds like perhaps the best option.  If 22.04LTS can be non-destructively installed over 20.04LTS, then that's what I'll do.  I don't have it in a Live USB, unfortunately, so I'll have to make that first.  But will it be an option I can choose out of the Live USB installer?  Or do I have to prep or have separated my /home dir or something?

I will post the output, @MAFoElffen, in just a bit.  Thank you (all) for your suggestions and time!

---

### Post by goemonburo on 2023-12-21
Here is the output:

```
lsblk -e7 -o name,label,size,fstype,type,mountpoint,model
NAME   LABEL                       SIZE FSTYPE TYPE MOUNTPOINT         MODEL
sda                              931.5G        disk                    TOSHIB
&#9500;&#9472;sda1 ESP                         650M vfat   part                    
&#9500;&#9472;sda2                             128M        part                    
&#9500;&#9472;sda3 OS                        195.3G ntfs   part /media/lubuntu/OS  
&#9500;&#9472;sda4 WINRETOOLS                  990M ntfs   part                    
&#9500;&#9472;sda5 Image                      13.9G ntfs   part                    
&#9500;&#9472;sda6 DELLSUPPORT                 1.4G ntfs   part                    
&#9492;&#9472;sda7                           719.2G ext4   part /media/lubuntu/0ff 
sdb                                3.7T        disk                    WDC_WD
&#9492;&#9472;sdb1                             3.7T ext4   part /media/lubuntu/889 
sde                               14.6T        disk                    M001G-
&#9492;&#9472;sde1 16TB                       14.6T ext4   part /media/lubuntu/16T 
sdf                               16.4T        disk                    M000J-
&#9492;&#9472;sdf1 18TB                       16.4T ext4   part /media/lubuntu/18T 
sdg    Lubuntu 20.04.3 LTS amd64   3.8G iso966 disk                    USB_Fl
&#9500;&#9472;sdg1 Lubuntu 20.04.3 LTS amd64   1.7G iso966 part /media/lubuntu/Lub 
&#9500;&#9472;sdg2                             3.9M vfat   part                    
&#9492;&#9472;sdg3 writable                      2G ext4   part /media/lubuntu/wri 
sdh                                1.9G        disk                    U3_Tit
&#9492;&#9472;sdh1 2GB_SANDISK                 1.9G vfat   part /media/lubuntu/2GB 
sr0    Lubuntu 22.04.3 LTS amd64   2.7G iso966 rom  /media/lubuntu/Lub HL-DT-
zram0                              2.4G        disk [SWAP]             
zram1                              2.4G        disk [SWAP]             
zram2                              2.4G        disk [SWAP]             
zram3                              2.4G        disk [SWAP]             
zram4                              2.4G        disk [SWAP]             
zram5                              2.4G        disk [SWAP]             
zram6                              2.4G        disk [SWAP]             
zram7                              2.4G        disk [SWAP]
```

---

### Post by goemonburo on 2023-12-21
I believe it's sdb that's got my system on it.  I should have unplugged the extraneous.  I have my Live USB system 20.04LTS running and have prepped a 22.04LTS dvd-r with the current (22.04.3LTS) system for that.  The 16 and 18 TB drives will just be unplugged before anything is upgraded.  I think sda is where my ancient and never used Dell OS still resides.  

Does anyone know if I'm able to make a Live USB from the Live CD these days?  I seem to recall having a heck of a time getting it to work when I did 20.04 initially.  May have even made the bootable USB in Windows first.  Can't recall.

In any case, my plan this evening is to reboot the system into 22.04LTS live, and then try a manual update as suggested by @guiverc.  If the above output helps anyone see things I might need to know beforehand, thank you as always for the help!

---

### Post by MAFoElffen on 2023-12-21
In that case, from a Live Session, do whatever you have to do to get networking working... Meaning if it uses a WiFi network, connect to your home WiFi. Open Firefox to get back to this past, then open a terminal session where you can cut-and-paste the commands into.

You do not have LVM, LUKS or anything else special, so is fairly straight forward... 
```

sudo su -
mount /dev/sdb1 /mnt
ls /mnt

```
You should see the OS root folder structure there. If not, find which partition is the OS root, and mount it instead... If it is so, then 
```

mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run  /mnt/run
cd /mnt
chroot /mnt /usr/bin/env bash --login
mount -a
apt update
apt install --reinstall -y python3
exit
umount /mnt
reboot

```
Test. 

Do a good backup, then upgrade the release to something supported.

Good luck and enjoy.

---

### Post by goemonburo on 2023-12-21
So, I've successfully mounted sdb1 to /mnt, but I'm not seeing what I expect from a Linux / directory, the /var, /home, /sbin, and so on directories.  All I'm seeing are three directories, one of them my home directory.  Call them "dirA," "dirB," and "MyHome."  

Would mounting /mnt onto sdb (without the 1) be what you mean by finding the root?

AH, hold on, I think I see it:  Maybe it's sda7?  I see a 719.2GB ext4 partition on sda...Going to try that.  I may have kept the /home drive on a separate partition for this exact reason, in case things got corrupted.  

Checking that...

---

### Post by MAFoElffen on 2023-12-21
No... Not directly to a drive only. 

Explanation. When you mount something, it's not to a disk (that is a Windows kind of misconception). You actually mount to the filesystem 'within' a container. So withi a partition, LVM LV or ZFS dataset...

To unmount that, please do (still as root)
```

umount /mnt

```
We know most of /dev/sda is Windows (except for /dev/sda7), and /dev/sdg is your Lubuntu LiveUSB...

So your other choices would be /dev/sda7, /dev/sde1, and /dev/sdf1... do the same to mount them, one by one, check them to ensure your are on the correct filesystem.

---

### Post by goemonburo on 2023-12-22
Well, thank you all for the help thus far, I've tried a few things...successfully chrooted into the old system as per the instructions, but got a "cannot unmout" error and when I finally exited (just turned things off, hoping the --restore worked...nope, same thing was happening.)

I then decided to install 22.04.3LTS in place of the old 20.04LTS partition.  That had some quirks (installer failed once, tried again, got partway through, failed...not sure why).

But third time's a charm and I'm writing from a freshly installed 22.04.3LTS NON live system.  It's in there.  Yay.

But I am now running into a problem in that I can't seem to get my /etc/fstab line to point properly to the old home directory.  Copying syntax from another recent post I tried using the UUID, but that mounts the drive one step higher in the path than I want...is there a way to use the /etc/fstab line to point further down the directory tree? 

For example, I have:

```
UUID=888xxx444bbblahblahblah  /home/myhome ext4 defaults 0 2
```

And what I WANT is:

```
UUID=888xxx444bbblahblahblah/myhome  /home/myhome ext4 defaults 0 2
```

I'm loathe to just guess if this is doable.  Should I be using the non-UUID descriptor?  /dev/sdb1/myhome?  

Thank you.  I'm nearly there!!

---

### Post by MAFoElffen on 2023-12-22
So your home is a Folder that resides within a partition?

What you do for something like that is to mount the the folder "somewhere" where it doesn't matter, such as to a Folder called /exports... Then replace /home/myhome with a symlink.

Not pretty, but it works.

What would be better for the future, is to just move that user home folder to it's ow partition, where you can just mount the filesystem of it like normal... That would straighten that out, for growth and portability down the road. It looks like you have plenty of storage there to do that.

---

### Post by goemonburo on 2023-12-22
Thank you for the info, as always.  How would I "move the user home folder to its own partition," seeing as this is probably as good a time as any to do that?  Is it something I'd do with gparted?  And would I maybe rsync the current /dev/sdb1/myhome to another location, then wipe and repartition that whole /dev/sdb, and then restore the folder back into the new partition, sans any folders above it?

Thank you.  I know we're now into a sort of different topic than the original post, but I appreciate the walkthrough just the same!

---

### Post by MAFoElffen on 2023-12-22
Wait... Let me rephrase that... I think I was confused. Doing several things at once.

Are you talking about /dev/sb1? if the root of /dev/sda1 has your /myfolder in it then do this

Make sure in your new install you do this
```

sudo su -
mv /home /home-old
mkdir /home
echo "/dev/disk/by-uuid/$(blkid -s UUID -o value /dev/sdb1) /home ext4 defaults 0 0" >> /etc/fstab
mount /home

```
That will mount that partition as home, and the folder within it will showup in the correct place within it.

---

### Post by goemonburo on 2023-12-22
No, the 22.04LTS install is in /dev/sda7  (sda)

But the home directory is in /dev/sdb1  (sdb)

But the home directory isn't in the root of /dev/sdb1, it's in a subdirectory (folder?).  I'm not sure this is the right syntax, but it's /dev/sdb1/myhome

There's also a /dev/sdb1/downloads and a /dev/sdb1/oldstuff location.

So instead of mounting /dev/sdb1 as my /home, I need to mount /dev/sdb1/myhome.

Does that make any sense?  I know it's confusing...even for me and I'm the one looking at the computer.

(But it's there earlier in this thread, in the output I posted.  You can see /sda7 and /sdb1 are separate.

---

### Post by MAFoElffen on 2023-12-22
Yes... I understood which that it was in /dev/sb1. And yes, It makes sense... There are other folders there in that partition

So the there there if you mounted that partition to a folder called /exports would look like
```

/exports
 |_ MyFolder
 |_ Downloads
 |_ Oldstuff

```
That changes the above directions back to
```

sudo su -
mv /home/MyHome /home/MyHome-old
mkdir /export
echo "/dev/disk/by-uuid/$(blkid -s UUID -o value /dev/sdb1) /exports ext4 defaults,uid=1000,gid=1000,fmask=0002,dmask=0002,rw  0 0" >> /etc/fstab
mount /exports
chown -R /export MyUser
ln -s /exports /home/MyUser

```
Like I started to explain above, but then... Back to that.

Understand that now?

---

### Post by goemonburo on 2023-12-23
Thank you again, as always.

I think I have that last post understood, moving the existing install's /home to a different place, then adding the original to fstab, then using a symbolic link to point from that to the /home/user folder.  Makes sense.

It was your suggestion that at some point I may want to move the directory entirely that had me curious.  Could it be simpler if I simply rsynced the entire /exports/myhome folder up one, so that all the content for /exports/myhome now was in the /exports location?  Then edited fstab to mount UUID (/dev/sdb1) to /home/user?

Am I explaining that well?

I think before this I didn't understand that fstab was only for mounting partitions, not going more down the file system to subfolders.  If it only mounts partitions, then I could just move my /home/user to reside at the top level of the /dev/sdb1 partition.  Right?

(Again, thank you for your patience.  You've been super helpful!)

---

### Post by MAFoElffen on 2023-12-23
I think we understand that as the same.

That if you rsynsed, the folder of /MyUser to it's own partition, say for example /dev/sbb2... That didn't include other types of folders (Besides home user home folders)... Then that partition could be mounted as /home (mounpoint /home)... Which then would contain just the folder MyUser... (/home/MyUser)

That would be less complex, and make that much simpler for any pother upgrades or migrations in the future.

---

### Post by oldfred on 2023-12-23
Detailed commands to move /home to its own partition. But not changing paths in same partition.
To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[Move Home]([https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)) & 

But always best to have good backup of /home, list of installed apps and any server type apps like database or web. User settings are in /home but hidden ( . ) files. 

I have multiple installs and want data, but not necessarily setting in /home in all my installs. So I move data folders like Documents, Downloads, Pictures etc into a data partition and mount that, and link folders into /home so /home looks like normal structure, but data is really in another partition.

---

### Post by goemonburo on 2023-12-23
Thank you again.  @oldfred, I appreciate the answer but the grammar is a bit hard to follow.  Are you saying that it's better for me to just use symlinks as described above?  Or that I should indeed (using rsync, I would assume with -a?) migrate the /dev/sdb1/myhome to /dev/sdb1 ?

I don't really mind linking as @MAFoElffen suggests.  But I do have a solid /home backup and could move it to the root of the partition if that's optimal.  I don't have multiple installs, but I did find years back that having my /home on a separate partition made it simpler to upgrade without risking data loss.

Thank you (all!) again.  I think at this point my only question is whether there's a good reason to migrate the data up to the root of the partition, or just leave it where it is and symlink.  If they're basically the same, it seems linking is going to be simplest.  Am I right?

---

### Post by MAFoElffen on 2023-12-23
Translation... He has one partition for his Home, which he shares with multiple installations. He mounts that somewhat as I described, and symlink's it/them to those installations user home folders... Same concepts.

When  rsync over data to places, I have both mounted to the system, then use something similar to
```

rsync -aAXv /path/to/source/ /path/to/target

```

---

