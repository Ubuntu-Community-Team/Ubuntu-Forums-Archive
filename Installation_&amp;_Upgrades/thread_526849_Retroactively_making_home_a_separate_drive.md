---
title: "Retroactively making /home a separate drive"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by dbsoundman on 2007-08-16
I just successfully installed Ubuntu 6.10 on my laptop. I partitioned the drives such that I could dual boot with Windows XP, and have a common file area. However, somehow in the setup of Ubuntu, I managed to not set /home to my "storage" partition, number 4. How can I do this now that everything is in place?

BTW: I'm assuming that making a partition /home in Linux won't make it inaccessable in Windows XP. The partition is formatted as FAT32, so there shouldn't be problems there from what I understand.

Thanks,
Dan

---

### Post by jdong on 2007-08-16
You should not make your /home partition on FAT32, as FAT32 does not properly retain UNIX permissions bits necessary for proper operation of some software (that ensure certain levels of permissions before allowing it to continue)

I guarantee if you do this, you'll reach a headache some day in the future.

---

### Post by dbsoundman on 2007-08-16
Oh. I was under the impression that I could do this safely. So essentially I can either use a really strange filesystem in this computer (which I don't want to do), or I can reformat the storage drive. I'm thinking that's the key, but I can't remember, is there some way for Windows to read ext3 (which is what I'm guessing I'll be reformatting to)?

-Dan

---

### Post by merlinus on 2007-08-16
[http://www.fs-driver.org/](http://www.fs-driver.org/)

-merlin

---

### Post by dbsoundman on 2007-08-16
All right, so once I reformat that volume to ext2, how do I make it the /home directory? And I still assume that making it /home in Ubuntu won't affect how Windows approaches it, correct?

-Dan

---

### Post by merlinus on 2007-08-16
You can format it as ext3.  fs-driver will allow windows to read-write to it.

Here is info about making a separate /home partition after install:

[SIZE=4][/SIZE]http://www.psychocats.net/ubuntu/separatehome

-merlin

---

### Post by dbsoundman on 2007-08-16
Well, I just did what the tutorial for making a /home directory told me to do, and now my Ubuntu won't start. It says that /home/dan doesn't actually exist. I did edit the fstab config file though like it says, but I don't think I did it right. My first question is how can I fix this? I tried doing what is outlined on the bottom of that page, and that didn't work. I suppose I could just reinstall Ubuntu; it would just mean I'd have to get all the work I did last night done again :(.

When I do finally get this right, when I get to the point of editing fstab, (assuming I don't just reinstall), do I really just add that line, or am I supposed to edit something? The drive I needed (sda4) was already listed there in fstab, but with all these wrong parameters; it still said it was a FAT volume (which it isn't anymore), things like that. I tried patching in what the page said but obviously I deleted something important there and for some reason that file isn't backed up. Help?

-Dan

---

### Post by jdong on 2007-08-16
Can you get in to your root partition via a LiveCD or something and paste us your /etc/fstab file? You probably just made a simple mistake we'd be able to point out.

---

### Post by merlinus on 2007-08-16
Post results of:

```

sudo fdisk -l
cat /etc/fstab

```

-merlin

---

### Post by dbsoundman on 2007-08-16
I haven't yet figured out how to post my fstab file because I first have to figure out how to mount the sda6 drive to get to it, I think.

I did run cat /etc/fstab, and these were the results:
```
ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
```

Somehow, I think this is telling the results for the Live CD and not the actual harddrive...how do I mount and navigate into the right drive (sda6)?

-Dan

UPDATE: When I logged in in a failsafe terminal in Ubuntu I was able to run cat /etc/fstab and I saw that on my main Linux volume (sda6) it said "default,error". Unfortunately I could not figure out how to write this file to disk (though I tried) so I can't put it on this computer to post it here...I tried opening it in nano and saving the file to my "common" file drive between windows and linux, but it appears that it didn't work, because I don't see it in windows. I do see, though, that somewhere in the whole process/mess, I created a home_backup folder, which is identical to the "dan" folder that I see here in windows on that common drive. However, I don't think that the /etc folder is in there.

---

### Post by merlinus on 2007-08-16
You are correct.  It is /etc/fstab from the live cd.

Here is mounting info:

[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_a_reiserfs_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_a_reiserfs_filesystem)

-merlin

---

