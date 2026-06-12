---
title: "Advance Partition Unity/Gnome 3/Windows 7"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by steigerjb on 2011-05-11
Hi, Im getting a new computer from System76 real soon. It was supposed to be shipped yesterday but we'll see. Anyway, it will have a 1TB HDD with Ubuntu 10.10 Maverick Meerkat.  I want to reformat the drive and do some kind of advanced partitioning.  I want to have 2 installs of Ubuntu11.04, that way I can have Unity AND Gnome 3.  Is there a way I can partition it so they share the home and swap partitions? (2.  / partitions, 1 /home and 1 swap) How would I do that?

I will also need 2 partitions for Windows 7 which I use for work. (No, I do not want to use VirtualBox) My Windows 7 cd creates a second system reserve partition. I don't know if this will make me run out of partitions.  I hear you can only have a max of 4.  My idea above has 4 partitions for Ubuntu alone.

Thoughts?

---

### Post by Quackers on 2011-05-11
It will depend on how the system is partitioned when it arrives, but what you want will certainly be possible.
The swap partition can certainly be shared but I would advise against sharing a home partition between a Unity based system and a Gnome3 based system. I would keep those separate as Gnome3 is still experimental in Ubuntu afaik.

---

### Post by steigerjb on 2011-05-11
> **Quackers said:**
> It will depend on how the system is partitioned when it arrives, but what you want will certainly be possible.
The swap partition can certainly be shared but I would advise against sharing a home partition between a Unity based system and a Gnome3 based system. I would keep those separate as Gnome3 is still experimental in Ubuntu afaik.

From what i hear, system76 systems have the 3 partitions. / /home swap

---

### Post by Quackers on 2011-05-11
Yes, but it will matter whether they are primary partitions or logical partitions.

---

### Post by steigerjb on 2011-05-11
> **Quackers said:**
> Yes, but it will matter whether they are primary partitions or logical partitions.

1primary, 2 logical

---

### Post by Quackers on 2011-05-11
Ok thanks.
Can you explain exactly what you want to do please?
Do you have an official Windows 7 installation disc?

---

### Post by steigerjb on 2011-05-11
> **Quackers said:**
> Ok thanks.
Can you explain exactly what you want to do please?
Do you have an official Windows 7 installation disc?

I bought it online. Got a Windows 7 usb stick.

1TB HDD:

Im going to wipe the drive clean.

I'll first do a small Windows 7 partition for work. About 30 GBs.

Then I want 2 installs of Ubuntu.

How should I partition it? I've alway done it like [http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml) but I have never done it with 2 installs before. You were saying before sharing partitions is a bad idea?

---

### Post by Quackers on 2011-05-11
Sharing a home partition is ok, but not sharing a home folder. In other words you can use the same partition for multiple Linux systems as /home, but within that partition there should be separate home folders for each system.
I see 2 choices for Windows installation. It's usually simpler to install Windows first. The first is to just install Windows to the drive (over-writing what's on there already). Windows 7 will probably use 2 primary partitions for this installation. This is ok as 4 primary partitions are allowed on an mbr partitioned disc, one of which can be an extended partition.
The problem with this method is that it will use the whole disc (1TB) and you would then need to defragment Windows' C: partition then shrink it to what size you want it to be (or to what size it will allow you to shrink it to).
You will then be able to create an extended partition with many logical partitions within it for your Linux installations.

The alternative would be to boot from a gparted live cd or similar, or an Ubuntu live cd and choose "try ubuntu". Then when the desktop loads you can open gparted and delete all partitions on the hard drive with it.
You can then create a primary partition of NTFS type of the size you want Windows to be. Windows may then install to that one partition (depending on the installation media, maybe).
Then you can create an extended partition and then within that you can create as many logical partitions as you want to, into which your Linux systems can be installed.

---

### Post by steigerjb on 2011-05-11
> **Quackers said:**
> Sharing a home partition is ok, but not sharing a home folder. In other words you can use the same partition for multiple Linux systems as /home, but within that partition there should be separate home folders for each system.
I see 2 choices for Windows installation. It's usually simpler to install Windows first. The first is to just install Windows to the drive (over-writing what's on there already). Windows 7 will probably use 2 primary partitions for this installation. This is ok as 4 primary partitions are allowed on an mbr partitioned disc, one of which can be an extended partition.
The problem with this method is that it will use the whole disc (1TB) and you would then need to defragment Windows' C: partition then shrink it to what size you want it to be (or to what size it will allow you to shrink it to).
You will then be able to create an extended partition with many logical partitions within it for your Linux installations.

The alternative would be to boot from a gparted live cd or similar, or an Ubuntu live cd and choose "try ubuntu". Then when the desktop loads you can open gparted and delete all partitions on the hard drive with it.
You can then create a primary partition of NTFS type of the size you want Windows to be. Windows may then install to that one partition (depending on the installation media, maybe).
Then you can create an extended partition and then within that you can create as many logical partitions as you want to, into which your Linux systems can be installed.
  
