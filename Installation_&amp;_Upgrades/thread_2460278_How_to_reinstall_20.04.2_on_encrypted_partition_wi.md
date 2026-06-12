---
title: "How to reinstall 20.04.2 on encrypted partition without data loss ?"
date: 2021-04-06
forum: Installation &amp; Upgrades
---

### Post by thealpman on 2021-04-06
Hello,
I have a serious problem with my system, with no solution so far : [https://ubuntuforums.org/showthread.php?t=2459816](https://ubuntuforums.org/showthread.php?t=2459816)
I'd like to reinstall Ubuntu without data/program loss.
The thing is I have one LVM encrypted partition with system & data and I don't have the option "reinstall Ubuntu" when I launch a live session.

[[IMG]https://i.ibb.co/hyQFzhS/Reinstall-Ubuntu.jpg[/IMG]]("https://ibb.co/hyQFzhS")

Is there a way to do this ?

Thank you !

---

### Post by yancek on 2021-04-06
Is all your data on one partition or do you have separate partitions for the system and personal data?

You're not likely to find a 'reinstall' option with any operating system.  The standard method is to simply install the OS again to the same partition and select to NOT format that partition  I you have separate data partition do not format those either.  I've done this successfully but I don't use LVM so I don't know what the results would be.  I would expect it to work and your Ubuntu would be back to the original install.

---

### Post by TheFu on 2021-04-06
Be 100% certain you have backups that can be restored for all data and settings you can't lose. Whenever using encryption, it is critical to have excellent backups. Just 1 tiny logical error or a physical error in the storage can be disastrous for all the data inside the encrypted container.

I've never done this.  I use LVM on almost all my systems and encrypt the laptops.  If I were attempting this, I'd choose the "do something else" option, unlock the LUKS container (manually if necessary), then chose each LV for the specific mount point.  As yancek suggests, don't format.  I have doubts that the crypttab and grub will be setup correctly to prompt to open the LUKS container pre-boot, but you might get lucky.

With great backups and since the restore process begins by doing a fresh, minimal install, I've never had to worry about this technique. Takes about 30 minutes to have everything back for the laptop, installed on a completely different system, with encryption and LVM - handled by the normal Ubuntu Installer - just check "use encryption + LVM". Solves all sorts of compatibility problems and allows completely changing the underlying storage setup without really changing the other settings or data or 99% of the installed programs.

---

### Post by thealpman on 2021-04-06
Thank you for your replies !
@yancek : I only have one partition for system & data. So I'm afraid installing Ubuntu again would erase my data (and all my programs).
@TheFu : I have periodical GRsync backups of all my data (but not my system). How can I unlock the LUKS container manually (with live sessions, I usually unlock it after, when I access the files) ? Maybe it's why I don't get this "reinstall option" ? This is all new to me (I don't follow everything you say in the last paragraph), are there tutorials explaining it ?
Thanks again

---

### Post by TheFu on 2021-04-06
> **thealpman said:**
>  
@TheFu : I have periodical GRsync backups of all my data (but not my system). How can I unlock the LUKS container manually (with live sessions, I usually unlock it after, when I access the files) ? Maybe it's why I don't get this "reinstall option" ? This is all new to me (I don't follow everything you say in the last paragraph), are there tutorials explaining it ?

**cryptsetup** can unlock LUKS encrypted containers.  You'll need to know the "name" for this command.  Look that up and write it down carefully BEFORE you need it.  cryptsetup options have changed slightly the last few releases, so check out the manpage to get a feel for the options.  You're looking for "open" or "Open" or "LUKSOpen" 
**vgchange -ay** will "activate" any inactive LVM VGs. These aren't available until after the LUKS container is unlocked.

A very useful command: **lsblk -e 7 -o name,size,type,fstype,mountpoint**
Not tutorials, but long posts in these forums.
BTW, rsync isn't a good backup tool alone. There are many better options.  Most are based on rsync, but add the stuff needed to be a good backup tool.

**Backup Methods**
[LIST]
[*][https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)
[*][https://popey.com/blog/2020/12/straightforward-linux-backups-with-rsnapshot/](https://popey.com/blog/2020/12/straightforward-linux-backups-with-rsnapshot/)
[*][https://www.cyberciti.biz/faq/linux-unix-apple-osx-bsd-rsync-copy-hard-links/](https://www.cyberciti.biz/faq/linux-unix-apple-osx-bsd-rsync-copy-hard-links/) 
[/LIST]
**Restore Methods**
[LIST]
[*][https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
[/LIST]
Some Linux skills are required.  This is deep stuff, so have some coffee and be ready to think.

---

### Post by ActionParsnip on 2021-04-06
Make sure your backups are up to date if you want to avoid data loss. Make a final FULL backup then you know your data is safe.

---

### Post by thealpman on 2021-04-09
In the end, I reinstalled the system from scratch. (Which did not solve my initial problem..)

Thank you for your help !

---

### Post by yancek on 2021-04-09
>  I only have one partition for system & data. So I'm afraid  installing Ubuntu again would erase my data (and all my programs). 

No, it should not if you do not select to format the partition.  I just did this with another Linux OS on which I had dozens of data files as well as various software I had installed before having problems and when I reinstalled NOT formatting the / (root filesystem) partition, all my personal data files as well as the software I had installed were still available.  I don't know what difference encryption would make if any.  Moot point since you have reinstalled.

---

