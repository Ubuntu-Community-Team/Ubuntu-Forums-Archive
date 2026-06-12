---
title: "2nd Hard drive question mounting"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by linuxfan128 on 2006-07-06
i have installed a 2nd hardrive in my PC.

I have used gnomes disks tool to mount it to a folder on my Desktop. The problem is when i restart my PC it is as if i did nothing. How do i fix this? it is listed as HDD.

---

### Post by frodon on 2006-07-06
If you want to have a partition automounted on startup you must add a dedicated line for this partition in the /etc/fstab file.
Give us the output of "fdisk -l" command or the name of the partition you want to mount.
Tell us what is the file system used on this partition and where you want to mount it.
Then we will tell you how to do it.

For information, the fstab file is used to put mount commands you want to run on startup.

---

### Post by linuxfan128 on 2006-07-06
fdisk -l output

```
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4678    37576003+  83  Linux
/dev/hda2            4679        4865     1502077+   5  Extended
/dev/hda5            4679        4865     1502046   82  Linux swap / Solaris

Disk /dev/hdd: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        3736    30009388+  83  Linux

```

Filesystem : ext3
shows as HDD
i wand the mount point to be /home/christopher/Desktop/2nd

---

### Post by frodon on 2006-07-06
Nice, open your fstab file : ```
sudo gedit /etc/fstab
```Then add this line at the end of the file : ```
/dev/hdd1 /home/christopher/Desktop/2nd ext3 defaults 0 0
```And it should be ok, if you want to try if it works without rebooting use this command : ```
sudo mount -a
```This command run all the mount commands written in the fstab file.

---

### Post by linuxfan128 on 2006-07-06
I thank you for your help. i have 1 more questions.
 Where can i find a icon of a hard driive in ubuntu? i want the folder to have a hard drive icon on my desktop.

---

### Post by aysiu on 2006-07-06
If you followed frodon's directions exactly, it should already be on your desktop as a folder called *2nd*... if your name is Christopher.

---

### Post by linuxfan128 on 2006-07-06
hmm i wounder what i did wrong.
It shows up on Desktop as a folder with a little lock icon on it.
it is because i created the folder before i mounted it?
it could be permsiion problems?
here is a screenshot to help diagnose the problem.
[[IMG]http://img408.imageshack.us/img408/9569/screenshot5rh.th.png[/IMG]](http://img408.imageshack.us/my.php?image=screenshot5rh.png)

---

### Post by aysiu on 2006-07-06
No, it's because you didn't change permission or ownership of the folder. If your username is, in fact, christopher: ```
sudo chown -R christopher:christopher home/christopher/Desktop/2nd
sudo chmod -R 755 home/christopher/Desktop/2nd
```

---

### Post by linuxfan128 on 2006-07-06
i want the folder icon to look like the icon i circled in this pic. i also dont want the lock shown.
[[IMG]http://img255.imageshack.us/img255/2443/screenshot16jt.th.png[/IMG]](http://img255.imageshack.us/my.php?image=screenshot16jt.png)

---

### Post by linuxfan128 on 2006-07-06
Lock icon gone!! Thanks allot. btw i added / infront of home to make it work. i think it should be fine now. Now all is left is to change the icon.

---

### Post by ThirdWorld on 2006-07-06
good thread and nice solution, but i still dont understand why this basic feature is so incredible complicated in Ubuntu, its absurd.  why you need to manually edit fstab to mout your new hdd and then type more commands in the console. In other operating systems, and other linux distros,  you just install your new hdd and the system automaticaly add it to your HDD list. Something so basic is so damn complicated.

---

### Post by aysiu on 2006-07-06
I don't understand either.

Knoppix has been able to do this forever regardless of filesystem--FAT32, Ext3, NTFS...

The drive is on your desktop, you click it, it mounts, it opens...

---

