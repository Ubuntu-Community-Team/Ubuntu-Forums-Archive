---
title: "Trouble installing Ubuntu alongside Windows 8"
date: 2014-03-02
forum: Installation &amp; Upgrades
---

### Post by dodo2 on 2014-03-02
Hello,
 I have trouble installing Ubuntu 12.04 LTS ony my laptop ( Asus k55vm - [http://www.asus.com/Notebooks_Ultrabooks/K55VM/#specifications](http://www.asus.com/Notebooks_Ultrabooks/K55VM/#specifications) ). I already have windows 8 and i want to install Ubuntu alongside it.(hopefully without deleting any files).I've read a lot of topics on the subject, but couldn't make it work.
Things i've tried: 
 - I turned off the **Fast Startup** on windows;
 - I have 3 disks, so i shrink **(E:** and now i have **97,66GB Unallocated** - thats the place i made for linux.(**disk manager** screen: [http://i.imgur.com/nJXx8UR.jpg](http://i.imgur.com/nJXx8UR.jpg) )
 - Checked the** Secure Boot**([http://i.imgur.com/skulZg4.jpg](http://i.imgur.com/skulZg4.jpg));
 - When i try to install Ubuntu, it doesn't recognize that i have an operation system([http://i.imgur.com/323QVPf.jpg](http://i.imgur.com/323QVPf.jpg)) (i found a lot of topics about that, so i guess it is normal not to detect windows 8), so i continue clicking "**Something Else**", but then it doesn't recognize the disks as they are in windows, it simply show me one partition([http://i.imgur.com/qcDNyT9.jpg](http://i.imgur.com/qcDNyT9.jpg)).( i was hoping to show me the unallocated space, so i could install it there)
 btw i noticed a little error shows just for a second right before it loads the ubuntu cd.([http://i.imgur.com/MCTzJwh.jpg](http://i.imgur.com/MCTzJwh.jpg)) (not sure if it is important)
 Additional information: 
 ***Gparted***
 ***sudo parted -l***(i wasnt sure yes/no)
 ***sudo fdisk -l***
screen: [http://i.imgur.com/wE1WO31.jpg](http://i.imgur.com/wE1WO31.jpg)
If there is any information you need, just say it.
Thank you.

---

### Post by ajgreeny on 2014-03-02
Did you boot the install medium (DVD/USB?) in UEFI mode, as it is essential that you boot in the same mode that you are going to install the OS.

I think that you have disabled secure boot but can not really see in your screenshot as it is a bit blurred, and secure boot is not something I have ever had to deal with; my computer had no OS at purchase.

Have you seen and read all the info at [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI").  If not have a good read through as it may help solve your problem.

---

### Post by dodo2 on 2014-03-02
I found  out that the BIOS Mode is **Legacy** and my pc doesn't support [B]secure boot.
[/B]So i went to BIOS settings, it was set **UEFI *Enabled*** so i disabled it and tried again to install(there was no error in the begining this time), but i got the same result -> when i come to this step [http://i.imgur.com/qcDNyT9.jpg](http://i.imgur.com/qcDNyT9.jpg) .. there is only one partition..

---

### Post by oldfred on 2014-03-02
Your screen shot showed typical BIOS type install with MBR(msdos) partitions. But it is also showing some gpt info. Was this a Windows 8 system before with gpt partitioning?
Windows does not correctly convert to MBR when overwritting a gpt drive. It leaves the backup gpt partition table, and then Linux tools see MBR and backup gpt and do not know which you have.

 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

But you are showing 4 primary partitions which is all you can have. You have to also count the system reserved or hidden boot partition for Windows.

      
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
This suggests removing system partition and making c: the bootable partition. But has details on all alternatives
[http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019](http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019)
Shrinking a Windows Vista/7/8 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

