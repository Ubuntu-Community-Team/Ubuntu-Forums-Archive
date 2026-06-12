---
title: "how to dual boot ubuntu 10.10, windows 7 on toshiba laptop???"
date: 2011-08-31
forum: Installation &amp; Upgrades
---

### Post by lalitha niharika on 2011-08-31
I dual booted my desktop with ubuntu and windows xp.But now I am unable to.First I installed ubuntu in one partition.I set other partition as FAT32.then I tried installing xp in other partition.I got error message that drive is correpted.Then I tried using windows 7.It formatted FAT32 to NTFS.I succesfully installed.But after installing, the screen to choose between ubuntu and windows is not appearing.Windows is opening by default.Now i just used ubuntu cd,I found that ubuntu is there in system.After checking that I am unable to open windows.Windows is giving error msg that some of its files got corrupted.Now I am going mad.Its my new laptop and I already booted it two times.This is the worst thing.Anyone plz give me perfect procedure to do everything perfectly.:mad:

---

### Post by saltmarshlamb on 2011-08-31
No idea why windows is causing issues - but the best way to install both without having bootloader issues is 

install windows
install linux

If you can get the windows issues dealt with then all you need to do then is reinstall grub2 and you'll get the grub screen to choose OS from

[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)
[http://ubuntuforums.org/showpost.php?p=6391959&postcount=1](http://ubuntuforums.org/showpost.php?p=6391959&postcount=1)

---

### Post by 3xp10r3r|X13 on 2011-08-31
This actually is a common issue. Windows always considers itself as the only OS on a hard drive. When you've installed Windows, it just got rid of your Linux boot loader (in this case grub 2). However, as both operating systems are still existing, the only thing you have to do now, is to install the Linux boot loader again.  

(when I say Linux boot loader, I'm talking about grub 2.. :) )

so here we go:
first of all, you've got to boot from a live cd (if you don't have it, just burn a new one). After you're in Ubuntu it's time to establish your root partition. You can either open a terminal and type:

```

# fdisk -l

```or just launch gParted to view the mount points of your partitions...well there  are loads of ways to do it.

Once you know which one your root partition is, you've got to mount it.
```

# mount /dev/root-partition /mnt

```after mounting it, you are able to install the grub 2 boot loader
```

# grub-install --root-directory=/mnt /dev/root-partition

```after you've installed it (assuming you're not having a specific partition like /boot)
just reboot 

In case windows is not showing up and you're just able to get into ubuntu, just update grub
```

# update-grub

```this should work for you

---

### Post by saltmarshlamb on 2011-08-31
> **3xp10r3r|X13 said:**
> This actually is a common issue.I was talking about the 'other' issues

> Windows is giving error msg that some of its files got corrupted.That needs to be dealt with in a windows forum :)

As you've said the bootloader issue itself is common and a quick search would have found thousands of the same :)

---

### Post by 3xp10r3r|X13 on 2011-08-31
> **saltmarshlamb said:**
> I was talking about the 'other' issues

That needs to be dealt with in a windows forum :)

As you've said the bootloader issue itself is common and a quick search would have found thousands of the same :)

sry, so I got him slightly wrong :D

I'll spend a bit more time reading the thread next time...

---

### Post by saltmarshlamb on 2011-08-31
:) Helps when it's not so much of a wall of text to be honest.

---

### Post by Mark Phelps on 2011-08-31
Would help if you told us WHAT you did with the Ubuntu CD.  You obviously did something that hosed up the Win7 boot.  Without knowing what you did, it's hard to provide advice.

Also, while you had Win7 working, you SHOULD have used the Backup feature to create and burn a Win7 Repair CD.  You could be using that right now to repair your Win7 problem.

---

### Post by lalitha niharika on 2011-09-03
I simply tried again, first i installed windows 7 then ubuntu, my problem got solved!!everything is fine now.Thank you all for quick help!!:P

---

