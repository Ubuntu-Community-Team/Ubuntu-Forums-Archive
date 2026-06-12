---
title: "questions before the switch, Mandrake to ubuntu"
date: 2005-04-22
forum: Installation &amp; Upgrades
---

### Post by railz68 on 2005-04-22
Currently dual booting Mandrake 10 and XP. I have to ask a few questions before I make the jump.
I have unbuntu downloaded and burned. Now it's backup time.

Mandrake 10 uses LILO for boot, ubuntu uses GRUB. Is there anything I need to do with master boot record before trying to install ubuntu ?. Back it up somehow, remove it, edit it ?.

Do I need to delete mandrake somehow, or will ubuntu install do this for me. I created the partitions for mandrake with Partition Magic in XP.
Will ubuntu see/use these partitions ?.

Backing up my accounts in mandrake, will this work, or does anyone have better suggestion.

> tar -cvpf /tmp/home.tar /home to tar up all of the files in /home under /tmp, preserving permissions (the p flag).

To undo it properly, after you have the new distro installed:
cd /
tar -xvpf home.tar

My plan is to create "accounts" with same names as now. I'm hoping to get up and running quicker this way. (email, bookmarks, passwords, ....).

Lastly, how can I remind myself which partition is what.
C: = XP
D: is 160gig, has a NTFS partition, a FAT32, and the SWAP and Linux partition.

I think it would be good to know (or find out) which is which in the linux lists partitions.

hda1
hdb1
.....
Hope I asked that last part correctly.

Thanks for any advise or help with this. I was nervous installing mandrake, more nervous now that I "could" destroy both OS's. I need one or the other to come back here for help  :|

---

### Post by magicfab on 2005-04-22
Regarding the backup, I would be careful when retrieving the files into a Ubuntu based system. Remember Mandrake is based on RedHatg originally, so the file structure (configs, options, docs, etc) is not the same.

I think fdisk -l will give you more information on your partitions . Use man to find out more about fdisk. You can also install qtparted which will be nicer (being a graphic application).

---

### Post by railz68 on 2005-04-22
[QUOTE=magicfab]Regarding the backup, I would be careful when retrieving the files into a Ubuntu based system. Remember Mandrake is based on RedHatg originally, so the file structure (configs, options, docs, etc) is not the same.
[/QUOTE]

Yes, I kinda fiqured it couldn't be that easy. What I'm really wanting to restore/backup are the hidden directories "ie  .evolution /  .etwolf  / .pan".......

For example, my wife uses Evolution, and some crazy reason, saves all mails in folders (personal/business/...)
I plan on installing and/or using Evolution with ubuntu for her, but was hoping I could copy the hidden ".evolution" directory back to her account (home). Giving her all her old mails and what not.
Myself, I use Thunderbird, so I was hoping to copy back ".thunderbird", and be up and running quickly.

I know I should, and will install programs based on ubuntu, but before they are actually "executed/run", the hidden directory usually dosen't excist. I was hoping I could use/copy the old ones from mandrake.

I did this process going from mandrake 9 to 10, and it worked, but as you have said, they are not the same.
From what I've learned, the ".hidden" in /home directory is not created untill the first time a application is executed. If I put that directory there first, will it not use it ?.

I'm hoping you kinda get the jist of what I'm trying to do. Would you happen to have a better option or advice on doing this.

---

### Post by sas on 2005-04-23
Ubuntu will see your mdk partitions, it's just a matter of selecting the one(s) you wish to format in the install process. Ubuntu should just overwrite the MBR as well...

---

### Post by fordfan753 on 2005-04-23
[QUOTE=railz68]Currently dual booting Mandrake 10 and XP. I have to ask a few questions before I make the jump.
I have unbuntu downloaded and burned. Now it's backup time.

Mandrake 10 uses LILO for boot, ubuntu uses GRUB. Is there anything I need to do with master boot record before trying to install ubuntu ?. Back it up somehow, remove it, edit it ?.

Do I need to delete mandrake somehow, or will ubuntu install do this for me. I created the partitions for mandrake with Partition Magic in XP.
Will ubuntu see/use these partitions ?.

Backing up my accounts in mandrake, will this work, or does anyone have better suggestion.



My plan is to create "accounts" with same names as now. I'm hoping to get up and running quicker this way. (email, bookmarks, passwords, ....).

Lastly, how can I remind myself which partition is what.
C: = XP
D: is 160gig, has a NTFS partition, a FAT32, and the SWAP and Linux partition.

I think it would be good to know (or find out) which is which in the linux lists partitions.

hda1
hdb1
.....
Hope I asked that last part correctly.

Thanks for any advise or help with this. I was nervous installing mandrake, more nervous now that I "could" destroy both OS's. I need one or the other to come back here for help  :|[/QUOTE]
 Grub will automatically recognise XP, so no problems there.

In the Ubuntu installer you have a choice where to install Ubuntu, select the old MDK partition, format it first, the mount it to / and tell the installer to use this partition, make sure the installer will not touch your NTFS partitions by making sure that "do not use" is selected in the NTFS partition screen thingy.

i don't recommend backing up your whole home directory, just copy the important stuff, eg documents, cool pictures, etc to a CD, USB Flash Drive, or even one of your NTFS partitions.
You probably would have used Kontact for your email in MDK since its KDE based, but since Ubuntu is Gnome based the most convenient mail client would be evolution, this means you can't import passwords and stuff from kontact, not that I would recommend that anyway, too much room for errors and conflicts. Good Luck with your Ubuntu install, it really is a great distro.

---

### Post by computerdude33 on 2005-04-23
One thing I've been able to do- I adore running KDE programs in Gnome, but, IMO, Konqueror < Nautilus & Firefox

---

### Post by fordfan753 on 2005-04-23
[QUOTE=computerdude33]One thing I've been able to do- I adore running KDE programs in Gnome, but, IMO, Konqueror < Nautilus & Firefox[/QUOTE]
 I would run a few KDE apps under Gnome...but the only reason I don't is that you have to have all the Klibs and stuff installed to satisfy all the dependencies of these programs, I just find this unnecessary when there are Gnome alternatives to everything I would ever want.

---

