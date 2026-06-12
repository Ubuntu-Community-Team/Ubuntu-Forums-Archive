---
title: "How to share files between dual-booted WinXP &amp; Ubuntu installed by Wubi"
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by nesnera on 2010-01-25
I'd like to install at several WinXP computers Ubuntu 9.10 for testing. I decide to install Ubuntu by [Wubi]("http://wiki.ubuntu.com/WubiGuide") (dual-head, install "without" partitioning disc, easy way to restore original state). Users should try out Ubuntu for 1-2 months therefore they need "to share" their data between both OS. When I tried to redirect Linux home folder to XP home I find out two problems in default mount settings:
1) common users haven't write permission to host (win) disc
2) files containing nonASCII characters are [handled and displayed incorrectly]("http://www.abclinuxu.cz/images/screenshots/5/3/102535-store-for-snapshots-13172.png")
Do you know how can I reach my goal? Thanks

---

### Post by labinnsw on 2010-01-25
Removed Comment

---

### Post by Mark Phelps on 2010-01-25
You can't share "home" folders between the two OS's-- MS Windows does not understand the Linux file systems and can't manage the permissions properly.

If you want to share data, the best approach is to create a separate data partition and format it as NTFS -- since both Linux and MS Windows can read/write NTFS files.

---

### Post by Ginsu543 on 2010-01-25
+1.

I dual-boot Windows XP and Ubuntu 9.10 and run Windows XP as a virtual machine in VirtualBox and the easiest way I've found to share data among all three with no hassles is to do what Mark said. If you look at my siggy, you'll see that I have 2 x 1 TB drives for data and they are both formatted in NTFS. Ubuntu is way more trustworthy to handle NTFS than is Windows to handle ext4.

---

### Post by gadolinio on 2010-01-25
As you have ubuntu inside  windows, you can store your data in the same partition where windows is (/host) or in another NTFS partition. I'd try the latter.
If you can, create a new ntfs partition in the machine's hard disk.
Then you can set both windows and ubuntu to use some folder inside it as the default user folder.

In windows you can do this by right clicking "my documents", and searchin through the tabs. In one of them you'll find the path "C:\docuemnts and settings\USERNAME\". Replace it with the one you want to create in the new partition. For example "D:\dualbooter" or whatever you want. (remember to have the partition and the folder already created before doing this).

Then in ubuntu you can create a new user, or modify an existing one (as long as it is not root!).
In the "advanced" tab you'll also see the user's path. Change it to, for example, "/media/VOLUME_WHERE_NTFS_PARTITION_IS_MOUNTED/dualbooter".
This way, both OS will store the user's data un the same folder.

Some interesting things:
-If both OS are in the same language, the desktop folder will be called exactly the same. So when you place or delete a file from the ubuntu's desktop, that change will also be present when you boot with windows.
-Other folders are called differently. "my music" in windows, but just "music" in ubuntu. Just delete ubuntu's one and use the other (because windows has direct links to "my images" for example, and it'll be easier to continue using them).
-ubuntu stores configuration files and folders starting with a point. When you use windows you'll see those folders, what can be somewhat annoying. It depends on the person who uses it.

Hope you find this useful... Reply if you have any trouble

---

### Post by J V on 2010-01-25
> **Mark Phelps said:**
> You can't share "home" folders between the two OS's.Incorrect! How often have I seen this question?

If you create symlinks (linux shortcuts) from Pictures to the NTFS "My pictures" etc etc etc, you can share almost your entire home (Including settings if you use the same app on both OSs...)

---

