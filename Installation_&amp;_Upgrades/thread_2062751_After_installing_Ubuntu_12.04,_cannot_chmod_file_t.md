---
title: "After installing Ubuntu 12.04, cannot chmod file to be exectable on separate disk"
date: 2012-09-25
forum: Installation &amp; Upgrades
---

### Post by sprilutsky on 2012-09-25
Hi there,

After I performed fresh install of Ubuntu 12.04 on sda drive, I cannot change perms on one of the files to make it executable.

I own the file as a user, i ran chmod as user or root with either +x, or u+x, or 700. Command runs, but file is still **rw**, not rw**x**.

I even tried to right click on it using GUI, then click the box for the "executable". It marks it as executable, and then immediately removes it by itself.


Anyone ran into this before?

---

### Post by cortman on 2012-09-25
Re-own it as your user

```
sudo chown username file
```

Then try changing the permissions:

```
chmod u+rwx file
```

Make sure you're logged in as your user when running chmod.

---

### Post by sprilutsky on 2012-09-25
Already tried all that, do not work.

---

### Post by Morbius1 on 2012-09-25
Is the file in question sitting on an NTFS or FAT32 partition? You can't chown or chmod such a file.

---

### Post by sprilutsky on 2012-09-25
I was able to before, than I was running Ubuntu 9.04.

---

### Post by sprilutsky on 2012-09-25
I am thinking - 12.04 mounts it differently than 9.04. Can someone confirm/deny that

---

### Post by cortman on 2012-09-26
I don't think so, but your question is a little unclear.

I know you'd tried some of the commands earlier- did you try them again in the sequence I gave?

---

### Post by Morbius1 on 2012-09-26
There was a change to the default mount parameters for NTFS partitions around maybe 10.04 or so - I can't remember exactly when. Before then all files would be 777 now all files are 600.

If this is an internal partition you can reproduce the way it was done back then by creating your own entry in fstab. Use the following template as a guide:
```
UUID=DA9056C19056A3B3 /media/Win ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
```[COLOR=Blue]*This will mount the NTFS partition with you as owner and all folders and files will have permissions of 777.*[/COLOR]

To find the correct UUID number for you partition run the following command:
```
sudo blkid -c /dev/null
```Create the mount point:
```
sudo mkdir /media/Win
```If you have mounted the partition manually [COLOR=Blue]unmount it first[/COLOR] then run the following command to mount it again with the new line in fstab:
```
sudo mount -a
```
[COLOR=Blue]**Note**[/COLOR]: If you only want it to be accessible and executable to you then change the umask to 077. this will make all files and folders 700:
```
UUID=DA9056C19056A3B3 /media/Win ntfs defaults,nls=utf8,umask=077,uid=1000,windows_names 0 0
```

---

