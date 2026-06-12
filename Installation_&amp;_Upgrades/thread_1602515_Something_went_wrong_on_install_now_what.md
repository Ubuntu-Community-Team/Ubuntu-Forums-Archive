---
title: "Something went wrong on install now what"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by leighahh on 2010-10-21
Hi everyone. I downloaded ubuntu 10 latest version. I had windows xp. I tried it out first to make sure it worked on my comp. So i installed it but now windows xp is still there in dual boot and its taking up alot of my space. I cant for the life of me figure out how to get rid of it and how to do a clean install. I am not sure what I need to do. I want only ubuntu as my os and nothing else. Please what should or can i do. Thanks so very much!

---

### Post by UnterUn on 2010-10-21
Is there not an 'install' icon on your Ubuntu Desktop?

Else you'll have to download the .iso from the Ubuntu Website (Not WUBI) and make an install disk and use that.

I think there's another way but i can't for the life of me remember it...

---

### Post by Rubi1200 on 2010-10-21
Hi and welcome to the forums leighahh :)

It sounds as if you may have chosen the option to install Ubuntu side-by-side with Windows.

If you are able to boot into Ubuntu, please post the output of the following command:
```
sudo fdisk -l
```
(lowercase L not 1)

Thanks.

---

### Post by leighahh on 2010-10-21
> **Rubi1200 said:**
> Hi and welcome to the forums leighahh :)

It sounds as if you may have chosen the option to install Ubuntu side-by-side with Windows.

If you are able to boot into Ubuntu, please post the output of the following command:
```
sudo fdisk -l
```
(lowercase L not 1)

Thanks.

Ok where and how do i do that? Im sorry Im so new to this.

---

### Post by Rubi1200 on 2010-10-21
In Ubuntu go to Applications > Accessories > Terminal and copy/paste the command. Then copy/paste the results back here please.

---

### Post by sikander3786 on 2010-10-21
Go to Applications > Accessories > Terminal and paste the command.

When prompted for password, type it in. You won't see any asterisk or any other characters while typing. Don't panic, just hit enter after you've typed it.

Now paste the output here. Simple ;-)

Edit: Rubi beats me here./

---

### Post by leighahh on 2010-10-21
Not sure how to post results but here goes:

Disk /dev/sda: 17.3 GB, 17280442368 bytes
255 heads, 63 sectors/track, 2100 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00009040

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2007    16121196    7  HPFS/NTFS
/dev/sda2            2008        2100      747022+   5  Extended
/dev/sda5            2008        2100      746991   82  Linux swap / Solaris
leigha@ubuntu:~$

---

### Post by leighahh on 2010-10-21
Ok i posted it but im not sure if that is correct that was everything that came up

---

### Post by sikander3786 on 2010-10-21
Yeh you posted the correct output.

Seems like Rubi is busy somewhere so I'll answer this one.

The problem lies here.

```
/dev/sda1 * 1 2007 16121196 7 HPFS/NTFS
```

You didn't delete the Windows partition during installation and you still got that.

You can delete it from gparted or any other partitioning software and then run

```
sudo update-grub
```

to get rid of the Windows entry in Grub menu.

What you want to do exactly? Create a new partition in the space of Windows partition or extend your Ubuntu partition to take up that space?

---

### Post by leighahh on 2010-10-21
I want to get rid of windows partition so that ubuntu takes up that space so that i only have ubuntu and no dual booting. I dont want any trace of xp, ok i just want to run ubuntu as my only OS if that makes sense.

---

### Post by Rubi1200 on 2010-10-21
The problem is where is your Ubuntu install?

```
/dev/sda1   *           1        2007    16121196 [COLOR=Red]   7[/COLOR]  HPFS/NTFS
/dev/sda2            2008        2100      747022+   5  Extended
/dev/sda5            2008        2100      746991 [COLOR=Red]  82[/COLOR]  Linux swap / Solaris
```

