---
title: "Installing Ubuntu over Windows 7, recovery partition"
date: 2013-05-15
forum: Installation &amp; Upgrades
---

### Post by Sugiura Ayano on 2013-05-15
[COLOR=#333333][FONT=Ubuntu Beta]I'm currently attempting to install Ubuntu 12.04 LTS on my Acer Aspire 4830T-6678 laptop.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]The laptop came pre-loaded with Windows 7 Home Premium, and it contains a recovery partition that I don't want to lose. I want to keep it just in case I need to install Windows over Linux. I really don't want to have to buy a copy of Windows unless I need to. :P[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]So in short, I want to keep my recovery partition intact, but I also want to use the rest of the drive to install Linux on.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]How should I go about doing this? When I go to install Ubuntu, I get a notification that the installer has detected mounted partition. I'm not entirely sure what this means: Will it ruin the recovery partition?[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]My other question: if I decide to delete the Windows 7 partition, would it disallow me from recovering? I'm not sure if the recovery partition requires the original Windows 7 partition to be intact or something along those lines.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]I'm sorry if my message seems confusing; I have a hard time explaining things.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Thanks in advance![/FONT][/COLOR]

---

### Post by coldraven on 2013-05-15
The first thing you should do is create restore CDs and also backup your data.
Then you might want to defrag your drive before attempting to shrink the largest partition.
Alternatively, if you feel happy with the restore CDs you could use that partition for Ubuntu. 
There are Windows tools to do all the above.

---

### Post by Mark Phelps on 2013-05-16
Every vendors requirements are different, but in general, if you make changes to any of the following, the vendor-provided Recovery option is likely to fail:
1) Layout, format, and size of the partitions on the drive
2) Resizing or removing the original Win7 Boot or Win7 OS partitions
3) Messing around at all with the Recovery partition.

One easy and simple way around this is to do the following:
1) Download and install the FREE version of Macrium Reflect into MS Windows
2) Use the Macrium Linux Boot CD option to create and burn a boot CD
3) Use the Macrium image backup feature to back up the Win7 Boot and Win7 OS partitions to an external drive
4) Reboot using the Linux Boot CD, attach the external drive with the MR backup -- and confirm you can find the backups

At this point, you can remove any and all of the Win7 and Recovery partitions -- as you have a way to restore Win7 to its current state.

---

### Post by coldraven on 2013-05-16
> **Mark Phelps said:**
> Every vendors requirements are different, but in general, if you make changes to any of the following, the vendor-provided Recovery option is likely to fail:
1) Layout, format, and size of the partitions on the drive
2) Resizing or removing the original Win7 Boot or Win7 OS partitions
3) Messing around at all with the Recovery partition.

One easy and simple way around this is to do the following:
1) Download and install the FREE version of Macrium Reflect into MS Windows
2) Use the Macrium Linux Boot CD option to create and burn a boot CD
3) Use the Macrium image backup feature to back up the Win7 Boot and Win7 OS partitions to an external drive
4) Reboot using the Linux Boot CD, attach the external drive with the MR backup -- and confirm you can find the backups

At this point, you can remove any and all of the Win7 and Recovery partitions -- as you have a way to restore Win7 to its current state.

Well I never knew that, I guess my knowledge of Windows ended with XP.
My only use of Win7 is a locked down version on a corporate network where I work sometimes.
I shall refrain from posting about this subject from now on.

---

### Post by midnightramen on 2013-05-17
I had a similar situation, and to be honest, I found out that the best way is to probably just use another hard drive for the linux install and keep Windows on its own disk. A bit of a pain to swap hard disks, but then again, I don't have to worry too much about partition issues, grub being messed up, some corruption in the MBR, or some other thing.

---

### Post by holycow131415 on 2013-05-17
Clone your whole hard drive with clonezilla to an external drive. it will save your partitions and the clone doesnt take that much space.

---

### Post by Sugiura Ayano on 2013-05-19
Thanks to everyone who posted!

I decided to go with Mark's suggestion, but instead of backing up all partitions, I decided to just backup the Windows partition. The recovery partition isn't very useful in the long run, now that I think about it. :P

Thanks again!

---

### Post by Mark Phelps on 2013-05-19
> **Sugiura Ayano said:**
> Thanks to everyone who posted!

I decided to go with Mark's suggestion, but instead of backing up all partitions, I decided to just backup the Windows partition. The recovery partition isn't very useful in the long run, now that I think about it. :P

Thanks again!

IF your boot loader files are on a separate partition (you'll see it in Win7 Disk Manager -- it's a very small partition usually at the start of the drive), you need to back that up as well.

Also, be sure to make the Win7 Repair CD using the Win7 Backup function.  This way, if you do a restore later and it doesn't boot, you can use that CD to do repairs.

---

### Post by Sugiura Ayano on 2013-05-19
> **Mark Phelps said:**
> IF your boot loader files are on a separate partition (you'll see it in Win7 Disk Manager -- it's a very small partition usually at the start of the drive), you need to back that up as well.

Also, be sure to make the Win7 Repair CD using the Win7 Backup function.  This way, if you do a restore later and it doesn't boot, you can use that CD to do repairs.

Will do, and will do. Thanks. :)

---

