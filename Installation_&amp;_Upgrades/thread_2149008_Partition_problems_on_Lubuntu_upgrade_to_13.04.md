---
title: "Partition problems on Lubuntu upgrade to 13.04"
date: 2013-05-27
forum: Installation &amp; Upgrades
---

### Post by ixusubunt on 2013-05-27
I was perfectly happy with my Lubuntu 12.10 so I don't know why I hit the ugrade button ... now I have so many problems I don't know where to start!
First of all the upgrade created so many error messages that my laptop crashed, so I hard to shut it down mid-upgrade and had no system at all. I therefore downloaded the ISO file on another PC and installed it from disc which seemed to work OK ... but I just pressed ok at the partition page, believing the default setting to be ok. (Probably a big mistake!)

Now I have a very small working area on my 80 Gb hard drive ... about 10 Gb, whilst all my files are on a 68 Gb section of the drive that I have to mount (and put in my password) to access. How can I change this?

I also have two of everything! For example my documents are here: /home/paul/Documents (in the 10 Gb section) and also here: /media/paul/e8c26d26-6f64-47c8-83b3-d5d59c17c874/home/paul/Documents (in the 68Gb section). Before I make things worse by deleting stuff and moving files around I thought I would get some advice!

Anyone have simmilar problems?

Paul

---

### Post by ajgreeny on 2013-05-27
> **ixusubunt said:**
> I therefore downloaded the ISO file on another PC and installed it from disc which seemed to work OK ... but I just pressed ok at the partition page, believing the default setting to be ok. (Probably a big mistake!)

Now I have a very small working area on my 80 Gb hard drive ... about 10 Gb, whilst all my files are on a 68 Gb section of the drive that I have to mount (and put in my password) to access. How can I change this?

I also have two of everything! For example my documents are here: /home/paul/Documents (in the 10 Gb section) and also here: /media/paul/e8c26d26-6f64-47c8-83b3-d5d59c17c874/home/paul/Documents (in the 68Gb section). Before I make things worse by deleting stuff and moving files around I thought I would get some advice!

You may have two **Documents** folders, but I imagine only the old one has any of your files in it!  You are probably right about it being a big mistake to just press OK at partitioning stage, but before we give any more advice can you mount the 68GB large partition and see if all your files are there, then check what is in the new 10GB partition; I suspect just empty folders in that, but we'll see.

Let's also see the output of ```
sudo fdisk -l
``` in terminal which will tell us exactly what partitions you already have and should give some clues about what is what.

---

### Post by ixusubunt on 2013-05-27
Yes you are correct, the new partition has empty folders (apart from things I have put there very recently) and all my stuff is in the large partition. The ouput from

sudo fdisk -l is

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00083e70

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   132153442    66075697+  83  Linux
/dev/sda2       132155390   156301311    12072961    5  Extended
/dev/sda5       154472448   156301311      914432   82  Linux swap / Solaris
/dev/sda6       132155392   154472447    11158528   83  Linux

Partition table entries are not in disk order

---

### Post by ixusubunt on 2013-05-27
A few more things ...

1. Apologies for not putting code tags around the terminal output ... it's a long time since I posted on the forum and I forgot the protocol!

Here it is again
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00083e70

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   132153442    66075697+  83  Linux
/dev/sda2       132155390   156301311    12072961    5  Extended
/dev/sda5       154472448   156301311      914432   82  Linux swap / Solaris
/dev/sda6       132155392   154472447    11158528   83  Linux


```

2. I Googled the problem and it seems that there are ways to carry out post-installation partition changes using applications such as GParted, so I installed it. When I open it gives me the option to reduce my large partition to just over 40Gb but no option to increase the small partition because it is mounted and would need to be unmounted manually. I can't figure out how to unmount it. Also, is this a safe way to go about it or am I barking up the wrong tree?! So far I have done nothing except put back my original settings, background, screensaver, panels, and so on.

3. I have nothing of any real importance on this laptop so it might be best to start all over again. Although I do have a reasonably large external hard-drive. Should I move the (old) home page onto this, re-install Lubuntu, and then put the home page back? ... or is there a simpler way of fixing things?

