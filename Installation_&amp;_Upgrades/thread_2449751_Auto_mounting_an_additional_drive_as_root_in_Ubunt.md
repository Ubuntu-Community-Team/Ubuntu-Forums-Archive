---
title: "Auto mounting an additional drive as root in Ubuntu 20.04 - and not mounting it as th"
date: 2020-09-01
forum: Installation &amp; Upgrades
---

### Post by wavesailor on 2020-09-01
Auto mounting an additional drive as root in Ubuntu 20.04 - and not mounting it as the user

My fstab entry looks like this:

```
/dev/disk/by-uuid/8a713da5-a410-4d61-8837-655e75f91d7f /mnt/dataXtra auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=dataXtra 0 2
```

When I auto mount an additional drive in Ubuntu 20.04, it mounts it under the username.

Before Mounting:
```
ll /mnt
drwxr-xr-x 4 root root 4096 Sep 1 17:47 ./
drwxr-xr-x 24 root root 4096 Sep 1 16:58 ../
drwxr-xr-x 2 root root 4096 Aug 12 16:43 dataXtra/
```

and then After mounting:
```
ll /mnt
drwxr-xr-x 4 root root 4096 Sep 1 17:47 ./
drwxr-xr-x 24 root root 4096 Sep 1 16:58 ../
drwx------ 4 wavesailor wavesailor 4096 Sep 1 16:36 dataXtra/
```

How do I get the mount to be "owned" by **root** and not the user **wavesailor**

---

### Post by TheFu on 2020-09-01
Do you want to use the autofs/automounter daemon to mount on-demand 
or 
do you just want the storage mounted at boot?

Please clarify which "auto mount" is desired.
[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)
or
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

fstab isn't auto mounting. It is a standard mount. All storage mounted that way, appear like local storage.

For the fstab method, I'd use:
```
UUID=8a713da5-a410-4d61-8837-655e75f91d7f    /mnt/dataXtra    NEED-REAL-FS-TYPE-HERE    nosuid,nodev,nofail 0 2
```
All on 1 line.   I don't use "auto" for the file system type. Clearly say what that file system actually is.
The  /mnt/dataXtra directory must exist.

After the mount is done, just use chown to make the permissions what you like. This assumes the file system supports chown. NTFS and FAT-whatever do not.


If you want help with the real automount setup, I can help with that too. It is what I use for all USB or NFS storage so they are mounted on-demand, not always.

---

### Post by wavesailor on 2020-09-01
Hi .. Thanks

The drive is formatted as ext4 so I added the line as you mentioned to fstab.
```
UUID=8a713da5-a410-4d61-8837-655e75f91d7f    /mnt/dataXtra    ext4    nosuid,nodev,nofail 0 2
```

But it didn't help. The drive is still mounted like this at the mount point - with username owning it and not root:
```
ll /mnt
drwxr-xr-x 4 root root 4096 Sep 1 17:47 ./
drwxr-xr-x 24 root root 4096 Sep 1 16:58 ../
drwx------ 4 wavesailor wavesailor 4096 Sep 1 16:36 dataXtra/
```


I would like it to be mounted automatically and as root - and not as the username.

Background: My laptop has two drives in it. SSD and HDD. The SSD has Ubuntu 20.04 installed on it and HDD is to be used for extra space(dataXtra). My goal is to make it a samba file share which can be accessed on my network. I could not get the samba file share to work on the "dataXtra" drive and the cause seems to be the way the drive is mounted. When I make the samba share under /var/samba/share it works perfectly.

---

### Post by TheFu on 2020-09-02
```
chown root:root /mnt/dataXtra
```
That will stick with the fstab I posted.  It does here.

Samba doesn't care about file permissions on the Unix side.  Samba runs as root and inflicts whatever permissions it wants.  The permissions don't have anything at all to do with samba.

Now, samba has some challenges because in the last 6 months both Samba and MSFT have changed their default settings for file sharing as clients and servers.  That's a completely different question, that I only know about slightly.  Someone else will need to help.

And Canonical hasn't done a good job conveying some of the new software package methods they're pushing.  I don't know if snap packages are used for Samba or not, but snaps are constrained to accessing specific directories only. There is no workaround for other directories beyond the hard-coded, 3 that the Snap team has decided are all anyone needs. Only 1 directory is automatically configured to work. The other 2 need to specifically be requested.  I hope that samba isn't a snap package, but if the GUI program to access the samba share is on Linux, it could easily be a snap and constrained to not have access.

Anyways, for the samba question, best to start a new thread, provide the exact server and the exact clients to be used, and post the output from **testparm** run on the samba server machine. If the "server" has a desktop install or a server install will matter too, since Linux servers don't setup zeroconf name resolution.

Update:  you have to remount the storage between fstab changes.  
```
sudo umount  /mnt/dataXtra
sudo mount -a
```
And no processes or shells can be accessing anything in /mnt/dataXtra when the umount command happens or that won't work.

---

