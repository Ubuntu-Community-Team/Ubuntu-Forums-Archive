---
title: "Cannot Load into Ubuntu"
date: 2006-06-24
forum: Installation &amp; Upgrades
---

### Post by luish on 2006-06-24
Hey !

I am new into all the linux things.. i got from a friend a ubuntu cd case with a live cd and and installation cd.

I created a new partition on my sec. HD and i ran the installation cd and it installed it all.

In the end of the installation i got asked to install a boot loader (grub, i think) cause it detected XP also and i OK'd that.

After the reboot, i am now on XP and i cannot manage to go into the ubuntu drive.

but on Partition magic i can see that the installation is there..

how can i boot into ubuntu ?

btw, it is ubuntu 5.10... when i manage to get there, i will update to last version...

---

### Post by JoshHendo on 2006-06-24
It could be that you installed Ubuntu onto a Second HDD. If that is a slave HDD (which I am assuming it is), you will not be able to boot off it. Partition your main HDD (the one that Windows is currently on) into 2 and install Ubuntu on the second partition. Also remember to remove your first Ubuntu installation.

Even better would be to get the Dapper live CD and let it run its self, getting rid of Windows entirely (but I am assuming you still want to keep Windows).

Hope this helps.

- Josh

---

### Post by luish on 2006-06-24
Hey man..

Thanks for your reply.. i will be back now to Partition magic to fix that and to create the drive on my main HD.. i got there place.. my question...how many GB I need minimum.. just for a test installation...

and i dont wanna wait for the 6.06 download.. which i am currently at.. i just wanna try it now :)

---

### Post by maskd on 2006-06-24
It's not being seen under Win XP because Windows provides no default support for ext2 or ext3.

Here are a few pages that you can look at (Did a quick Google search):
[http://www.tldp.org/HOWTO/Filesystems-HOWTO-6.html](http://www.tldp.org/HOWTO/Filesystems-HOWTO-6.html)
[http://www.roudybob.net/?p=121](http://www.roudybob.net/?p=121)

Seems to just be a program that allows windows to see the ext3 (or ext2) drive.

Good luck with it.

EDIT: I reread your question and I think I answered a completely different question, this will let you see the ubuntu drive as any normal NTFS or FAT32 drive, I'll leave it up anyway.

---

### Post by luish on 2006-06-24
[QUOTE=JoshHendo]It could be that you installed Ubuntu onto a Second HDD. If that is a slave HDD (which I am assuming it is), you will not be able to boot off it. Partition your main HDD (the one that Windows is currently on) into 2 and install Ubuntu on the second partition. Also remember to remove your first Ubuntu installation.

Even better would be to get the Dapper live CD and let it run its self, getting rid of Windows entirely (but I am assuming you still want to keep Windows).

Hope this helps.

- Josh[/QUOTE]

I tried everything, and after each install i get to XP and i cannot boot into ubuntu..

what else can i try ?

---

### Post by luish on 2006-06-24
anyone... please help me !

I wanna try this distro :D

---

### Post by loserboy on 2006-06-24
so you're not getting a boot menu to choose your os?

and you did what he said about the partition on the main hd?

well im using 6.06 and its my 1st and only linux and it handles pretty much everything for you. are you using dial up and thats why u dont wanna dl?

---

### Post by luish on 2006-06-25
I download 6.06.
I am using XP i created a new partition using partition magic.
The new partition was made out of my Main HD, sata one, and the partition it's 20GB's.
I booted into cd installation cd and got all the install and after the end, i got the reboot and GRUB didn't load and i got into XP.

Another Problem ...

When I used the live version, I couldn't configure my modem.
I got an Router that it is connected to my PC LAN and to the telephone line.
In XP i use a PPPOE connection and i only put my username and password.
When i tryed to configure the modem, ubuntu asked me for an old modem, and i couldnt' try to connect.

Please help me to become a new user :)

---

### Post by luish on 2006-06-26
Bump..

anyone ?

---

### Post by loserboy on 2006-06-26
as far as configuring your modem on the livecd, i dont think you can really do any of that from cd because its not storing anything on hd.

and i'm still too much of a noob to tell you about grub... i do know you can get the super grub disc and try to install it from a bootable cd

search super grub   -   its easy to use just burn it as a bootable after u unzip it. its always good to have a backup of that anyway.


Edit: also were you watching the boot sequence and it didnt give an error or anything?

---

