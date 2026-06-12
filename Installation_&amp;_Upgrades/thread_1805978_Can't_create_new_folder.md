---
title: "Can't create new folder"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by lwalper on 2011-07-16
I've just used gparted to create a new primary partition formatted with ext4 on my primary drive (drive 0). That all seems OK, but ...


I don't seem to be able to work in the new partition. When I right click in the area the "add new folder" option is greyed out" and when I try to drag a file from the original partiton to the new one I get 

Error opening file '/media/1c1eba21-fc77-45f5-86f2-2c9fa22e0031/1001.MP3': Permission denied

If I try to drag a folder I get

The folder "Music" cannot be copied because you do not have permissions to create it in the destination.

What gives??

---

### Post by cipherboy_loc on 2011-07-16
If you are using this drive between different computers with different users and/or user ids, that is your problem. To fix it, navigate to the terminal (Applications -> Accessories -> Terminal) on either of the computers, then type (or copy and paste) the following:

```

sudo chmod 666 -R /media/1c1eba21-fc77-45f5-86f2-2c9fa22e0031

```which will require you to enter your password (after this is done and you see the prompt again, you can exit the terminal by typing exit). What this does is change the permissions on all the files to 666 or RW for everybody (user, group, world). This should allow you to create files from both computers. You might also need to run this multiple times after you create new files.

Edit: Notice: I did not chmod 777 as that would allow execution of files. This may or may not be desired, but this is just a thin safety precaution. 

Cipherboy

---

### Post by lwalper on 2011-07-17
OK, thanks, I'll try that.

No, not using two computers just two partitions on the same drive. With my last OS update to 11.04 I lost everything on the large single primary partition so I'm just partitioning off a small (20Gb) space for the OS and a separate partition for user data. I just need full permissions (which would be persistant and I won't ever need to fool with again) for that new partition.

I'll try that 666 option. Any executables will be on the main OS partition, so that shouldn't be an issue.

---

### Post by lwalper on 2011-07-17
I'm in the root of the OS partition and tried that command and came up with

chmod: cannot access `/media/1c1eba21-fc77-45f5-86f2-2c9fa22e0031': No such file or directory

Do I need to be in the "D" drive? (I know that's Windoze, but what do you call it?) to execute that command?

---

### Post by lwalper on 2011-07-17
I note that when I right click on the newly created partition icon that I can open a dialog showing drive properties. One of the tabs is labeled Permissions. Is it possible to change permissions here?

---

### Post by coffeecat on 2011-07-17
> **lwalper said:**
> I note that when I right click on the newly created partition icon that I can open a dialog showing drive properties. One of the tabs is labeled Permissions. Is it possible to change permissions here?

No - you would need root privileges.

> **lwalper said:**
> I'm in the root of the OS partition and tried that command and came up with

chmod: cannot access `/media/1c1eba21-fc77-45f5-86f2-2c9fa22e0031': No such file or directory

That means that you hadn't mounted the new partition. It's UUID is 1c1eba21-fc77-45f5-86f2-2c9fa22e0031, which is why the systen is creating a folder named 1c1eba21-fc77-45f5-86f2-2c9fa22e0031 in /media as the mountpoint. Click on the partition in the left pane of Nautilus to mount it and then run the chmod command. However, I am going to make two amendments to cipherboy_loc's code. First, you do not need the -R recursive option if you have not copied any files to the new partition yet. Also, you **do** need to set either 777 or 770 permissions on the root of the filesystem. I can understand cipherboy_loc's caution over setting the executable bit, but you do need this because the root of the filesystem is akin to a directory and you need the executable bit on a directory to have access. The executable bit in permissions is different for folders and files. Run this:

```
sudo chmod 777 /media/1c1eba21-fc77-45f5-86f2-2c9fa22e0031
```

... after you have mounted the partition. Note the absence of the -R option. This has the curious effect of changing the permissions on the partition filesystem and not on the /media/1c1eba21-fc77-45f5-86f2-2c9fa22e0031 folder. You (or any ordinary user) will then be able to create folders and write files to the partition.

---

### Post by lwalper on 2011-07-17
OK, thanks everyone for the efforts. I am still unable to access the partition. Gparted labels it as /dev/sda3 and says that it is unmounted and that it is "Unable to find mount point; Unable to read contents of this file system!" and tells me that a "list of software packages is required for ext4 file system support: e2fsprogsv1.41+." Is that just for gparted to work properly? or is that something I need to be able to read the partition at all? 

The file manager ?Nautilus? gives me the option to "unmount"  and there is currently an icon for the partition on the desktop so I'm assuming the partition is mounted, but I still cannot access the partition.

I then ran
```
sudo chmod 777 /media/1c1eba21-fc77-45f5-86f2-2c9fa22e0031
```
which tells me
```
chmod: cannot access `/media/1c1eba21-fc77-45f5-86f2-2c9fa22e0031': No such file or directory
```

I also tried
```
mount /dev/sda3
```
which tells me
```
mount: can't find /dev/sda3 in /etc/fstab or /etc/mtab
```
As I was going along I labeled the partition "User Data"
```
sudo mount /dev/User Data
```
returns
```
mount: mount point Data does not exist
```
Does the label need to be a single word without spaces? It does not seem to have read the whole label? I'm at a point where I can easily reformat and rename the partition?

---

### Post by lwalper on 2011-07-17
OK, that did it. I reformatted the partition, giving it a single word label "data" -- the format went off without a hitch, automatically mounted the partition, and now I can drag files to the partition -- without running anything else in terminal.

Looks like it's fixed. Thanks all!!

---

### Post by coffeecat on 2011-07-17
> **lwalper said:**
> OK, that did it. I reformatted the partition, giving it a single word label "data" -- the format went off without a hitch, automatically mounted the partition, and now I can drag files to the partition -- without running anything else in terminal.

Looks like it's fixed. Thanks all!!

Hmm. If you can drag and drop files into the reformatted partition without running a chmod command, you must have formatted it NTFS or FAT32.

Unless you reformatted it ext3/4 in Disk Utility and ticked the "take ownership" tickbox.

---

### Post by lwalper on 2011-07-18
No, I just checked that -- it's ext3/4. If I ticked the "take ownership" box I sure don't remember doing it. Maybe I did??

---

### Post by coffeecat on 2011-07-18
> **lwalper said:**
> No, I just checked that -- it's ext3/4. If I ticked the "take ownership" box I sure don't remember doing it. Maybe I did??

The "take ownership" box in Disk Utility does the equivalent of a "sudo chown yourusername:yourusergroup" on the root of the new filesystem. Which has the effect that you were wanting in that you will be able to write to the partition and create folders. What the "sudo chmod 777" does is to give permissions to everyone to do the same so that if you create other accounts in Ubuntu, those accounts will have access to the partition as well.

By the way, the reason the chmod command gave you "chmod: cannot access `/media/1c1eba21-fc77-45f5-86f2-2c9fa22e0031': No such file or directory" before is because:

1 - You hadn't mounted the partition.

Or...

2 - You had manually mounted it to a mountpoint other than /media/1c1eba21-fc77-45f5-86f2-2c9fa22e0031.

Or...

3 - You had created a partition label subsequent to your first post so that the system would have created a mountpoint /media/*label* where *label* was the partition label.

You didn't have to reformat the partition at all. We simply needed to investigate why the partition hadn't been mounted to /media/1c1eba21-fc77-45f5-86f2-2c9fa22e0031. Anyway, the new filesystem will have a different UUID now so you can forget the "1c1eba21-fc77-45f5-86f2-2c9fa22e0031" UUID.

---

