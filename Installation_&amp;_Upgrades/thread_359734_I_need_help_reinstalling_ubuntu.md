---
title: "I need help reinstalling ubuntu"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by noobuntoo on 2007-02-12
After a recent update of my feisty fawn ubuntu, it will no longer boot ubuntu anymore. I cant get any answers as to why, so i want to reinstall ubuntu.

The only thing is, i dont want to lose all my files on my hard drive in the process. I have a live cd of 6.06 and another live cd of herd 3.

So heres my questions. 

Is it possible to access the hard drive when running ubuntu off a live cd?

If i reinstall ubuntu, am i going to lose my files on the hard drive? If no, can someone give me a quick walkthrough of the process?

---

### Post by Kateikyoushi on 2007-02-12
How did you partition your drive when you installed ubuntu ?
You can access your hard drive from the live disc. [LINK]("http://ubuntuforums.org/showthread.php?t=256632")

---

### Post by noobuntoo on 2007-02-12
Thanks for the reply

> **Kateikyoushi said:**
> How did you partition your drive when you installed ubuntu ?

Hmm im not completely sure. I know i have one internal hard drive that i partitioned to run ubuntu on. I have another internal hard drive that i run windows xp on. i do have grub installed on the same hard drive with ubuntu on it. Ubuntu is on the second internal hard drive in my system. Where do i find more specific partition information so i can mount the hard drive?

---

### Post by Kateikyoushi on 2007-02-12
You can check your partitions in gparted or with the following command.
```
sudo fdisk -l
```

You can check this guide to get more info how to mount your partitions. [LINK]("http://ubuntuguide.org/wiki/Dapper")

---

### Post by noobuntoo on 2007-02-13
ok, i ran this in terminal

```
sudo fdisk -l
```

and got this

```
disk /dev/hdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device     Boot     Start     End     Blocks     Id     System
/dev/hdc1   *          1      8612  69175858+  7     HPFS/NTFS

disk /dev/hde  120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device        Boot         Start        End          Blocks         Id          System
/dev/hde1     *               1          14219     114214086     83          Linux
/dev/hde2                  14220       14596       3028252+     5           Extended
/dev/hde5                  14220        14595      3028221       82         Linux Swap/Solaris
```

Still having a little trouble mounting it. I think my syntax is wrong. It should be something like "sudo mount /dev/hde5"?

Also, when i mount it, will i be able to login as my root username? Most of my files are in that username's folder and other usernames dont have permission to it. This is also a concern of mine when reinstalling. In the steps to install, it asks me to create a name and password. If i make a new one, will my old root name and pass be gone along with the username's folder?

Thanks in advance for any help anyone can give me. I feel im getting close to solving this one.

---

### Post by noobuntoo on 2007-02-13
ok i got a little farther

i ran
```
sudo mount /dev/hde1 /home/(myusername)/
```

and it basically tells me only the root user can mount that. If i try another folder, one that doesn't have any special permissions, then it just starts a new line in terminal with the cursor blinking....and thats it. Where would i find the folder i mounted? I open up the file browser and its the same old stuff. 

whats funny is, in the file browser it lists my other hard drive (the one that i have xp on) and i just have to right click it and select mount and i can see everything on it. But the one for ubuntu is not there. I know its plugged in, i have grub on it. The machine wouldn't get to the grub menu if it wasn't plugged in.

at this point i have 2 questions. How do i mount a folder from live cd when only the root user has access to it?

and, if possible, how do i reinstall ubuntu without losing my files or root username?

---

### Post by noobuntoo on 2007-02-15
*bump*

anyone? it can't be that hard.

---

### Post by Kateikyoushi on 2007-02-15
Does it work with this ?

```
sudo mount -t ext3 /dev/hde1 /mnt
```

---

### Post by Omnios on 2007-02-15
What errors do you get on boot? might be a grub thing if it can not find the two grub entries.

---

### Post by noobuntoo on 2007-02-16
> **Kateikyoushi said:**
> Does it work with this ?

```
sudo mount -t ext3 /dev/hde1 /mnt
```


ok, tried that in the terminal. Basically once i do, the cursor moves one line down and just sits there blinking. Waited a while and nothing happens besides that.

btw, this isnt a problem with grub. Grub loads fine. Its during the normal ubuntu loading screen that it fails.

---

### Post by confused57 on 2007-02-16
Here's the best tutorial I've found for mounting Ubuntu with the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

Do you get any error messages when Ubuntu tries to boot up? Can you boot into "Recovery" mode?

---