If you installed to the drive there is supposed to be a partition that ends ```
83 Linux
```

If you installed via Wubi, then Ubuntu is **inside** the Windows partition.

You need to tell us what you want to do.

Here are a couple of options:

1. migrate the Wubi install to the drive (possible)

2. erase everything and go for a clean install (recommended)

3. setup a true dual-boot with Windows and Ubuntu (also a good idea if you plan on using Windows at all)

However, I am concerned because fdisk reports you only have a 17GB drive??

---

### Post by leighahh on 2010-10-21
> **sikander3786 said:**
> Yeh you posted the correct output.

Seems like Rubi is busy somewhere so I'll answer this one.

The problem lies here.

```
/dev/sda1 * 1 2007 16121196 7 HPFS/NTFS
```

You didn't delete the Windows partition during installation and you still got that.

You can delete it from gparted or any other partitioning software and then run

```
sudo update-grub
```

to get rid of the Windows entry in Grub menu.

What you want to do exactly? Create a new partition in the space of Windows partition or extend your Ubuntu partition to take up that space?

Ok I tried gparted but when I try to unmount it it says that it cant be cause its busy

---

### Post by PaulJ1 on 2010-10-21
Looks like something went wrong with the partitioning stage of the installer.

I don't see a Linux partition there. I only see the Linux swap partition and the NTFS-partition where windows lives (or used to live).

Perhaps next time you run the Ubuntu-installer, you might choose to erase your hard disk.(That will replace all partitions with the Linux filesystem, probably EXT4 and a swap partition. You will lose everything that was in your winXP installation.)

---

### Post by leighahh on 2010-10-21
> **Rubi1200 said:**
> The problem is where is your Ubuntu install?

```
/dev/sda1   *           1        2007    16121196 [COLOR=Red]   7[/COLOR]  HPFS/NTFS
/dev/sda2            2008        2100      747022+   5  Extended
/dev/sda5            2008        2100      746991 [COLOR=Red]  82[/COLOR]  Linux swap / Solaris
```

If you installed to the drive there is supposed to be a partition that ends ```
83 Linux
```

If you installed via Wubi, then Ubuntu is **inside** the Windows partition.

You need to tell us what you want to do.

Here are a couple of options:

1. migrate the Wubi install to the drive (possible)

2. erase everything and go for a clean install (recommended)

3. setup a true dual-boot with Windows and Ubuntu (also a good idea if you plan on using Windows at all)

However, I am concerned because fdisk reports you only have a 17GB drive??

it is low on GB its an old comp and only used for email and such.

---

### Post by leighahh on 2010-10-21
I want to just erase everything and go for the clean install, just start over.

---

### Post by Rubi1200 on 2010-10-21
> **leighahh said:**
> I want to just erase everything and go for the clean install, just start over.
No problem; here is how I suggest you do it.

Start the computer with the Ubuntu CD and choose to install.

Tell it to erase and use the entire disk.

Let Ubuntu run the default options, meaning the main partition and a swap partition. It will format the drive and do everything for you.

Then restart when it is finished, not forgetting to take the CD out, and you will have a nice, new Ubuntu installation.

Good luck and let us know how it goes please.

---

### Post by leighahh on 2010-10-21
> **Rubi1200 said:**
> No problem; here is how I suggest you do it.

Start the computer with the Ubuntu CD and choose to install.

Tell it to erase and use the entire disk.

Let Ubuntu run the default options, meaning the main partition and a swap partition. It will format the drive and do everything for you.

Then restart when it is finished, not forgetting to take the CD out, and you will have a nice, new Ubuntu installation.

Good luck and let us know how it goes please. 

Ok the problem is that when I start the comp with the disk in it doesnt give me any option to install it just does it my screen flashs a couple times but no options are available. Does this mean I need a new copy of it?

---

### Post by Rubi1200 on 2010-10-21
Please post the specifications especially RAM and graphics card.

---

