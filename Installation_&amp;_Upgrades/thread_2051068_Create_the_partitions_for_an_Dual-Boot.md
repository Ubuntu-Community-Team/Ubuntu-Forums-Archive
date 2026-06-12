---
title: "Create the partitions for an Dual-Boot"
date: 2012-09-01
forum: Installation &amp; Upgrades
---

### Post by alevkov on 2012-09-01
Sorry for opening the thread but i need to ask this just to be sure. 

I have an 500 GB HDD and want to make it dual boot ready while installing Ubuntu first and leave an 50GB partition free for Windows if needed. 

This is so what i know and i need to create for Ubuntu

/boot (primary?) about 300 - 500 MB. 
/swap (primary) 4 - 8 GB 
/ (logical) should be around 20 GB, right? 

The question is, i want to create an partition where i can put my private data (nd later encrypt it with TC) which format shoould be that partition for my data (if somethign happends to ubuntu i can make sure it wont break it). 

Also, the Windows partition should just can be unaloccated space right?

---

### Post by jerome1232 on 2012-09-01
You don't *need* a seperate /boot partition for Ubuntu, I would recommend you create a swap partition and a / partition. 20 GB's is plenty for / if you are keeping your data on a separate partition. You can make / a logical partition, Ubuntu will still be perfectly happy to boot. For a data partition that needs to be shared with Windows I would use ntfs, some might recommend fat32... I don't since it can't hold files bigger than 4 GB's.

I would also like to note that it's much, much easier to install Windows first then Ubuntu if you intend to dual boot. If you install Ubuntu first, then when you install Windows it will happily nuke grub without saying anything and make Ubuntu unbootable, then you have to go through this whole repair grub ordeal to get both booting. If you install Ubuntu last grub automatically picks up on the windows install and everyone is happy.

---

### Post by alevkov on 2012-09-01
Thanx jerome, that's exactly what i ve read were many mented the boot grup problems. 

Well then this is the process, 

Install Window$ and turn it off. 

Use the space like this?

/swap 8 GB primary
/ 10 GB logical
/home 330 GB logical

agree?

---

### Post by jerome1232 on 2012-09-01
> **alevkov said:**
> Thanx jerome, that's exactly what i ve read were many mented the boot grup problems. 

Well then this is the process, 

Install Window$ and turn it off. 

Use the space like this?

/swap 8 GB primary
/ 10 GB logical
/home 330 GB logical

agree?

That's a ton of swap, If you wan to hibernate go with a little more than you have in ram, otherwise 1-2 GB's of it is plenty, I have 1 GB of swap with 4 GB's of ram and I rarely dip more than 100 MB's into my swap.

I was under the impression you wanted a totally separate data partition to be shared between Windows and LInux, /home can't be used for that purpose as it has to be ext4 or another Linux file-system, Windows support for Linux file systems is dodgy at best.

I would go with something like this if I was creating a separate data partition to share between Windows/Ubuntu. With this setup you'd store all data under the partition mounted at /mnt/data, it would be easily accessible from both Windows (Windows would call it the "D:" drive) and Ubuntu.

```

sda1 Primary ntfs Windows (whatever here)
sda5 Logical swap 1 GB
sda6 Logical ext4 / 15 - 20 GB's 
sda7 Logical ntfs /mnt/data (really big amount)

```Alternatively if you don't care about accessing it easily from Windows and you just want a separate home
```

sda1 Primary ntfs Windows (whatever here)
sda5 Logical swap 1 GB
sda6 Logical ext4 / 15 - 20 GB's 
sda7 Logical ext4 /home (really big amount)
```

---

### Post by alevkov on 2012-09-01
Now that's quality, thanx for input. Well i don't care bout the sharing since i will encrypt home and make it private. The only thing i might need is to transfer some files from Ubuntu to Win nd that's easy done.

---

### Post by jerome1232 on 2012-09-01
> **alevkov said:**
> Now that's quality, thanx for input. Well i don't care bout the sharing since i will encrypt home and make it private. The only thing i might need is to transfer some files from Ubuntu to Win nd that's easy done.

Just so you know Ubuntu offers to encrypt your users home directory during the install, you can do this and as long as you have a live cd around you can recover your encrypted data if your system went south. (your keeping backups anyways though, right?)

This link gives you information on what to do if you ever had to manually recover an Ubuntu encrypted home directory
[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Data_Automatically](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Data_Automatically)

