---
title: "Locked out, can't boot."
date: 2010-09-22
forum: Installation &amp; Upgrades
---

### Post by HistoryMac on 2010-09-22
Hi all, I have a rather frustrating issue here that's been giving me hell since about 5:00AM this morning. I just got a new laptop (a Compaq CQ42-138TU) and was hoping to dual boot between Ubuntu 10.04 and Windows 7 Ultimate (64-bit).
So, I partitioned the HDD (leaving the HP/Compaq restore partition and other partitions alone) and resized the partition that held the bundled copy of Windows 7 (32-bit). I resized it into two parts, installed Windows 7 Ultimate on one, and Ubuntu on the other. That's where the problems began.
Selecting "Windows 7 (loader)" in Grub presented me with the first few second of the bootscreen, then a BSOD for less than a second. After that, the machine immediately rebooted and got back to Grub. Ubuntu still booted fine, but I wanted to get access to Windows back, soI attempted to fix this by running:
```
 bootec.exe /fixmbr 
```
through CMD.exe on my Windows install disk. Now Grub is gone, and I'm stuck with Windows that still won't boot. :confused:

Essentially, I'm locked out from my PC.

I think this may have something to do (although I'm not really sure) with the order of my partitions, and the fact that one of them (I fear the Windows one) is a Dynamic partition, not primary, and is freaked out by the presence of other boot loaders and (to it) unreadable  partitions...

Also, just to clarify, the Windows install disk doesn't detect any HDD or OSs. I have no problem, however, booting into the Ubuntu 10.04 install disk so I can make any necessary changes through there.

Help would really be appreciated!

---

### Post by CharlesA on 2010-09-22
I would try to boot off the recovery partition to restore the drive to the original state. After that's done, image it with something like Clonezilla.

That way you can restore the image if it doesn't work.

Either that, or just reinstall Windows, since you have an install disk and clone it before you start messing with partitions.

---

### Post by HistoryMac on 2010-09-23
Problem is that the recovery partition seems to have freaked out too (although it's definitely still there on the HDD) so I can't use that, and the Windows Installer DVD doesn't even recognise the HDD at all! :confused:

---

### Post by CharlesA on 2010-09-23
So no drive is listed when you boot off the install dvd and are asked to select which device to install onto?

Try booting off an ubuntu livecd and running gparted to see if the drive shows up.

---

### Post by arjunbajaj on 2010-09-23
Hey,

1.First backup all your data.

2.Then Wipe your hard drive clean with something like WipeDrive.

3.Make 2 or more partitions...
One for Windows and one for Ubuntu

4.Then install windows 7 ultimate and install all the things provided with your laptop.

5.Then install Ubuntu on the next partition.

6.Boot into ubuntu and in the software center search and install StartUp-Manager.

7.Change the way you want to boot.

8. Enjoy!!!

The reason for installing windows first is because ubuntu leaves some linux strains which not much advavced os's like Windows cannot handle. Thats y they crash. If you install ubuntu later everything works fine.

Note: if you dont want to create a seprate partition for ubuntu you can try using wubi. Its an installer which will install ubuntu on the same partition but it will work as a seprate os.

Hope it helped you....

Arjun
[ArjunBajaj.com]("http://arjunbajaj.com")

---

### Post by HistoryMac on 2010-09-23
> **CharlesA said:**
> So no drive is listed when you boot off the install dvd and are asked to select which device to install onto?

Try booting off an ubuntu livecd and running gparted to see if the drive shows up.

GParted sees everything fine, and Ubuntu installer goes without a hitch. It's just the Windows installer that's a problem. It says that it doesn't detect any connect drives.

---

### Post by HistoryMac on 2010-09-23
> **arjunbajaj said:**
> Hey,

1.First backup all your data.

2.Then Wipe your hard drive clean with something like WipeDrive.

3.Make 2 or more partitions...
One for Windows and one for Ubuntu

4.Then install windows 7 ultimate and install all the things provided with your laptop.

5.Then install Ubuntu on the next partition.

6.Boot into ubuntu and in the software center search and install StartUp-Manager.

7.Change the way you want to boot.

8. Enjoy!!!

The reason for installing windows first is because ubuntu leaves some linux strains which not much advavced os's like Windows cannot handle. Thats y they crash. If you install ubuntu later everything works fine.

Note: if you dont want to create a seprate partition for ubuntu you can try using wubi. Its an installer which will install ubuntu on the same partition but it will work as a seprate os.

Hope it helped you....

Arjun
[ArjunBajaj.com]("http://arjunbajaj.com")

Thanks for that, if all else fails I'll give it a shot!

---

### Post by CharlesA on 2010-09-23
> **HistoryMac said:**
> GParted sees everything fine, and Ubuntu installer goes without a hitch. It's just the Windows installer that's a problem. It says that it doesn't detect any connect drives.

That's very strange indeed. When you installed Win 7 originally, did the installer see the drives?

I'm guessing you're probably going to need to delete the partition and see if it'll see the drive. Not sure why it's not seeing the drive at all.

@arjunbajaj: The reason you always install Windows first is because Windows likes to use it's own bootloader and will overwrite GRUB. If you install Linux after Windows, you don't have to mess around with getting GRUB to install.

You can  install Linux first and Windows second, but you'll have to reinstall GRUB.

Sidenote: When I get a new machine, I almost always clone the drive before doing anything with it. That way, if something goes wrong, I can just reimage it and be back at square one.

---

### Post by HistoryMac on 2010-09-23
> **CharlesA said:**
> That's very strange indeed. When you installed Win 7 originally, did the installer see the drives?
Yep, saw them fine. But that was before I installed Ubuntu. Since then it hasn't detected anything.

> **CharlesA said:**
> I'm guessing you're probably going to need to delete the partition and see if it'll see the drive. Not sure why it's not seeing the drive at all.
That's what I thought. I have attempted removing ONLY the partitions that I used to hold Windows and Ubuntu, but the Windows Installer still sees nothing. The only thing I haven't messed with is the two tiny partitions, one of which I believe is the recovery partition, and the other one Ubuntu refers to as "Windows 7 loader" which is odd, because the actual Windows partition is long gone. Does 7 use a loader separate to the host partition itself? Cause that might explain a bit...

> **CharlesA said:**
> @arjunbajaj: The reason you always install Windows first is because Windows likes to use it's own bootloader and will overwrite GRUB. If you install Linux after Windows, you don't have to mess around with getting GRUB to install.
This I am aware of, as it is the sole reason why I ended up locked out of Ubuntu too.

> **CharlesA said:**
> Sidenote: When I get a new machine, I almost always clone the drive before doing anything with it. That way, if something goes wrong, I can just reimage it and be back at square one.
I would usually do this to, but didn't expect to run into such strange problems. Then again, I was partitioning... Definitely a must-do for the future.

---

### Post by CharlesA on 2010-09-23
Yeah, Windows 7 loads the "boot loader" or something into a small 100MB partition. Might try deleting that one and see what happens.

---

### Post by HistoryMac on 2010-09-24
> **CharlesA said:**
> Yeah, Windows 7 loads the "boot loader" or something into a small 100MB partition. Might try deleting that one and see what happens.

Do you think maybe my best option would be to just wipe the entire HDD, pop in the Windows disk and then follow what arjunbajaj suggested?

---

### Post by CharlesA on 2010-09-24
> **HistoryMac said:**
> Do you think maybe my best option would be to just wipe the entire HDD, pop in the Windows disk and then follow what arjunbajaj suggested?

That would probably be a good idea. You don't really need the recovery partition if you've got a Windows install disk.

---

### Post by HistoryMac on 2010-09-25
Well, I erased the HDD entirely, booted into the Windows Installer and suddenly it could see it. I'm now typing this from Ubuntu 10.04, although I could also boot over into Windows and type it from there if I wanted to, seeing as dual-booting is now working A-Okay!. :popcorn:

Thanks for all your help, it's nice to finally be up and running.
Now, I just need to [get my sound working]("http://ubuntuforums.org/showthread.php?t=1580072")...

---

### Post by CharlesA on 2010-09-25
Glad it's working. :)

Don't forget to mark is as solved.

---

