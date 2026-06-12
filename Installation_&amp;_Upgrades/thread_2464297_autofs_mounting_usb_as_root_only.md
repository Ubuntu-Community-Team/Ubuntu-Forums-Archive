---
title: "autofs mounting usb as root only"
date: 2021-06-28
forum: Installation &amp; Upgrades
---

### Post by stevenjrees on 2021-06-28
- i don't have anything in fstab for the usb hdd drive i am using
- i am using a usb3 to sata convertor
- i do not have auto.misc enabled and no other specific settings for the usb

autofs does however automatically mount the drive when plugged in. 

the drive is mounted as removable media under /media/me/UUID 
* this is desirable behaviour up to this point

However; 
it mounts the drive as root and i have to use su to do anything

---

### Post by TheFu on 2021-06-28
That isn't **autofs**.  That is something else, probably systemd-mount or systemd-automount.
If you want to control the mount options, there are multiple different ways, which depend on a few things:

[LIST]
[*]Do you want to have it mount on-demand or always at boot? What should happen if it isn't there?
[*]Which file system(s) do the partitions have currently?  ext4, ext2/3, zfs, ntfs, exfat, fat32, f2fs, xfs, btrfs, something else?
[*]Are multiple Linux users going to need read/write access or just read-only?  Need to know for correct permissions to be setup.
[/LIST]

With the answers to those questions, good advice can be provided.

---

### Post by stevenjrees on 2021-06-29
hi, 

the way it works now is good. i.e. plugin, it auto mounts, select safe remove to unmount. 
file systems will be ext4, ntfs, fat, brts

only problem is, the mount is root. any logged in user should be able to use the usb hdd or usb key

I have autofs for mounting nfs shares - works no problem. otherwise, it is vanilla 21.04 install

---

### Post by Morbius1 on 2021-06-29
> [COLOR=#ff0000]**any logged in user**[/COLOR] should be able to use the usb hdd or usb key

Not as long at it mounts to /media/me/UUID. Even if the permissions on /UUID were 777 only "me" will gain access to it. That is by design.

Run:
```
getfacl /media/$USER
```
You should get something like this:
> tester@vub2004:~$ getfacl /media/$USER
getfacl: Removing leading '/' from absolute path names
# file: media/tester
# owner: root
# group: root
user::rwx
[COLOR=#0000cd]**user:tester:r-x**[/COLOR]
group::---
mask::r-x
other::---
Only the user that plugged in the device ( and root ) can traverse the /media/$USER directory to get to what is mounted under it.

---

### Post by TheFu on 2021-06-29
> **stevenjrees said:**
>  file systems will be ext4, ntfs, fat, brts

I know nothing about btrfs. That's a different animal.

I do know how to deal with ext4.  Just **chown** and **chmod** on the top level. That sticks with the file system and it will work the same going forward.

I know for non-Linux file systems, ntfs, exFAT, FAT32, the only answer is to set the permissions using mount options. In general, that means adding a uid=stevenjrees to every mount for non-native file systems.  If you also want better performance from NTFS storage, then add the big_writes option too.

For an NTFS partition here, I use these options - configured via autofs - 
Inside /etc/auto.misc, which is configured in auto.master:
```
/misc/250G    -nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,fstype=ntfs,uid=1000,gid=1000,fmask=0002,dmask=0002    LABEL=250G
```

This mounts based on the LABEL of the partition. I prefer those over UUIDs. Labels are easier for humans. By using autofs, the storage mounts on-demand and umounts when not in use. I find that handy since it is usually mounted for only a few hours a week to a Linux system.

Here's the result:
```
$ dft
Filesystem                        Type     Size  Used Avail Use% Mounted on
/dev/sdc1                         fuseblk  233G   27G  207G  12% /misc/250G

$ mount |grep 250
/etc/auto.misc on /misc/250G type autofs (rw,relatime,fd=6,pgrp=3345,timeout=60,minproto=5,maxproto=5,direct,pipe_ino=34590)
/dev/sdc1 on /misc/250G type fuseblk (rw,nosuid,nodev,noatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096)

```
And finally, the result:
```
$ ls -alF
total 27622821
drwxrwxr-x 1 thefu   thefu      12288 Jun 28 19:49 ./
dr-xr-xr-x 8 root    root        4096 Apr 20  2020 ../
-rwxrwxr-x 1 thefu   thefu 2098380981 Dec 31  2012 Encode_4254.mp4*
```

---

### Post by ActionParsnip on 2021-06-29
if it is NTFS then run a full chkdsk in Windows too so that you know the file system is perfect

---

### Post by stevenjrees on 2021-06-29
> **Morbius1 said:**
> Not as long at it mounts to /media/me/UUID. Even if the permissions on /UUID were 777 only "me" will gain access to it. That is by design.

Run:
```
getfacl /media/$USER
```
You should get something like this:

Only the user that plugged in the device ( and root ) can traverse the /media/$USER directory to get to what is mounted under it.

Yes, this is exactly what i get with getfacl 

I can not traverse lost&found
I can open a file that is on the drive
I cannot create a new file (eventhough it was formatted on the system with btrs)

---

### Post by TheFu on 2021-06-29
Use chmod to make the permissions whatever you like. Use chown to set the owner of the directories.  The owner change is necessary just once with any native Linux file system.  Nothing unexpected has happened - well - except using btrfs for usb storage.

End-users shouldn't have access to lost+found. That is expected on every file system.

---

### Post by stevenjrees on 2021-06-30
> **TheFu said:**
> Use chmod to make the permissions whatever you like. Use chown to set the owner of the directories.  The owner change is necessary just once with any native Linux file system.  Nothing unexpected has happened - well - except using btrfs for usb storage.

End-users shouldn't have access to lost+found. That is expected on every file system.

that doesn't work.

1) if i change the owner of /media/$USER from root:root to user:user 
    a) I can see and write into the drive - yes
    b) drive no longer mounts on next reboot/login or if dismounted, it cannot be remounted

