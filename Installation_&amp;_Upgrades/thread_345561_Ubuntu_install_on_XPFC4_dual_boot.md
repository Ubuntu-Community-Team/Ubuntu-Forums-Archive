---
title: "Ubuntu install on XP/FC4 dual boot?"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by aseembehl on 2007-01-24
I had installed fedora core4 on my PC some time back. Now I have decided to switch from FC4 to ubuntu.I am planning to install Ubuntu over Fedora on my computer. I am almost a total newbie to linux.

I have XP on one of the hardisk(80GB partitioned into two D: and E: )
The other hardisk(10GB C: ) has got Fedora Core4. When I had installed FC4, I had a tough time to get GRUB to work(I had to do a lot of research before getting it to work, had to edit something in the GRUB configuration file)

Now what scares me is if GRUB gives problems this time as well, then I am gonna loose my XP hardisk as well(which has got lots of important stuff), as Ubuntu installation would remove the previously installed Bootloader GRUB.

So is there any precautionary measure I should take before jumping into installation?

Aseem

---

### Post by aseembehl on 2007-01-24
Below is the screenshot which shows all my partitions taken from windows 'Disk management'

[[IMG]http://img244.imageshack.us/img244/5355/partition6xo.th.jpg[/IMG]](http://img244.imageshack.us/my.php?image=partition6xo.jpg)

My friend who is an advanced linux user advised me to post the screenshot here as he was not sure if I delete the C: drive(which has fedora right now) while installing ubuntu over it and windows changes the drive letters automatically thereafter, what would happen.

I also wanted to mention that I cannot read/write on this C: hardisk from windows.

Thanks
Aseem

---

### Post by aseembehl on 2007-01-25
It has been a day and still no reply to my query? Seeing the activity of the forum, I thought I would be answered in a few hours.

Anyways I have searced the forums here, none of them I found answered my query, so it would be nice if someone here would help.

Thanks in advance
Aseem

---

### Post by louieb on 2007-01-25
Need some more info that disk manager does not provide. 
(Don't see a swap partition that could give Ubuntu a problem). 
Log into Fedora as root. open a terminal window.
and copy and paste  the output of 
```
fdisk -l
```that a lowercase l as in little.
here.

---

### Post by aseembehl on 2007-01-25
Thank you for the reply. 

I did what you said and this is what I got:

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/hda2            5100        9729    37190475    f  W95 Ext'd (LBA)
/dev/hda5            5100        9729    37190443+   7  HPFS/NTFS

Disk /dev/hdb: 10.2 GB, 10242892800 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          13      104391   83  Linux
/dev/hdb2              14        1245     9896040   8e  Linux LVM
```

---

### Post by louieb on 2007-01-25
I don't think you are going to have any problem replacing Fedora with Ubuntu.
fdisk show me you have an 80 gig drive  with 2 windows partitions I assume that you want Ubuntu to leave this drive untouched. 
You also have a 10 gig drive that has Fedora Linux installed. The reason I did not see a swap partition is that Fedora set up the 2nd partition under what is called Logical Volume Management. and the swap partition is hidden in it somehere. That a very nice thing to have if you are running a Linux only server.  But it just gets in the way of sharing Linux data on a Dual Boot PC.

But there is something strange about the windows disk management window screen shot. It really weird that is says the LVM partition in the small drive is drive C:. I would have expected the partitions windows labeled the E: drive to be labeled C:. And the 2nd partition of the small drive not to be labeled at all.     

Just better safe that sorry. Download and burn to CD the system rescue CD  and  the Super Grub Disk CD. Especially if you are install Edgy. I have found Dapper (6.06.1) does a safer job of installing itself. Usually it safe enough to install to a second hard drive but in you case  I would strongly recommend backing up your data.    

When you install Ubuntu it will ask where you want to install it. 
Just choose your 10 gig drive (the installer will probably call /dev/hdb or just hdb) .
After a while Fedora will be replaced by Ubuntu.
Good luck

One more thing I just noticed is both your NTFS partitions  on the 80 gig drive are almost full. Don't know how XP is going to act when you fill them up. But if you do that in Linux there is a good chance   it won't work unitl you free up some space or add more.

---

### Post by aseembehl on 2007-01-26
Finally today I went ahead with the installation. It couldn't be easier, the installation was such a breeze.

Thank you louieb for all the help.

Aseem

---