### Post by nesnera on 2010-01-27
Thanks a lot for all reply. As seems I'm on the right way but I must emphasize my main problem isn't whether it is possible to redirect Linux home to Windows home (yes, it's possible :D) but _where and how_ to modify default behaviour if I want reach **write access** (for non roots) and correct handling **non ASCII** characters.
Additional informations (hopefully useful):
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#

proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/usr.disk /usr            ext4    loop            0       2
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
``````

mount
/dev/loop0 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda1 on /host type vfat (rw)
/dev/loop1 on /usr type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/pazdera/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=pazdera)
```
Question is - what mounts /dev/sda1 to /host and what limits write access only for root?
Notice - [Ubuntu Tweak]("http://ubuntu-tweak.com/") seems be good choice for [folder manipulation]("http://www.abclinuxu.cz/images/screenshots/5/3/102535-store-for-snapshots-20717.png")

---

### Post by gadolinio on 2010-02-01
> **nesnera said:**
>  ... _where and how_ to modify default behaviour if I want reach **write access** (for non roots) and correct handling **non ASCII** characters.


To gain writing permission on NTFS drives, you can use disk-manager.
You can download it from http:/packages.ubuntu.com/search?disk-manager
Once installed, it will be in system-->administration-->disk manager. You'll be asked for your password.
Once the program is opened, you'll find two tabs. Go to the second one, where you'll have the list of hard drives in the system. Select the one you want to write on and click the "edit" button on the lower part of that screen. (you may be told to unmount that drive firs; if so, do it). When you edit the disk, in the new window you have to choose "ntfs-3g" read and write driver.
Then apply changes, make sure the check box is ticked for that drive, and that's it. I write in windows' ntfs hard disk this way.
Hope you find this useful...

---

### Post by nesnera on 2010-02-03
> **gadolinio said:**
> .. you can use disk-manager ..

Thanks for response - I'll try that.
I have got new opinions in this case:
- I made the same procedure at a different machine (XP with ntfs) - non-ASCII and write access for non-root users works well. It seems the problem is only with vfat.
- Tweak is nice tool but without expected effect. I had to delete the directories (Music, Pictures etc.) and replace them by symlinks pointed to equivalent XP home directories.

---

### Post by ellebanna on 2010-05-15
> **gadolinio said:**
> As you have ubuntu inside  windows, you can store your data in the same partition where windows is (/host) or in another NTFS partition. I'd try the latter.
If you can, create a new ntfs partition in the machine's hard disk.
Then you can set both windows and ubuntu to use some folder inside it as the default user folder.

In windows you can do this by right clicking "my documents", and searchin through the tabs. In one of them you'll find the path "C:\docuemnts and settings\USERNAME\". Replace it with the one you want to create in the new partition. For example "D:\dualbooter" or whatever you want. (remember to have the partition and the folder already created before doing this).

Then in ubuntu you can create a new user, or modify an existing one (as long as it is not root!).
In the "advanced" tab you'll also see the user's path. Change it to, for example, "/media/VOLUME_WHERE_NTFS_PARTITION_IS_MOUNTED/dualbooter".
This way, both OS will store the user's data un the same folder.

Some interesting things:
-If both OS are in the same language, the desktop folder will be called exactly the same. So when you place or delete a file from the ubuntu's desktop, that change will also be present when you boot with windows.
-Other folders are called differently. "my music" in windows, but just "music" in ubuntu. Just delete ubuntu's one and use the other (because windows has direct links to "my images" for example, and it'll be easier to continue using them).
-ubuntu stores configuration files and folders starting with a point. When you use windows you'll see those folders, what can be somewhat annoying. It depends on the person who uses it.

Hope you find this useful... Reply if you have any trouble
:confused:
help? i don't quite understand. really, i feel quite stupid when people explain compie stuff to me.  it's like i can figure out so much on my own, but i need it explained very simply if it's something i don't know.

i have a 250 GB HD and I formatted it and reinstalled XP.  It is already partitioned into ~150GB and ~100 GB.  I am having trouble with my Ubuntu CD so i figured I would try Wubi again.

ps. i will absolutely love you in a non-creepy way if you could include some screenshots

---

### Post by gadolinio on 2010-05-15
> **ellebanna said:**
> :confused:
help? i don't quite understand. really, i feel quite stupid when people explain compie stuff to me.  it's like i can figure out so much on my own, but i need it explained very simply if it's something i don't know.

i have a 250 GB HD and I formatted it and reinstalled XP.  It is already partitioned into ~150GB and ~100 GB.  I am having trouble with my Ubuntu CD so i figured I would try Wubi again.

ps. i will absolutely love you in a non-creepy way if you could include some screenshots

What's your exact problem? Please provide detailed information.

---

### Post by ellebanna on 2010-05-15
> **gadolinio said:**
> What's your exact problem? Please provide detailed information.

You suggest storing data in another NTFS partition and then go on to explain how to do it, but I don't understand the instructions you gave--

> **gadolinio said:**
> In windows you can do this by right clicking "my documents", and  searchin through the tabs. In one of them you'll find the path  "C:\docuemnts and settings\USERNAME\". Replace it with the one you want  to create in the new partition. For example "D:\dualbooter" or whatever  you want. (remember to have the partition and the folder already created  before doing this).

It seems as though you wrote clearly, I just do not seem to understand. . . maybe a case of PEBKAC?:(

---

### Post by gadolinio on 2010-05-16
> **ellebanna said:**
> You suggest storing data in another NTFS partition and then go on to explain how to do it, but I don't understand the instructions you gave--



It seems as though you wrote clearly, I just do not seem to understand. . . maybe a case of PEBKAC?:(

What's PEBKAC? :S

In the post you quote I suggest a way of having both <the documents a user creates when using windows> and <the ones he creates when using ubuntu> in the same folder, in a NTFS partition for storage purposes.
I'm trying to explain how to tell windows to use that folder as the default user folder, so that when you enter "My documents" you actually go to the folder outside windows's partition.
To do that (in windows XP, and I think in Vista also) you right-click the "my documents" icon you have on your windows's desktop, and then choose "properties". A window with some tabs on the upper part will appear. The first tab is called something like "destination", and has a text box with the title "folder's location". Change the content of that text box to the path of the folder you want to use (the one in the other NTFS partition). For example, if the ntfs partition is D:\, and the folder is called "user", you should put in the text box "D:\user" (without the quotes). Then click "accept".

---

### Post by ellebanna on 2010-05-16
> **gadolinio said:**
> What's PEBKAC? :S

In the post you quote I suggest a way of having both <the documents a user creates when using windows> and <the ones he creates when using ubuntu> in the same folder, in a NTFS partition for storage purposes.
I'm trying to explain how to tell windows to use that folder as the default user folder, so that when you enter "My documents" you actually go to the folder outside windows's partition.
To do that (in windows XP, and I think in Vista also) you right-click the "my documents" icon you have on your windows's desktop, and then choose "properties". A window with some tabs on the upper part will appear. The first tab is called something like "destination", and has a text box with the title "folder's location". Change the content of that text box to the path of the folder you want to use (the one in the other NTFS partition). For example, if the ntfs partition is D:\, and the folder is called "user", you should put in the text box "D:\user" (without the quotes). Then click "accept".

okay, changed the windows  my docs to my D drive--thanks, I understand it!

PEBKAC (PEBCAC)--problem exists between keyboard (computer) and chair  ;)

ok, now to DL Wubi!  I will likely be back with some new problem, I am rather new to messing with computers, but I love it!

---

### Post by ellebanna on 2010-05-16
Why are there different sizes for Wubi?  I do not remember seeing this before.  I assume I should go for the largest, since I have waaaaay more than 30GB to spare?

Also, do I install this on the C partition (the main one) 
or the D partition ( where I just redirected my docs to)?

---

### Post by gadolinio on 2010-05-17
> **ellebanna said:**
> Why are there different sizes for Wubi?  I do not remember seeing this before.  I assume I should go for the largest, since I have waaaaay more than 30GB to spare?

Also, do I install this on the C partition (the main one) 
or the D partition ( where I just redirected my docs to)?

Wubi is intended for testing more than full/definitive use of ubuntu, so it lets you give ubuntu a little space enough for you to see how it works but without too much commitment (that would be, without making a special partition on the hard disk). If you know you will need much space, and/or have plenty of it anyway, go for the biggest amount of space.
(There might be some technical reason to justify the upper limit, I don't know).

I've used the main disk in one occasion, and a storage partition in another computer. Both worked OK. Don't know if there is any difference, pros and cons, etc.

Regarding your transferred documents, I think it would be tidier to have them in a folder inside D, instead of D "itself"/the main directory.

---

### Post by ellebanna on 2010-05-17
> **gadolinio said:**
> Wubi is intended for testing more than full/definitive use of ubuntu, so it lets you give ubuntu a little space enough for you to see how it works but without too much commitment (that would be, without making a special partition on the hard disk). If you know you will need much space, and/or have plenty of it anyway, go for the biggest amount of space.
(There might be some technical reason to justify the upper limit, I don't know).

I've used the main disk in one occasion, and a storage partition in another computer. Both worked OK. Don't know if there is any difference, pros and cons, etc.

Regarding your transferred documents, I think it would be tidier to have them in a folder inside D, instead of D "itself"/the main directory.

this is the current loc-D:\Documents\~annabelle~\My Documents. i think i went for 25 GB since the wifi is being slow for no good reason

I TRIED getting Ubuntu three times now and I am just having trouble, and of course both my geeky guy friends have been acting like PMSing women plus they both want to get it but neither has ever done it.  so i do not know what to do--i may try a different software for the image or whatever (i am at the point where i do not know what i am talking about) :(

thus, i went for wubi before, loved it, but i never got it optimised for my needs, which is what I am attempting to do now.

---