I was going to delete all the partitions with gparted, the Windows disk creates the partitions.

Can you spell out doing the 2 Ubuntu installs for me? Like in that article. After I install Windows, I should have around 1000gb free unallocated space. Please spell out partitioning and creating 2 home folders.

---

### Post by Quackers on 2011-05-11
Once Windows is installed you should be able to boot from the Ubuntu live cd and install Ubuntu using the manual partitioning choice (or "something else" in 11.04). In this part you can create your root partition (mount point of "/" and your separate home partition (mount point of "/home").
In this part you should probably select "logical" as partition type rather than the default "primary" type. Look out for that.
The second Ubuntu installation is done the same way except that you select the /home partition that you made for the first installation and give that same partition the mount point /home.
The separate home folders would be created if you use different user names on each installation, for instance.

---

### Post by steigerjb on 2011-05-12
> **Quackers said:**
> Once Windows is installed you should be able to boot from the Ubuntu live cd and install Ubuntu using the manual partitioning choice (or "something else" in 11.04). In this part you can create your root partition (mount point of "/" and your separate home partition (mount point of "/home").
In this part you should probably select "logical" as partition type rather than the default "primary" type. Look out for that.
The second Ubuntu installation is done the same way except that you select the /home partition that you made for the first installation and give that same partition the mount point /home.
The separate home folders would be created if you use different user names on each installation, for instance.

Ok

---

### Post by srs5694 on 2011-05-12
> **steigerjb said:**
> I want to have 2 installs of Ubuntu11.04, that way I can have Unity AND Gnome 3.

That shouldn't be necessary. On most Linux systems, including Ubuntu, you can install multiple desktop environments (Unity, GNOME, KDE, Xfce, etc.) and select which one to use when you log in. This is *much* simpler and more convenient than dual-booting to switch between desktop environments.

That said, I haven't yet installed Ubuntu 11.04 on any "real" computers, just in a VirtualBox environment, which doesn't run Unity (it drops back to GNOME). I've just done a quick test, though, and it works as expected with a selection of the default (GNOME, marked as "Ubuntu" in the menu), Xfce, and IceWM -- see the attached screen shot to see where you make the selection of which environment to run. (This is in the login screen, which you won't normally see if you tell Ubuntu to log in automatically. You must then select the "log out" to get to the login screen if you want to change your desktop environment.)

---

### Post by steigerjb on 2011-05-12
> **srs5694 said:**
> That shouldn't be necessary. On most Linux systems, including Ubuntu, you can install multiple desktop environments (Unity, GNOME, KDE, Xfce, etc.) and select which one to use when you log in. This is *much* simpler and more convenient than dual-booting to switch between desktop environments.

That said, I haven't yet installed Ubuntu 11.04 on any "real" computers, just in a VirtualBox environment, which doesn't run Unity (it drops back to GNOME). I've just done a quick test, though, and it works as expected with a selection of the default (GNOME, marked as "Ubuntu" in the menu), Xfce, and IceWM -- see the attached screen shot to see where you make the selection of which environment to run. (This is in the login screen, which you won't normally see if you tell Ubuntu to log in automatically. You must then select the "log out" to get to the login screen if you want to change your desktop environment.)

It is necessary.  You can't have Unity and Gnome 3.  Gnome 3 breaks Unity.

---

### Post by Quackers on 2011-05-12
Actually I have a similar setup as the one you intend to have. For the same reason :-)
However, some people have indeed got Unity and Gnome 3 to work on the same installation (though I still don't).
Posts 15 & 17 here
[http://ubuntuforums.org/showthread.php?t=1745454&page=2](http://ubuntuforums.org/showthread.php?t=1745454&page=2)

---

### Post by Bonster on 2011-05-12
primary (windows), primary(linux), logical(other linuxes)

1tb Drive
primary:
50gb windows
10gb ubuntu 10.10  username-main

logical:
10gb ubuntu unity  username-unity
10gb gnome shell   username-shell
20-30gb /home
886gb /data
2-4gb swap

your /home is only going to be use for temp files and config settings (.folders). Making different usernames-(main|unity|shell) for each distro avoids conflicts, while still shares the same partition.


your /data will have all ur stuff like those Video Music Documents Pictures folder..etc. These will be linked using symlinks so u can use it on any linux distro.

---

### Post by srs5694 on 2011-05-12
> **steigerjb said:**
> It is necessary.  You can't have Unity and Gnome 3.  Gnome 3 breaks Unity.

Really? If that's true, I'd steer clear of the whole OS, since that suggests a level of misconfiguration (in the default setup) that's frightening. Linux desktop environments are *supposed* to be able to coexist on the same machine, although not necessarily run simultaneously for a single session. If they can't get this detail right, what else have they messed up? (Of course, there are lots of posts here from unhappy upgraders, so I guess they document the "what else....")

FWIW, from what I've seen, I'm underwhelmed by both Unity and GNOME 3; however, I haven't used either of them enough to make a final judgment. Maybe there's some hidden power or elegance there that I've just missed so far.

---

