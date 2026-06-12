---
title: "Installation Failure: Lost Windows boot"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by kitsch76 on 2007-01-06
Hello All,

Today I tried installing Ubuntu for the first time using the Live CD I just received in the mail. I tried twice to installing using the Live CD to create the partition but both times got an error saying "Failed to create enough memory"

Third attempt I tried to Manually manage the partitions. The Windows partition was 27GB and I left that alone. I added two partitions. One of 8GB and one of 512MB (for the Swap), when I hit the forward button and Ubuntu asked me if I wanted to make these changes take effect I said yes.

I received an error, and the result is that now I have the following partitions:

/dev/hda2  unknown 0.00 MB      ----    ----
/dev/hda1  unknown 27.95 GB     ----    ----     boot

When I went to reboot I could not boot windows XP and it gave the error that it "Could not start or find operating system"

When I went to reboot using the LiveCD with Ubuntu it failed to load completely. I restarted with Safe Mode and it loaded.


My fear is that the file system for windows is completely botched up.  I really don't care about that.  My problem is that I have some data (photos) that I want to recover and haven't a clue about how to get to them.  

The PC is a laptop so removing the hard drive to put into another PC is harder.

If anyone has any tips to get my Windows Data back, I would be truly greatful.

I tried the commands that were suggested in another post.

The Fdisk command gives nothing
The mslist command gives a blank file


Thanx In Advance to anyone 

Please help, I am really desperate to get that data back

---

### Post by bulldog on 2007-01-06
Boot into the live cd and mount your windows partition.
This will give you the opportunity to save your data.

If you are booted from the live cd open a terminal [ALT+F2 and type gnome-terminal]
Type in the terminal
```
sudo mkdir /mnt/rescue
sudo mount -t ntfs /dev/hda1 /mnt/rescue
``` 
Now your windows install is mounted and you can navigate with the file browser [nautilus] to the folder rescue and see if you can copy data from it.

You can try and reinstall the windows bootloader with the windows install disk.
Boot from it and let it run till you get three options.
1/Install windows
2/Repair a windows
3/Exit
Choose option two and you will be taken to the recovery console.
Choose your windows install,mostly 1,and provide the administration password.
Then type fixboot and after that fixmbr
You'll get a warning but proceed after that exit the disk and try to boot into windows.

---

### Post by kitsch76 on 2007-01-06
Hi Bulldog,

Thanx for the quick reply.

I created the mnt/rescue successfully because I can see them using nautilus

the command "sudo mount -t ntfs /dev/hda1 /mnt/rescue"

gives the following:

mount: wrong fs type, bad option, bad superblock on /dev/hda1, missing codepage or other error. In some cases useful info is found in syslog - try dmesg | tail or so.


Also, I tried to do a Windows recovery but the process stops after I hit "r" for recover and I get a C: prompt. When I do "dir" I get a message that the file enumartion is not valid.

Any modifications to the mount command?

Thanx

Kitsch

---

### Post by bulldog on 2007-01-06
Well the mounting command is valid,if it can't mount your hdd,because the hdd is a mess another command won't help either.
You can't find a windows install,that says enough.

The only thing you can try is reinstalling windows,and I only can hope your data isn't on the first partition,because you almost certain have to format it before you can install windows.

Maybe you can give me the outcome of this command?
```
sudo fdisk -l  (l as in like)
```

---

### Post by kitsch76 on 2007-01-06
Hey Bulldog,

Yeah I kinda figured that the Windows partition is pretty much gone. My only hope is that "disk recovery" software will help recuperate the data.

As for the fdisk command:

Disk /dev/hda: 30.0 GB, 
15 heads, 63 sectors/track, 62016 cylinders
Units = cylinders of 945*512 = 483840 bytes

Device        Boot     Start       End       Blocks          Id    System
/dev/hda1     *         1          62016     29302528+   83     Linux
Partition 1 does not end on cylinder boundary
/dev/hda2
Partition 2 does not end on cylinder boundary

Partition table entries are not in disk order



(Yeah that sounds pretty bad doesn't it )


Not sure if you or anyone else knows about disk recovery programs:

My guess was to find a away to connect the Laptop hardisk (the one that is corrupted)
to my desktop and run the disk recovery program on the laptop harddisk to either try rebuilding the tables or recover the partition.  Or otherwise just try recovering the files

Any advice?

Thanx

Kitsch

---

### Post by bulldog on 2007-01-06
Doesn't look very well indeed.

Can't give you any helpful advice I'm  afraid,never had to recover data.

---