2) if i;
    a) change owner back to root
    b) systemctl restart autofs 
    dive again remounts, but back under root. 

It suggests the autofs is what is mounting the drive, even though i do not have auto.misc configured no? does autofs have a default config maybe?

---

### Post by TheFu on 2021-06-30
If you don't setup autofs for the storage, then it isn't autofs being used.  It is something else as said above.  gio or gvfs probably.  IMHO, those are abominations, but end-users want to point-n-click regardless of terrible performance.

If btrfs is doing something special, that is where I'd look. I've never touched it, since early on it had data loss problems with the primary way that I use storage.

If you think autofs is involved, it will be in the log files. What do those say?  All my systems don't automount storage through any GUIs.  The power to mount is the power to destroy. Only root should have that power, unless I setup a specific mount location for a specific device.

It would really help us if you'd run commands and post the output here. We are used to seeing that stuff.  For examples, look at how we did the same above. We showed proof.

---

### Post by Morbius1 on 2021-07-01
I admit I'm getting confused by all this.

[1] I don't know why autofs is getting referenced in all this.

The way an external usb storage drive automatically mounts is in fact an auto-mounting process but it's not an "automounter" like the old autofs process or the systemd equivalent. It's a udisks / udev thing.

I just inserted an ext4 formatted USB stick into my system. If I run the mount command I see it's using udisks:
> tester@ub2004:~$ mount | grep udisks
/dev/sde1 on /media/tester/USBExt4 type ext4 (rw,nosuid,nodev,relatime,data=ordered,[COLOR=#ff0000]**uhelper=udisks2**[/COLOR])

[2] I don't understand the write access inability you are experiencing.

If your device is mounting to /media/me/UUID I can understand why everyone but "me" cannot write or even get access to /UUID but it shouldn't pose a problem for "me" - as long as the permissions on/UUID itself allow it. 

I do have a question though and it's about the contents of these USB storage devices. What's on them? Is it just a bunch of data?

The reason I ask is because if you want access by every local user to these devices you really only have two alternatives here:

*** Create an fstab entry for every single external USB HDD you come across and make sure the mount point is anywhere other than under /media/$USER/

*** OR if there can be any number of random external devices use bindfs to create a view that gives write access to everyone regardless of the Linux permissions.

Example:

Create a new mount point .. say at /USBMedia

Install bindfs: 
```
sudo apt install bindfs
```

Temporally remount /media to /USBMedia with a set of permissions that allows anyone write access - something like this:
```
sudo bindfs -o perms=0777 /media /USBMedia
```

Whenever a USB HDD is attached to the system it will mount twice:

Once under /media/tester [COLOR=#ff0000]which you will use to unmount the device.[/COLOR]

And again - [COLOR=#ff0000]as a "view"[/COLOR] - under /USBMedia/tester where the permissions allow write access to all since that is how you defined it ( perms=0777 ). Note: These permissions are immutable and are the same throughout the "view".

To undo the bindfs remount:
```
sudo umount /USBMedia
```

An equivalent entry in fstab will have this "view" remount happen at every boot if it satisfies your use case. This bindfs method may not be applicable or desirable in your situation since I don't know how these external HDD's are being used.

---

