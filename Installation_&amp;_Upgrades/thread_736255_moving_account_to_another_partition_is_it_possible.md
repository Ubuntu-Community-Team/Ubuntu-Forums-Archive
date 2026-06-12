---
title: "moving account to another partition? is it possible?"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by robgr85 on 2008-03-26
Hi!

Got some issue with my ubuntu. Long time ago, while instalation process I've chosen hda3 for my 'home' account partition. There are 4 user accounts on hda3 now. I want change it now.

Is it possible to transfer it to other partition without reinstalling the system/ damaging existing accounts? How?

Is it possible to set different partition for only one of accounts without reinstalling/damaging existing accounts? How?

Cheers.
Rob

---

### Post by Ptero-4 on 2008-03-26
You can change your accounts from one partition to another by copying the contents of the home section of your filesystem using these command
```

sudo cp -a /home/* <newpartitionmountpoint>
(note that you may want to clean up your old partition after you're done copying it to the new one)

```
you can also (not recommended) copy individual accounts to special partitions with
```

sudo cp -a /home/<username>/* <newpartitionmountpoint>

```
After that you'll need to add or update the /etc/fstab file like this
```

for new home partition
/dev/<yourhomepartition> /home <fs> defaults 0 0
for individual user account
/dev/<userpartition> /home/<username> <fs> defaults 0 0

```

---

### Post by matt_heys on 2008-03-26
> **Ptero-4 said:**
> 
After that you'll need to add or update the /etc/fstab file like this
```

for new home partition
/dev/<yourhomepartition> /home <fs> defaults 0 0
for individual user account
/dev/<userpartition> /home/<username> <fs> defaults 0 0

```


I think Ubuntu uses UUID's in the fstab, in which case you can run 
```

/lib/udev/vol_id -u /dev/<yourhomepartition>

```
to get the UUID

It might not matter though.

---

### Post by Ptero-4 on 2008-03-29
You can still use the old /dev/hd* method in your /etc/fstab, no need for getting UUID's

---

### Post by robgr85 on 2008-03-31
there is still some issue with that topic.

before, the home directory was on partition with my os.

i succesfully moved it to the new partition,

now I would like to delete old /home directory, but it /home reffers to new one. How to find the old home dir?

Cheers,
Robert

---

### Post by vanadium on 2008-03-31
In order to move a home partition or a user partition, I recommend using the copy commands referred to on various sites, e.g. [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)
because
> 
Since the “/home” directory will have hardlinks, softlinks, files and nested directories, a regular copy (cp) may not do the job completely.


Indeed, cp -a might work in many cases, but is not guaranteed to work always.

---

### Post by Ptero-4 on 2008-04-03
> **robgr85 said:**
> there is still some issue with that topic.

before, the home directory was on partition with my os.

i succesfully moved it to the new partition,

now I would like to delete old /home directory, but it /home reffers to new one. How to find the old home dir?

Cheers,
Robert

To do that just format your old home partition (the one that you copied everything from). It doesn't show up in the /home folder because that folder is actually a mount point that used to point to your old partition but now points to the new one.

---

### Post by robgr85 on 2008-04-04
I managed to delete files of old home.

my account works fine on new partition, but another user got the message after login attempt:

> 
Could not start kstartupconfig. Check your installation.


do anyone know what to do now?

---

### Post by phenest on 2008-04-05
I'm having problems copying the files over correctly.
```
steve@precision:/home$ find . -depth -print0 | cpio –null –sparse -pvd /media/disk-5/
cpio: You must specify one of -oipt options.
Try `cpio --help' or `cpio --usage' for more information.

```
If I use:
```
cp -a steve/ /media/disk-5/
```
...I end up with unreadable folders and files, i.e. I don't have the correct permissions.

Can someone please advise me on the correct way to do this.

---