---

### Post by alevkov on 2012-09-01
jerome lets get back to 

> sda1 Primary ntfs Windows (whatever here) 
sda5 Logical swap 1 GB 
sda6 Logical ext4 / 15 - 20 GB's  
sda7 Logical ntfs /mnt/data (really big amount)If i decide for this setup, how should like one extra private data partition for the private stuff? 

I mean an 25 GB partition, which can be seen only under Ubuntu but it should be out of the dange if root crashes. Home will be lost if i decide to upgrade / make a new install, right?

---

### Post by jerome1232 on 2012-09-01
> **alevkov said:**
> Home will be lost if i decide to upgrade / make a new install, right?

Let's talk about this first, first know your users home directory is where all per user configuration files and personal data is normally kept. You can preserve your /home if it's on a separate partition but I don't like dragging my old configurations into a new install. So I opt to not separate my /home, and I keep all of my data on a partition that's shared with Windows.

> **alevkov said:**
> If i decide for this setup, how should like one extra private data partition for the private stuff? 

I mean an 25 GB partition, which can be seen only under Ubuntu but it should be out of the dange if root crashes

You can just add an extra partition like so (of course you can name the mount point whatever you want) If you use the alternate text based installer, it comes with encryption utilities built into it, and you can create that last partition as an encrypted partition.. however

```
sda1 Primary ntfs Windows (whatever here) 
sda5 Logical swap 1 GB
sda6 Logical ext4 / 15 - 20 GB's  
sda7 Logical ntfs /mnt/data (really big amount)
sda8 Logical ext4 /mnt/supersecret 25 GB's
```

Now I'm about to get complicated, if your going to go around encrypting things, you should encrypt your swap partition as well (since your data can be in ram, and get paged out to swap, where it will be visible in plain text unless your swap is encrypted) If you elect to encrypt your users home directory as I mentioned during the install, it does that for you.

If you wanted to do all that with an Alternate install cd you could us lvm and luks to encrypt your entire Ubuntu install (minus the shared partition)

It would be something like (but again this is probably getting to complicated)
```

sda1 Primary Windows ntfs
sda4 Logical /mnt/data ntfs
sda5 Logical Physical Volume for encryption
         |--------- Physical Volume for Logical Volume Management 
          Volume Group "Ubuntu"
           |---------- Logical Volume "root" ext4 / 15 - 20 GB's
           |---------- Logical Volume "swap" swap 1 GB
           |---------- Logical Volume "supersecret" ext4 /mnt/supersecret 25 GB's
```Here is a video demonstrating what I am talking about [http://www.youtube.com/watch?v=V4Bje0sLblo](http://www.youtube.com/watch?v=V4Bje0sLblo)

---

### Post by alevkov on 2012-09-01
That was interessing indeed. Tho i prefer to use TC and ecrypt the all partions with different keys/passwords nd auto options. 

Thanks alot, ya helped here alot.

---

### Post by darkod on 2012-09-01
If you want to make clean installs in future without deleting your home folder, why don't you simply create a separate /home partitions? That way you can reuse it in future installs without formatting it.

That partition can be the same with the one you mention about private data, or totally different, doesn't matter.

Also, I totally disagree with something said at the beginning: reinstalling grub2 to the MBR is hardly an ordeal. You need to boot into live mode and run two commands. Hardly difficult.
So, if you plan to install windows after 3-4 months, you can go ahead and install first ubuntu now, then windows later, and recover grub2 to the MBR after that.
On the other hand, if you plan to install windows in 2-3 days anyway, it makes more sense to install windows first and then ubuntu.

---

### Post by jerome1232 on 2012-09-01
> **darkod said:**
> If you want to make clean installs in future without deleting your home folder, why don't you simply create a separate /home partitions? That way you can reuse it in future installs without formatting it.

My take on this is, dragging your old config files around with you *can* cause issues, I like having my data separated, don't care about my configs. Everyone is different though.

> **darkod said:**
> 
Also, I totally disagree with something said at the beginning: reinstalling grub2 to the MBR is hardly an ordeal. You need to boot into live mode and run two commands. Hardly difficult.

Granted, it isn't difficult. If your not familiar with a command line it can be daunting though. Ubuntu live cd's really need a recovery GUI that can restore the MBR for you imho.

---

