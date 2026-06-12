---
title: "Installing Ubuntu 14.04 LTS"
date: 2014-08-03
forum: Installation &amp; Upgrades
---

### Post by persiangulf on 2014-08-03
I want to install ubuntu 14.04 on my laptop that windows 7 was installed before. Here is my partition disk details :

C: 50GB
D: 390GB
E: 22.4GB ---- for ubuntu partiotion
F: 1.95GB ---- for swap partition


But when i want to install ubuntu on E partition, Ubuntu show D,E,F as one partition with 415GB.

Can anyone help me to separate them install Ubuntu on E and F.

By the way I have this problem with installing Redhat 6.4 too.

Thanks

---

### Post by Vladlenin5000 on 2014-08-03
Linux doesn't use letters like Windows. How exactly have you partitioned the disk? If you did it with Windows you did it wrong. You can and should use Windows tools to shrink any existing Windows partition in order to obtain free space for Linux but you can't use Windows tools to create partitions for Linux. After assuring you have enough free space and that your Windows boots fine - it's recommend to reboot twice and let it run chkdsk - then you can boot the Ubuntu installation media and, when prompted, select the 'Something Else' option and partition like you want.

---

### Post by coffeecat on 2014-08-03
> **persiangulf said:**
> 
But when i want to install ubuntu on E partition, Ubuntu show D,E,F as one partition with 415GB.

What in Ubuntu shows this? And as Vladlenin5000 says, Windows "drive" letters have no meaning in Linux.

Assuming that you are able to boot into the live desktop with the Ubuntu CD or USB, from the live desktop open the gparted program and then take a screenshot of the open window. Post the screenshot here.

You can take a screenshot of an open window in Ubuntu with alt-PrtScn, but if you need help with any of the rest of that, post back.

---

### Post by persiangulf on 2014-08-03
Thanks
Here is my partitions exactly as Ubuntu shows me :

Device          type        size
/dev/sda1     ntfs         1MB  
/dev/sda2     ntfs         104MB  
/dev/sda3     ntfs         54356MB  
/dev/sda4     ntfs         445644MB  

What tools should I use to create new partition for linux without damaging my /dev/sda4

---

### Post by coffeecat on 2014-08-03
What you have just posted doesn't in any way correspond with what you posted in your first post. How did you get that second list? If we are to help you effectively, we need **exactly** what Ubuntu is telling you, not an edited transcription. I'm baffled as to what your 1MB partition could possibly be - that must surely be a mistake.

Either post the output of this from an Ubuntu terminal:

```
sudo fdisk -lu
sudo blkid
```

Or the screenshot of gparted as I describe in my previous post.

Do you still have Windows? Which partition do you believe it is on?

---

### Post by persiangulf on 2014-08-03
> **coffeecat said:**
> What you have just posted doesn't in any way correspond with what you posted in your first post. How did you get that second list? If we are to help you effectively, we need **exactly** what Ubuntu is telling you, not an edited transcription. I'm baffled as to what your 1MB partition could possibly be - that must surely be a mistake.

Either post the output of this from an Ubuntu terminal:

```
sudo fdisk -lu
sudo blkid
```

Or the screenshot of gparted as I describe in my previous post.

Do you still have Windows? Which partition do you believe it is on?

Yes , I still have windows 7 and it is installed on /dev/sda3.
[ATTACH=CONFIG]255230[/ATTACH]

---

### Post by persiangulf on 2014-08-03
```
sudo fdisk -lu
```

Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63        2047         992+  42  SFS
/dev/sda2   *        2048      206847      102400   42  SFS
/dev/sda3          206848   106371071    53082112   42  SFS
/dev/sda4       106371072   976771119   435200024   42  SFS

```
sudo blkid
```

/dev/sda2: UUID="CAC48D71C48D6095" TYPE="ntfs" LABEL="System Reserved" 
/dev/sda3: LABEL="Data" UUID="3270F55770F521F1" TYPE="ntfs" 
/dev/sda4: LABEL="New Volume" UUID="EA74D0A574D07633" TYPE="ntfs" 
/dev/sda5: LABEL="New Volume" UUID="72C8D6C2C8D683AF" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
/dev/sr0: LABEL="Ubuntu 14.04.1 LTS amd64" TYPE="iso9660

---

### Post by coffeecat on 2014-08-03
Well - you've left out much of the output from both commands - there is no sda5 from fdisk and much else missing besides, and no sda1 from blkid - but I can see your main problem immediately. SFS in your fdisk output means that you have Microsoft dynamic partitions. You must have created them when you were using the Disk Management utility. There is no way you can install Ubuntu or any version of Linux to a dynamic disk. It is a Microsoft proprietary setup. You'll have to convert the disk back to a basic one if you want to install Ubuntu to it.

I'll have to find a couple of links for you for this. I'll post back when I have them.

---

### Post by coffeecat on 2014-08-03
Here we are. Read what oldfred has to say about converting dynamic disks to basic ones:

[http://ubuntuforums.org/showthread.php?t=2234660&p=13076200#post13076200](http://ubuntuforums.org/showthread.php?t=2234660&p=13076200#post13076200)

Ignore the bit about gpt/LDM - it's not relevant to you.

If you do successfully restore your drive back to a basic one, leave the Windows partitions as they are and don't try to create partitions for Ubuntu. Use Gparted in Ubuntu for that.

---

### Post by persiangulf on 2014-08-03
> **coffeecat said:**
> Here we are. Read what oldfred has to say about converting dynamic disks to basic ones:

[http://ubuntuforums.org/showthread.php?t=2234660&p=13076200#post13076200](http://ubuntuforums.org/showthread.php?t=2234660&p=13076200#post13076200)

Ignore the bit about gpt/LDM - it's not relevant to you.

If you do successfully restore your drive back to a basic one, leave the Windows partitions as they are and don't try to create partitions for Ubuntu. Use Gparted in Ubuntu for that.

Thanks a lot,
I used MiniTool Partition Wizard and convert dynamic partitions to basic ones and my problem has been solved.

---

