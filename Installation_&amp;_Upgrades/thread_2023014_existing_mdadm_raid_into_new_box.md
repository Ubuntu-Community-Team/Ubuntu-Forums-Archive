---
title: "existing mdadm raid into new box"
date: 2012-07-11
forum: Installation &amp; Upgrades
---

### Post by Saicho on 2012-07-11
I have an ancient ubuntu installation that I've been using for years in a box. The box has 3 physical drives. One drive that has the OS and / is mounted there. Two more drives are present in raid1 using mdadm where /home is mounted.

I would like to install a fresh modern ubuntu in a new box and move the existing mdadm raid over using the same setup. I'm comfortable installing ubuntu and mounting / on a disk.

Then I'd like to move the 2 physical raid disks over, get mdadm to recognize the raid, and mount /home there again.

Is there anything I need to watch out for, particularly with the order I do things? Obviously install a new ubuntu first. Then should I delete all users besides root? Will mounting /home get confused from all the data already there from an old installation? Do I need to create the same usernames?

Thanks in advance!

---

### Post by darkod on 2012-07-12
I would move the raid disks too, before installing the new OS. That can allow them to be detected during install. But for that you would need to use the Alternate CD I guess, since it has built-in support for raid and lvm.
You should be able to do it with the live cd too, just boot it into live mode first, add the mdadm package in the live environment, and then click the Install icon on the desktop. That should start the installer with mdadm available.

As far as /home is concerned, when using existing /home (with or without raid), the usual rule is to create the first user during installation the same as the first user on the old system. Once you have the OS installed you can add all the other users since their Home folders will be kept too.

If you add the raid disks before the install it helps with one more thing. You can actually use the raided /home as /home during the install (provided mdadm can see it as explained above). That will make the system use the "correct" /home from the start.
If you only install the OS first, it will create home as folder inside /, and after adding the raid disks you have to play around and tell it to use the array as /home. That's not too complicated, but why do it if you can "attach" it during the installation.

---

