---
title: "Need help with accessing usb external hard drive with Ubuntu 12.04"
date: 2012-09-15
forum: Installation &amp; Upgrades
---

### Post by rohmalik on 2012-09-15
Hi everyone,

Having really hard time being able to properly mount my eternal usb hard drive. I have read most of the forums here but never seem to find up to date one simple easy to follow steps from beginning to end on how to properly mount and access and external usb hard drive from which i want to be able to pull all the files and move them to my internal storage hard drive.

I am using hitachi 3 tb external hard drive that seems to have hfs+ format. Was originally format on macbook.

I would really very much appreciate if someone can please help me understand the correct and easy to follow step by step process.

---

### Post by darkod on 2012-09-15
Have you tried something like this?
[http://ivanhoecomputers.com/how-to-mount-mac-hfs-read-and-write-with-ubuntu-linux/](http://ivanhoecomputers.com/how-to-mount-mac-hfs-read-and-write-with-ubuntu-linux/)

It also depends if you want to mount it only temporary, or on every boot. So it can mount on every boot you will have to add an entry in /etc/fstab but I am still not sure how to format that entry correctly.

---

### Post by rohmalik on 2012-09-15
thanks Darkod for replying quickly. Basically i just want this external HD to connect temporarily to give me ability to move all the files from in it to my storage HD. I am just trying to copy all media files from.

I will try those steps you provided in the link. and report back to you if it works.

once again thank you very much for a quick reply.

---

### Post by ajgreeny on 2012-09-15
Try this, which may only give you read permissions, but may be all you need for what you are wanting to do.

1) sudo apt-get install hfsplus hfsprogs hfsutils

2) mount -o force -t hfsplus /dev/XXX /mnt/

---

### Post by rohmalik on 2012-09-15
Hi guys,

I tried both the steps however it still deosnt let me read view the drive. 
Any other suggestions?

Please let me know

Thanks,

---

### Post by darkod on 2012-09-16
Are you sure you can't see it or you just don't know where to find it?

If you expect to see it in the GUI like Nautilus file browser, only if you mount it in /media/<foldername> it will show there.

If it's mounted for example in /mnt/<foldername> it doesn't show in Nautilus but you can access it in terminal always.

After you mounted it, did you try to list the content of that mount point with:
```
ls /mountpoint
```

---

### Post by rohmalik on 2012-09-16
thanks darkod. i can see it but cant mount it. it keeps telling me

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I can create a media/storage on it as it needs permissions.

I simply just want to connect it mount it so i can get in it to grab the files from it.

please let me know if need to anything else beside formatting it that would delete everything on it.

---

### Post by darkod on 2012-09-16
First, you don't create /media/storage "on it", you create that mount point in your ubuntu filesystem. The /media is there anyway, so the folder will be created in the ubuntu filesystem.

Are you sure the filesystem you are trying, hsf+ is correct? And that the disk is not already mounted? The links posted mentioned something that the disk might try to auto mount when you connect it.

With the disk connected, post the output of:
```
sudo parted -l
df -h
mount -l
```That might help us.

---

