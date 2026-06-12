---
title: "[SOLVED] Adding another HD"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by easy_target on 2008-07-01
Hi!

Back to the forums again. I have a machine that had only a 40Gb HD with Ubuntu Hardy installed. Unfortunately I ran out of space these days and ended up buying a 250Gb HD. Now, how can I add that to the system in a way that my home partition will be on the second (bigger) HD without having to do a fresh install? I saw something about LVM's [here]("https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall") but I have no idea where to start. Any help is appreciated.

Thanks in advance.

PS: Using Gparted I couldn't find an option to format my second HD to linux-LVM.

---

### Post by dominiquec on 2008-07-01
You can mount your bigger HD as /home in /etc/fstab.  

Back up all your existing /home data first, or better yet, copy it to the new hard disk.  

Edit your /etc/fstab and add a line similar to the following (just copied from mine, so yours will be different):

```
UUID=8e07c0b8-5380-473f-bcbf-bed85b93d168 /home ext3 relatime 0  2
```

You can determine the UUID of your disk by looking it up in /dev/disk/by-uuid.  Just do an ls -l.

Then, reboot (or type mount -a).

---

### Post by logos34 on 2008-07-02
You don't need to use LVM--just add it as a separate volume, partitioned and formatted ext3.

I highly encourage you to follow [this guide.]("http://www.psychocats.net/ubuntu/separatehome")  

But do use the UUID in fstab, as dominiqueq said, instead of '/dev/drive' format

---

### Post by easy_target on 2008-07-03
Okay. I managed to mount the home directory on the second HD but I am having problems with permissions. I can only log in failsafe terminal. Maybe I put something wrong in fstab?

Here is my fstab's contents:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=4bba2707-99e2-470e-b16a-35fcc0f3da5e / ext3    defaults,errors=remount-ro 0 1
# /dev/sdb1
UUID=74cc5f5b-9d0a-401c-87e3-1f6d945c13ec /home	ext3 relatime 1 1
# /dev/hda5
UUID=7edbb909-4fb7-465f-96ed-53340bed11ed none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0 0
```

Any ideas?

---

### Post by logos34 on 2008-07-03
> **easy_target said:**
> ```

# /dev/sdb1
UUID=74cc5f5b-9d0a-401c-87e3-1f6d945c13ec /home    ext3 relatime 1 1

```Any ideas?

I believe you want:

>  # /dev/sdb1
UUID=74cc5f5b-9d0a-401c-87e3-1f6d945c13ec /home    ext3 relatime [COLOR=Red]**0 2**[/COLOR]

---

### Post by easy_target on 2008-07-03
Oh I see. And what does that mean?
Learning...

thanks for the prompt reply

---

### Post by logos34 on 2008-07-03
> **< [B]5th and 6th columns: Dump and fsck options** >[/B]

 		Dump and, uh, *what* options? Well, dump is a backup utility and fsck is a filesystem check utility. I won't discuss them in great length here (they would both need their own tuXfile), but I'll mention them, because otherwise you'd spend the rest of the day wondering what on God's green Earth do these things mean.
 		The 5th column in /etc/fstab is the dump option. Dump checks it and uses the number to decide if a filesystem should be backed up. If it's zero, dump will ignore that filesystem. If you take a look at the example fstab, you'll notice that the 5th column is zero in most cases.
 		The 6th column is a fsck option. fsck looks at the number in the 6th column to determine in which order the filesystems should be checked. If it's zero, fsck won't check the filesystem.


Only / (root) should be '1'--it gets priority with fsck.  Any other linux partitions should be '2'.  (windows '0' because linux can't check ntfs and vfat)

---

### Post by easy_target on 2008-07-03
Okay. Changed the parameter in fstab. 
However, whenever I log into gnome I receive the following message:

"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. Files should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

What did I do wrong? Is it something with having to copy my home directory to the new hard drive partition as a super user?

---

### Post by easy_target on 2008-07-04
Okay, found the answer on [this thread]("http://ubuntuforums.org/showthread.php?t=371052&highlight=%24HOME%2F.dmrc").  Apparently I used sudo instead of using gksudo to work with nautilus while copying my home directory to my new hard drive. With that my permissions became all messed up. 
Good news is that you can change them back to their original state with these commands:

```
sudo chmod 644 /home/your_user_name_here/.dmrc
sudo chown your_user_name_here /home/your_user_name_here/.dmrc
sudo chmod -R 755 /home/your_user_name_here
sudo chown -R your_user_name_here /home/your_user_name_here
```

Thanks to ricardisimo, wert 613, dominiquec and logos34 for the answers. I will mark this as solved.

---

