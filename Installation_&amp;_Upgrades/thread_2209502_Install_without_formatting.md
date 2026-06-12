---
title: "Install without formatting"
date: 2014-03-06
forum: Installation &amp; Upgrades
---

### Post by gavannon on 2014-03-06
I'm trying to install the new Ubuntu 13 from CD. I'm installing OVER TOP of an old, corrupt Ubuntu install. I don't want to format anything, and want to just install linux and recover my files. Please help!

During the disk formatting pages, I've chosen "configure encrypted volumes", and unlocked my encrypted volume. 

I now have: guided partitioning, configure software RAID, configure logical volume manager, configure encrypted (already done), and configure iSCSI volumes.

Here are my volumes:

encrypted volume sda1_crypt
lvm vg lv root
lvm vg lv swap_1
scsi (sda)
  1 primary
  2 logical

Again, how can I just install on an existing partition, and not format?

---

### Post by Lars Noodén on 2014-03-06
If you don't have a separate /home partition then the safest solution is to boot to the live disc image and recover your files to some backup storage.  

Then do a fresh install, but this time make sure to have a separate /home partition.  You won't always need a separate /home but having it is insurance against situations where you do need to re-install and keep your files intact.  

If you do have a separate /home, do the backup anyway from the live image, and then do the re-install.  But when it gets to the partitioning stage, select "something else" and identify your /home partition but do not mark it for formatting.

---

### Post by vanadium on 2014-03-06
With the option "do something else", you can determine yourself which partitions should be used for what, and whether they should be formatted or not. However, the suggestion of Lars is by far preferred to obtain a solid, clean system to start with, rather than trying to overwrite an existing install that is corrupt anyway.

---

### Post by gavannon on 2014-03-06
Okay I've solved it. To help others:

1. I gave up on doing a new install. I had to get my files off, and wouldn't trust any of the warnings like "this will format ___". Too risky.

2. I instead downloaded Ubuntu desktop, which includes the "LiveCD". Lets you run near-full working Ubuntu from the CD.

3. Once in, I was able to decrypt my partitions using trial and error of these commands:

[INDENT]```
sudo cryptsetup luksOpen /dev/sda1 encrypted_volume

```

Then I tried to mount it:

```
sudo mkdir /media/my_device
sudo mount /dev/mapper/encrypted_volume /media/my_device
```

(That didn't work. It said it was already mounted or mapped.)

So then I tired:

```
sudo udisksctl unlock -b /dev/sda1
```

This mounted my encrypted drive into /media/ubuntu/____crazylongname____

Inside that crazylongname folder was my encrypted files![/INDENT]

4. Permissions from my previous install didn't allow access to some folders. So I used:
```
sudo chmod o+rw -R foldername
```
and even
```
sudo chown root:root -R foldername
```
for each that I couldn't get into. Still no luck for either. Turns out, I had to be super user.

5. Changed to super user
```
sudo -s
```
NOW I can get into my encrypted folders, and copy them off to an external HD.

6. Launched file explorer as sudo for easy GUI copying to external HD!
```
sudo nautilus
```

7. Celebrate, do full install of latest Ubuntu.

---

