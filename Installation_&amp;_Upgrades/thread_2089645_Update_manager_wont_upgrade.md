---
title: "Update manager wont upgrade"
date: 2012-11-29
forum: Installation &amp; Upgrades
---

### Post by stockpimp on 2012-11-29
I am trying to upgrade from an older version of Ubuntu but update manager will not let me upgrade.  I get the following error;

W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

I am a novice so please go easy!  Thank-you for your help!

---

### Post by wojox on 2012-11-29
You would need to switch repo's like here [How to install software or upgrade from old unsupported release?]("http://askubuntu.com/a/91821/2973")

---

### Post by stockpimp on 2012-11-29
K.  I would like to upgrade to a current supported format (as suggested in the post) but I don't seem to be able to get to stage one as it were as i keep getting this error.  Do i need to go to the old repo's and get the missing files and upgrade step by step or is there a way to go from a to z and force an update to a current version?  Thank-you.

---

### Post by stockpimp on 2012-11-29
i also tried the above line /etc/apt/sources.list and I get a permission denied error in terminal even after i login etc.?

xxxxxxxxx@D2030:~$ /etc/apt/sources.list
-bash: /etc/apt/sources.list: Permission denied
xxxxxxxxx@D2030:~$

---

### Post by snowpine on 2012-11-29
> **stockpimp said:**
> i also tried the above line /etc/apt/sources.list and I get a permission denied error in terminal even after i login etc.?

xxxxxxxxx@D2030:~$ /etc/apt/sources.list
-bash: /etc/apt/sources.list: Permission denied
xxxxxxxxx@D2030:~$

This is a file you need to edit with your favorite text editor (gedit, nano, etc.) using 'sudo' rights. For example:

```
gksu gedit /etc/apt/sources.list
```

or:

```
sudo nano /etc/apt/sources.list
```

The full process is documented here: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

If these are new concepts to you, then you may be better off backing up your documents/files and doing a fresh reinstall of the new release.

---

### Post by stockpimp on 2012-11-29
> **snowpine said:**
> This is a file you need to edit with your favorite text editor (gedit, nano, etc.) using 'sudo' rights. For example:

```
gksu gedit /etc/apt/sources.list
```

or:

```
sudo nano /etc/apt/sources.list
```

The full process is documented here: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

If these are new concepts to you, then you may be better off backing up your documents/files and doing a fresh reinstall of the new release.

I was thinking the same however i don't have anything approaching enough space to back my files up on.  i have one drive that's 1tb and a second that's 750 gb.  the 750 drive is 93% full and the 1tb drive is 40% full.  it's all media files so compression would be a no go to try and save space etc.  i think I'm going to have to fumble my way through this update but really have NO idea what I'm doing.

---

### Post by snowpine on 2012-11-29
> **stockpimp said:**
>  but really have NO idea what I'm doing.

All the more reason to have a full backup of your important data! Hard drive failure, power surge, buggy software, user error, accident, theft, and it's all gone. External hard drives are really cheap these days relative to the value of a data backup.

On your next install, you may wish to create a separate /home partition (if you haven't already done so, which can be verified with 'df -h'). This means your user data is separate from the system files, so if you understand partitioning concepts, you can reinstall Ubuntu without erasing your personal documents/files. (But this is not a substitute for a true backup plan.) Here's a how-to: [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

Just some friendly advice. :)

---

### Post by stockpimp on 2012-11-29
> **snowpine said:**
> All the more reason to have a full backup of your important data! Hard drive failure, power surge, buggy software, user error, accident, theft, and it's all gone. External hard drives are really cheap these days relative to the value of a data backup.

On your next install, you may wish to create a separate /home partition (if you haven't already done so, which can be verified with 'df -h'). This means your user data is separate from the system files, so if you understand partitioning concepts, you can reinstall Ubuntu without erasing your personal documents/files. (But this is not a substitute for a true backup plan.) Here's a how-to: [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

Just some friendly advice. :)

understood.  I set it up with the master drive being the 750 gb drive and added the 1tb later as i ran out of room.  i think i may be able to dump some of the unwanted / used files if i went on a purging binge.  this might allow me to fit / move all files on to the 1 tb drive.  i think at that point i could yank the drive and reload the os on the 750 gb drive?  sound functional?

---

