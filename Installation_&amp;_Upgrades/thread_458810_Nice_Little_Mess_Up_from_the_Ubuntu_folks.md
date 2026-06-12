---
title: "Nice Little Mess Up from the Ubuntu folks"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by jimbo99 on 2007-05-30
Here I sit all broken hearted, ran the upgrade and Ubuntu farted.

Well, aside from the stupid humor there is an issue with the update that was CAUSED by the FOLKS at UBUNTU.

You developers/repository maintainers do realize you are targeting the average home user, no?  Well, you should.  Never should I be required, after performing an update flagged by the folks at the Ubuntu repository, to modify the grub boot loader and then correct the /boot/grub/menu.lst file.

What happened was I have several HDDs, all of them are SATA.  I have one drive that is set up with Ubuntu.  It has the boot loader.  I then have two other SATA drives just for various types of storage.

When I was flagged and told that there was an upgrade to the Ubuntu generic headers, etc I just took them.  I did this because the folks at Ubuntu are making this OS for the human beings in the world.  Mom and pop, and grandma and grandpa and even the great great grandmas and grandpas that exist in this world are human too and they have no intention whatsoever of modifying their grub nor do they expect that a simple update should wreak such havoc.

After I ran the update and rebooted I received messages such as error 17 and error 21.  After tracking it down it turns out that the update modified my menu.lst.  In doing so it messed up because it improperly determined the boot device (or rather which of my 3 drives is the correct one to boot from).  Instead of looking at the BIOS and determining which one was set to be booted from and correctly determining which device it should be listed as for grub it failed.

What it did was it took and modified the menu.lst file correctly.  Then it copied the menu.lst file into the name menu.lst~ and then it proceeded to modify the menu.lst file a second time this time putting the wrong HDD as the boot device.  It listed it as HD1,0 instead of HD0,0.

In grub you can run the command line and issue a find command to locate the stage one and stage two.  You can also do several other things including modifying the menu.lst with a series of commands.

Unfortunately all these things failed.

Running:

grub> root (0,0)
grub> setup (hd0)

and even

find /boot/grub/stage1 (which worked but seems to not have made any difference as it probably isn't a command that is used to alter files).

Anyway, after issuing the first two commands it should have altered my menu.lst file with the correct HDD reference except it didn't. 

I then had to find my Ubuntu boot CD.  Then I had to try to remember the command to manually mount the volume.  Then I had to edit the menu.lst file manually.  Well, I actually just copied files around since the attempt by the update manager did actually alter the file correctly, it just screwed up and altered it a second time with the wrong references.

I managed to get it up and running, but I don't have the second and 3rd drive set up again--yet.

This has been a great inconvenience and the whole process of updating grub needs to work before you introduce ANY change to the repository which could affect the humans that we are out in the wild world of Linux.  Think twice, three times, check over and over and don't release anything until you are 100% correct in making the change.  Otherwise it isn't worth it.  It just isn't worth putting grandma or grandpa through such a nasty problem when all they do is choose to accept the update that you guys provide.

Anyway, enough of my rant.  I would just say "don't let it happen again".  You should know better.

---

### Post by confused57 on 2007-05-30
> This has been a great inconvenience and the whole process of updating grub needs to work before you introduce ANY change to the repository which could affect the humans that we are out in the wild world of Linux. Think twice, three times, check over and over and don't release anything until you are 100% correct in making the change. Otherwise it isn't worth it. It just isn't worth putting grandma or grandpa through such a nasty problem when all they do is choose to accept the update that you guys provide.

I agree completely...your point was eloquently presented.  I've seen numerous posts with almost identical problems as yours after the most recent Feisty kernel update, i.e. hard drive boot order wasn't identified correctly, thus the menu.lst boot entries were incorrectly listed(or listed differently) and other hard drives were identified differently than in the previous kernel.  I've attempted to assist some posters, but not know exactly what has changed is making it rather difficult...I maybe could troubleshoot on my own pc, which luckily updated without a problem.
Unless there is a possible kernel "fix", guess people with problems will have to "muddle" through it to find a solution.

---

### Post by Seti on 2007-05-30
Farts in the wind, my friend.

There's more to it here than grub, some of us actually use (dare I say it?) lilo. I do because in my infinite stupidity I decided to make my root partition xfs. Ubuntu installer didn't like that, therefore I got stuck with lilo. I spent about 30 minutes reading up on how lilo works again, and quickly decided it wasn't that worth it to me, so I just reinstalled. One hour later I had a perfectly working ubuntu install again. With lilo. 
Now I have something like 46 updates that I can install. You can bet I won't be running any more updates to kernel-images and such until I feel well reassured by ubuntu that it is safe, even for lilo users. 

cheers.

P.S.
and oh yeah, it would be nice to get some aknowledgement from ubuntu regarding this update problem, and some kind of an idea on when we can expect an update that doesn't do this.

thanks

---

### Post by confused57 on 2007-05-30
You're right, it's more than a grub issue...the Developers have a difficult job and it's hard to predict how kernel updates will affect certain hardware and configurations, they do a fantastic job in spite of these limitations...

It might be revealing if someone had:
```
sudo fdisk -l
gedit /boot/grub/menu.lst
gedit /etc/fstab
gedit /boot/grub/device.map
```

before & after the latest Feisty kernel update...especially users with multiple hard drives, SATA & IDE.

---

