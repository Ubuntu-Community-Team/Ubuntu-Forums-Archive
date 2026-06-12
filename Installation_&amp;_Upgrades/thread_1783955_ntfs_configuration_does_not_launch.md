---
title: "ntfs configuration does not launch"
date: 2011-06-16
forum: Installation &amp; Upgrades
---

### Post by asad.bukhari on 2011-06-16
I am new to ubuntu.

I have partitioned my hard drive into three parts: 1 lean section for windows 7 (50 gb), another section for ubuntu 11.04 (50 gb) and one final massive section for 'storage' (360-ish gb).  I have been following the following guide to accomplish this process:

[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

I am lost in the final stages of the process.  The article says that:
[COLOR=Purple]
[/COLOR][COLOR=Purple]"Ubuntu won't "mount," or make available, your Windows 7 and Storage  drives on boot-up, however, and we at least want constant access to the  Storage drive. To fix that, head to Software Sources in the  System->Administration menu. From there go to Applications, then the  Ubuntu Software Center at the bottom. Under the "Ubuntu Software" and  "Updates" sections, add a check to the un-checked sources, like  Restricted, Multiverse, Proposed, and Backports. Hit "Close," and agree  to Reload your software sources."[/COLOR]

I completed this but I did not get the "reload your software sources" option.  Then the article says:

[COLOR=Purple]"Finally! Head to the Applications menu and pick the Ubuntu Software  Center. In there, search for "ntfs-config," and double-click on the NTFS  Configuration Tool that's the first result. Install it, then close the  Software Center. If you've got the "Storage" or Windows 7 partitions  mounted, head to any location in Places and then click the eject icon  next to those drives in the left-hand sidebar. Now head to the  System->Administration menu and pick the NTFS Configuration Tool."[/COLOR]

[COLOR=Red]I was able to install NTFS Config.  However, when I click on it and enter my administrative password, it does not launch.[/COLOR]

I do not know how to get around this, I did some research online but was not able to find any solutions.
I do not fully understand what ntfs config will accomplish, but I think it has something to do with accessibility to the storage partition from both windows 7 AND linux.

The article says:

[COLOR=Purple]"You'll see a few partitions listed, likely as /dev/sda1, /dev/sda2, and the like. If you only want your storage drive, it should be listed as /dev/sda3  or something similar--just not the first or second options. Check the  box for "Add," click in the "Mount point" column to give it a name  (Storage, perhaps?), and hit "Apply." Check both boxes on the next  window to allow read/write access, and hit OK, and you're done. Now the  drive with all your stuff is accessible to Windows and Linux at all  times."[/COLOR]

I would really appreciate it if someone could help me with this issue and tell me if this last phase of the dual-booting/partitioning process in necessary.  I am somewhat computer-savvy but a complete child when it comes to ubuntu.

This is my first post on ubuntu forums :p

---

### Post by Morbius1 on 2011-06-16
If I read this correctly you have already installed Ubuntu and now you want to auto mount your other partitions. If this is correct please post the output of the following commands:
```
sudo blkid -c /dev/null
```
```
cat /etc/fstab
```
```
mount
```

---

### Post by asad.bukhari on 2011-06-16
I apologize, I am not very familiar with auto-mounting.  I was mostly following the article.

What does auto mounting accomplish?

Where do I enter this code?  In something called the terminal?  Is it similar to command prompt in windows?

---

### Post by Morbius1 on 2011-06-16
>  What does auto mounting accomplish?When you boot into Ubuntu all the other partitions will automatically be available to you.
>  Where do I enter this code?  In something called the terminal?  Is it similar to command prompt in windows?     Yes. In the terminal. Then just copy and paste to your next post.

---

### Post by asad.bukhari on 2011-06-16
I entered the codes and this was the output:

```
 asad@Clyde:~$ sudo blkid - c /dev/null
[sudo] password for asad: 
Sorry, try again.
[sudo] password for asad: 
asad@Clyde:~$ sudo blkid - c /dev/null

```

```

asad@Clyde:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=40f9dbdf-a593-4cef-860e-9a69eba7ac8a /               ext4    errors=remount-ro 0       1

```

```

asad@Clyde:~$ mount
/dev/sda3 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)

```

---

### Post by Morbius1 on 2011-06-16
There's no space between the "-" and the "c":
```
sudo blkid -c /dev/null
```

---

### Post by asad.bukhari on 2011-06-16
I entered it the correct way:

```

asad@Clyde:~$ sudo blkid -c /dev/null
[sudo] password for asad: 
/dev/sda1: LABEL="System Reserved" UUID="0E6227A162278D11" TYPE="ntfs" 
/dev/sda2: UUID="8A58294458292FFD" TYPE="ntfs" 
/dev/sda3: UUID="40f9dbdf-a593-4cef-860e-9a69eba7ac8a" TYPE="ext4" 
/dev/sda4: LABEL="Storage" UUID="26B8915F72FB89C3" TYPE="ntfs" 
asad@Clyde:~$ 

```

Must I enter the other codes now, again?

---

### Post by Morbius1 on 2011-06-16
Edit fstab as root:
```
gksu gedit /etc/fstab
```Add the following line to the end of the file:
```
 UUID=26B8915F72FB89C3 /media/Storage ntfs defaults,uid=1000 0 0
```Save the file, exit gedit, and you will find yourself back in the terminal. 

Now unmount the currently mounted partition:
```
 sudo umount /media/Storage
```Create a permanent mount point at the old location:
```
 sudo mkdir /media/Storage
```Run the following command to test for errors ( post them if there are any ) and mount the partition:
```
 sudo mount -a
```

---

### Post by asad.bukhari on 2011-06-16
Alright, I followed your directions.  This is what my terminal looks like:

```
asad@Clyde:~$ gksu gedit /etc/fstab

(gedit:3009): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:3009): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.DBKAXV': No such file or directory

(gedit:3009): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:3009): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.JENSWV': No such file or directory

(gedit:3009): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
asad@Clyde:~$  sudo umount /media/Storage
asad@Clyde:~$  sudo mkdir /media/Storage
asad@Clyde:~$ sudo mount -a

```

Can we confirm that the other partitions are mounted?

---

### Post by Morbius1 on 2011-06-16
I'll have to do some searching for the error message but did gedit open and did you add the line to fstab?

If you di then just go to /media/Storage and see if you can access the directory.

---

### Post by asad.bukhari on 2011-06-16
> 
I'll have to do some searching for the error message but did gedit open and did you add the line to fstab?


Yes I did.  It opened and I pasted the line at the end of the file.  You did not want me to replace anything with the line, just add it at the end, right?

> 
If you di then just go to /media/Storage and see if you can access the directory.


I'm very new to ubuntu.  Can you simplify that?

---

### Post by Morbius1 on 2011-06-16
Bring up the terminal again and type:
```
nautilus /media/Storage
```
Does it contain what you want it to contain?

---

### Post by asad.bukhari on 2011-06-16
Yes it does :D

---

### Post by asad.bukhari on 2011-06-16
Am I all set?

---

### Post by Morbius1 on 2011-06-16
OK, all that we've done is replace the steps in the HowTo you are following that pertain to ntfs-config. The author must not know that ntfs-cong isn't maintained anymore and it has very bad side affects sometimes. To answer your question, yes, the next time you boot the storage partition will be located at /media/Storage.

A piece of advice as you continue your Linux education: Don't use HowTo's that you find on someone's own webpage. It's better to use HowTo's you find in forums. If I say something stupid ( and lord knows I have ) 26 people will jump in and correct me. There's no guarantee that a HowTO in this form will be better or more accurate but at least there is some level of peer review.

---

### Post by asad.bukhari on 2011-06-16
Understood.  I appreciate your help.  You made a great first impression on a new linux user on behalf of the ubuntu community.  I am doing further research on how to use ubuntu now.

Thanks once again :D

---

