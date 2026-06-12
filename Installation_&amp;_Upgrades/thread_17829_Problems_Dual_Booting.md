---
title: "Problems Dual Booting"
date: 2005-03-03
forum: Installation &amp; Upgrades
---

### Post by ironliver on 2005-03-03
Im a new user to linux and am having problems dual booting.

I have windowsXP on a harddrive that is Serial ATA
My Ubuntu installation is on another HD that is ATA

In my bios, if i have the Serial ATA device anywhere in the bootup order, it will go straight to Windows XP. For me to get into Ubuntu, i have to remove the Serial ATA from the order, and have it just boot to the ATA Hd. It waits for a second then goes to the Grub thing (sorry im a linux noob). If i choose to boot to Windows XP, it will do something then just hang (not frozen, but not doing anything).

So basically i have to mess with the bios depending on which operating system i want to use.

Another problem that i think is related, is i cant see my SATA HD (the one with XP on it) while im in Ubuntu. I read something that says i should mount /dev/hda1 to /media/windows/ .. I tried doing that, and it says its already mounted to / .Also how can you tell which partition is which in the /dev directory? I attached an image of what it says when i type mount. if that helps...

Anyways, thanks for any help.

-dan

---

### Post by zcox on 2005-03-03
I put [this tutorial](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/ubuntu.html) together to guide through a dual-boot install but it assumes you're installing Ubuntu to the same h/d.  Not sure how to do the two h/d thing.

As for mounting the WinXP partition, maybe [this](http://ubuntuguide.org/index.html#automountntfs) will help.

---

### Post by ironliver on 2005-03-03
ya, i did what that guide says about mounting the winXP partition, but it says that its already mounted... dont know what to do?

---

### Post by ShortyG on 2005-03-03
I have two hard drives now, one with XP, the other i'm planning on installing Ubuntu on soon.  I wish i could help, but i have my own question for this thread.  I was planning to just disconnect my master hd(with XP on it) and install ubuntu on the slave(set to master) just so i don't have to worry about fooling with partitions, i can just format and go. but i don't know if ubuntu will install a bootloader if it doesn't see another OS during the installation. Does ubuntu even have a bootloader? Does windows install a bootloader? I've worked with red hat and windows together, where red had installed it's own bootloader. I just didn't know if i need to go ahead and leave the windows drive plugged in and do advanced setup for ubuntu.

---

### Post by Buffalo Soldier on 2005-03-03
[QUOTE=ironliver]ya, i did what that guide says about mounting the winXP partition, but it says that its already mounted... dont know what to do?[/QUOTE]
 Can you copy and paste in here the output of **df -h -T**. Example:```

username@ubuntu:~ $ df -h -T
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hda2     ext3    8.9G  1.7G  6.8G  20% /
tmpfs         tmpfs   253M     0  253M   0% /dev/shm
/dev/hda1     vfat    9.5G  4.6G  5.0G  48% /media/windows
```

---

### Post by ironliver on 2005-03-03
ironliver@dan:~ $ df -h -T
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hda1     ext3     55G  1.6G   51G   3% /
tmpfs        tmpfs    253M     0  253M   0% /dev/shm

---

### Post by Buffalo Soldier on 2005-03-03
[QUOTE=ironliver]ya, i did what that guide says about mounting the winXP partition, but it says that its already mounted... dont know what to do?[/QUOTE]

If it's already mounted than it should show up with the **df -h -T** command.

Mind showing your fstab entry? (Easiest way for me is by typing **gedit /etc/fstab** in the console and just copy and paste here)

---

### Post by Beast on 2005-03-07
Ok im having a problem with THE ISO file that is said to download and run_qparted. I burned both programs onto a disk using Nero! and for whatever reason when i restart my computer it doesnt detect the file on the cd. Now am i doing something wronge? do i need to burn it a certain way? please help!. i a newbie when it comes to linux and been messing with my system all night to get a dual boot going.

P.S yes i have my cdrom as #1 boot drive. 

thanks in advance!

---

### Post by zcox on 2005-03-07
What programs did you burn?  (You said "burned both programs").  See [this page](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html#example) for info on how to burn SystemRescueCD and use QtParted.

---

### Post by Beast on 2005-03-07
Stable x86: and Unstable PowerPC: rescuecd. downlaoded both to see if one or the other worked.

Been up all night and very tired so i prob done somethign wronge here.

---

### Post by zcox on 2005-03-07
[QUOTE=Beast]Stable x86: and Unstable PowerPC: rescuecd. downlaoded both to see if one or the other worked.

Been up all night and very tired so i prob done somethign wronge here.[/QUOTE]
 Use SystemRescueCD from the link I sent before.  It works.

---

### Post by Beast on 2005-03-07
Well i just confused with that tutorial in the link above! the problem is even tough im reading it i still not quite sure what programs i need to be running! the qtparted and rescuecd part is what im having a problem with!

Im running ubuntu 64amd version.

Can some explain a little better what to do with qtparted and rescueCD.. if i ever get qtparted running i can do what the pictures show with no problems.

------------------------------------------------------------------------------------------------------------------------------

Ok that's where i downloaded the link from! from this page [http://www.sysresccd.org/download.en.php](http://www.sysresccd.org/download.en.php)

Ok i read up somemore and notice i have to download Qtparted, but it seems like for every program i download i need something else to run it. I still cant find out what do do with Qtparted! do i add it to the cd with the rescueCD?? then i read something about needing GNUparted then i need a bootdisk image for that WTH? lol.. also there are 2 files on this page for QTparted [http://qtparted.sourceforge.net/download.en.html](http://qtparted.sourceforge.net/download.en.html) 
im such a Noob when it comes to this Linux i really hate asking questions like this i have always been a windows user and know nothing about Linux.

-James

---

### Post by Beast on 2005-03-08
Ok, i said to heck with it and ordered a rescue cd.Ill mess with this crazy OS in a few days.

---