Thanks for your help.

---

### Post by ajgreeny on 2013-05-27
You must use a live CD/USB to run gparted safely, and even then you will probably need to right click on the swap partition and choose swapoff.

If there is enough space in your new home to copy all the files etc etc from your old home it may be worth trying to do so, but if you are prepared to do so, I think it may be simpler and quicker to start again after backing up everything, including all hidden folders and files, in your old home to your external disk.  I would recommend that you install this time with a separate /home partition as it makes reinstalls so much easier if you have to do it again for any reason.
[Separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome")
This site is for an older version but should still give you the basics for doing this.  The "Specify partitions manually (advanced)" is now shown as "Something Else", but I think everything should be easy to follow.

---

### Post by ixusubunt on 2013-05-27
I think I'll leave it for now ... seems to be working ok and I'll just have to remember where everything is.
In fact, I have so much unnecessary stuff in the old Home folder (30Gb of videos, photos, and music) that I might have a big clean up sometime.

Just a couple of final things ... every time I need to access the larger partition I have to enter my password. Is there a way of auto-loading it? 

Also can I rename it as it seems to be called "e8c26d26-6f64-47c8-83b3-d5d59c17c874" ... !!

Thanks again for your help. I always learn something from these mistakes e.g. don't press 'yes' unless you fully understand the implications!!

Cheers

---

### Post by ajgreeny on 2013-05-28
Apart from the files in your old home folders are you using the old ubuntu in any way, ie, do you occasionally boot to it, or do you now use only the new install?

---

### Post by ixusubunt on 2013-05-28
That's a good question! I don't think that I'm using the old Ubuntu ... why? is it still there?

I never really understood how Lubuntu works. Is it an operating sytem in it's own right or just Ubuntu running with a different desktop?

When I switch on my laptop, after the Fujitsu logo I get a black screen for a few seconds that lists several options and looks something like this:
[LIST]
[*]Ubuntu 
[*]Advanced options for Ubuntu 
[*]Memory test (memtest 86+) 
[*]Ubuntu 13.04 
[*]Advanced options for Ubuntu 13.04 
[/LIST]

This is just approximate, it doesn't last long and a I can't copy the screen. Only the top selection (Ubuntu) works ... anything else just re-boots the computer.

After I select Ubuntu or allow it to default to Ubuntu, I get the blue Lubuntu log-in page with (again!) some selections:
[LIST]
[*]KDE Plasma workspace 
[*]KDE/Openbox 
[*]LX games 
[*]Lubuntu 
[*]Lubuntu Netbook 
[*]Lubuntu Nexus7 session 
[*]Openbox 
[/LIST]
I just select Lubuntu.

I wish the machine would just switch on and automatically boot up into Lubuntu 13.04 ... nothing else!

---

### Post by ajgreeny on 2013-05-28
Let's see the output of ```
ls /media/paul/e8c26d26-6f64-47c8-83b3-d5d59c17c874
``` to see exactly what is on your old installation partition, and then I can tell you more about what is going on here.  You will have to mount that partition first to see any output, of course.

---

### Post by ixusubunt on 2013-05-28
Ok ... here it is:

```
paul@paul-AMILO-La1703:~$ ls /media/paul/e8c26d26-6f64-47c8-83b3-d5d59c17c874
bin    dev   initrd.img      libnss3.so  mnt   root  selinux  tmp  vmlinuz
boot   etc   initrd.img.old  lost+found  opt   run   srv      usr  vmlinuz.old
cdrom  home  lib             media       proc  sbin  sys      var
paul@paul-AMILO-La1703:~$ 

```

---

### Post by ajgreeny on 2013-05-29
Well it looks as if you have the full old system still there, with all the system folders of a normal installation.

It can be quite difficult to see what OS is what if you have several of the ubuntu family on one system; I know, as I did at one time have five OSs on my machine, all of the *ubuntu variety, and they all showed as ubuntu on the grub menu, even though there was Kubuntu, Xubuntu, Lubuntu and a second newer Ubuntu.  I overcame that by editing the /etc/default/grub file in each OS and changing the line ```
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
```to read ```
GRUB_DISTRIBUTOR="Xubuntu-12.04-amd64 Precise"
```as appropraite for that OS. Note the double quotation marks " in the edit instead of the backtic ` in the original.

Obviously grub manages to boot your new system, but does not seem to show your old one? Actually, I am not even certain about that, and I have not moved to 13.04 so am not aware of any changes in grub menu that may be on this newest system.

I suggest you download the **Boot-repair** script from my signature, run it and follow the instructions to produce a link for the boot-info-script output, which you post back here.

---

### Post by ixusubunt on 2013-05-29
I feel like I'm well out of my depth here!!

However I took your advice, downloaded Boot-repair from your link page, created an image on a CD and booted from it.

After it had looked at my system it provided the following link [http://paste.ubuntu.com/5714775/](http://paste.ubuntu.com/5714775/)

I have looked at this page and do not understand any of it!

Does it tell you anything that might help to improve my system?

---

### Post by ajgreeny on 2013-05-29
Thanks for that info which helps and I am now pretty certain it is the OS on sda6 that you are using, ie the one on the 10GB partition.

Can you please run the command mount from your ubuntu which will tell me exactly which of the two you are running.  We can then decide how to deal with the various files/folders/partitions to make sure that only what you do not need is removed, and that your whole system is cleaned up as best we can.

I note you have many kernels in your system which are not really needed. I always use synaptic to remove unwanted kernels, keeping just the two most recent.  You can see just how many you have with the command ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
``` which will list everything that shows in your grub menu, ie probably two entries for each kernel, plus memtest, all repeated again for the second OS on the disk.

Alternatively, as you have already suggested, it may be almost as simple to  backup everything including hidden files and folders from both system's  /home folders to separate new folders on your external disk and then  start again with a fresh clean install. You can then copy back  everything you need from the external disk to your new clean /home.

---

### Post by ixusubunt on 2013-05-30
The output from 'mount' is: 
```
paul@paul-AMILO-La1703:~$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/paul/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=paul)
paul@paul-AMILO-La1703:~$ 

```

Yes, I can see that the first line states sda6 ... seems like you are right!

Is there a quick fix?

Paul

PS. Thanks for the free Linux training course!

---

### Post by ajgreeny on 2013-05-30
You could convert the old OS partition sda1 into a separate /home with a bit of a workaround, and as it already holds some of your files it would not take too much doing.


[LIST]
[*]Backup any files you really need to keep from both OSs on your external disk, including the hidden files and folders. 
[/LIST]

[LIST]
[*]Delete all the folders except the username folder in /home from sda1, leaving you with just the one folder (your username) which you may need to move to the top of that partition file-tree, if you see what I mean, as you no longer want it in the folder /home/username, just in /username. 
[*]Edit your /etc/fstab file with ```
gksudo leafpad /etc/fstab
```adding lines ```
# /home added on /dev/sda1 after installation
UUID=e8c26d26-6f64-47c8-83b3-d5d59c17c874 /home           ext4    defaults        0       2
```at the bottom. 
[*]Run ```
sudo mount -a
```to check all is OK and the new home mounts properly.  This assumes your username has not changed. 
[*]If all is OK, the new separate /home should now be in use on the 69GB partition, and you should be able to copy across to it the files from the folders that are now in your external disk.
[*]Run ```
sudo update-grub
```to remove the old OS from the grub menu. 
[/LIST]

This may all seem very complicated to you at the moment, but if you can manage to do it you will understand a great deal more about the Linux filesystem and how it all fits together and works (hopefully it works, anyway).

Good luck, if you choose to try, but if not you will have your files backed up so you can do a clean install then copy across your old files to your new home, which again I recommend you have as a separate partition; see my link in post #5.

---

### Post by ixusubunt on 2013-05-31
Mmmm .... that didn't work (I am now logged in as 'Guest' as paul does not work anymore!)

I followed your instructions and added the line to fstab, but when I ran 'mount -a' I got an error message stating something about there being no end line in fstab. I tried to go back to fstab to have another stab at it (no pun intended!) but it was not possible.

Looks like re-install necessary but no time at present, will do it later.

Just one thought ... now that I have the disc, is it worth booting from Boot-repair and seeing what happens. After all, I have nothing to lose so may as well play around a bit.

Paul

---

### Post by ajgreeny on 2013-05-31
Just a quickie!  Try adding an empty line at the end of your fstab file if there isn't one already.

---

### Post by ixusubunt on 2013-05-31
I can't sudo anymore as I'm logged in as guest! If I try to login as paul with my normal password it just cycles the log-in screen so I can only pick 'guest'.
Is there any other way of editing fstab?

---

### Post by ajgreeny on 2013-05-31
You can either do it via a live system (CD or USB), mounting the installed OS partition and then editing with ```
gksudo leafpad
``` or text editor on the live system, or you could do it from recovery mode of the installed system. From recovery mode run ```
mount -o rw,remount /
```then  ```
nano /etc/fstab
``` use cursor keys to get to the end of the final line and just hit return to give you an empty line and proper end-of-line marker to the file.  Use Ctrl+X to exit, then hit enter to save the file. Now try running **sudo mount -a** again after a reboot.

It appears that fstab always needs an empty line at the end, see posts 8 and on of this thread [http://www.kubuntuforums.net/showthread.php?62143-How-do-I-change-fstab](http://www.kubuntuforums.net/showthread.php?62143-How-do-I-change-fstab), something I admit I was not aware of, so my full apologies for that slip-up.

Nearly there - let's hope!

---

### Post by ixusubunt on 2013-05-31
Ok I got into recovery mode and added the final line to fstab, saved it ... but how do I reboot from the root prompt without typing exit and going back to the recovery menu? 
The only sensible option in the recovery menu looks like  'resume normal boot' , but this seems to lose the changes. Is there a re-boot command I should be using rather than exit or should I crash out of it by holding down the power switch on the laptop?

---

### Post by ixusubunt on 2013-05-31
Ignore previous message ... going back to the recovery menu and choosing to 'resume boot' does not lose changes and seems to be the only way out of recovery mode.

I am pretty sure my fstab file is now ok but I still cannot log in normally (I'm typing this on another PC). One thing I did notice is that editing the fstab file via nano automatically adds another line when you save it ... so if you add one then you get two! 

I think that's all I can do. Tomorrow I'll re-install Lubuntu and set up a separate 10Gb home partition as recommended.

The only other tip I would appreciate is how to get rid of obsolete kernels and clean out any other necessary OS.

One observation when logged in as Guest ... the machine is really fast!!

Thanks

---

### Post by ajgreeny on 2013-06-01
Sorry we did not make it all work for you as hoped, but at least a re-installation will give you a clean start with a brand new unadulterated OS, and hopefully you have learned a bit more about Linux and its workings.

However, when you set up your partitions I suggest you use **10GB for root**, about **2GB for swap**, depending on how much ram you have, and the rest, 68GB for /home, by deleting all the current partitions when you get to the "Something Else" partitioning stage.  A 10GB /home will very quickly fill up if you have lots of photos, music, videos and documents, but will be plenty for a Lubuntu root partition for most people.  Backup everything first of course or you will lose all your files.

Once upon a time it was always suggested that swap was at least as large as your ram, and if you were short of ram to make swap larger.  Now with machines generally having plenty of ram it is possible to run without swap, but I have used 2GB for a long time until now, with a new machine which has 8GB ram and as I want it to hibernate, I have given myself 8GB swap as well.

To keep kernels down to a small number I always check what I have with command ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
```which will list them all for you; they do not show by default in the grub menu any more unless you choose to open the "Previous versions" item in the menu, but that command shows everything.  I then use synaptic, searching by name alone for the oldest kernel numbers, eg **3.5.0-27**, and remove those I don't need as well as the header packages with the same version number, leaving just the most recent and the one before that as backup.

---

### Post by ixusubunt on 2013-06-02
Re-installed today ... took less than an hour and everything fine now.

Took ages to copy all Home files back, but it was worth it as everything is there, even panel settings, favourites, email messages etc.

I now have 68Gb to play with instead of 10!

Thanks for your help (and patience!)

Paul

---

### Post by ajgreeny on 2013-06-02
Wonderful!

Enjoy yourself.

---

