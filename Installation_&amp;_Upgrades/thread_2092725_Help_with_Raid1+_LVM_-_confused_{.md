---
title: "Help with Raid1+ LVM - confused :{"
date: 2012-12-08
forum: Installation &amp; Upgrades
---

### Post by bunglehaze on 2012-12-08
I am reinstalling 12.04 server again as I wanted to tweak the hard drive quotas and as it's not live as yet I can afford to play a little.

I only have a 2 disc setup, Raid 1 for the mirroring and I have been using a standard partitioned setup with root, home, var, tmp and swap, what I have read about LVM has me thinking that it will allow me to resize partitions if required rather than stick with the fixed quotas of a normal partition - this is of huge interest as it stops me leaving the size allocation too small for long term and not an issue to resize smaller if over allocated.

Or am I misunderstanding this?

In any case I have gone through the tutorials and tried to set things up as needed, paritions created as before, raid setup for each partition and then LVM setup as a single group and volume

In every attempt to continue after creating an LVM I get the notice that no root partition is selected and the install will not continue, I cannot seem to understand how I set the root partition any differently.

Please help, my head feels like it might explode.

---

### Post by darkod on 2012-12-08
The message is clear, you are trying to continue the installation without specifying a root partition.

It seems you are missing few details how LVM works. After you set up your raid1 software raid, select the raid device and set Use As physical device for LVM.

After that you need to go into Configure LVM.
You will need to set up a Volume Group, it can be only one, for example named VG1.
In that VG you need to set Logical Volumes. In LVM the LVs are like partitions in standard install. You need to create one LV for each mount point / partition you want to use. For example, in your case you might want to create LVs named:
LVroot
LVswap
LVhome
LVtmp
LVvar

Create these LVs with small size, but enough for the installation to finish. This will help you use the space more efficiently. Later you will grow the LVs when they start getting filled up, only when needed.

When the LVs are created, and you return to the partitions list, select the LVs one by one, and set their filesystem in the Use As field, and their mount point.

Once you set the LVroot mount point as /, the installer will allow you to continue. But if you want the other LVs to be used as /home, /var, /tmp and swap, you need to set all those mount points.

That's it.

---

### Post by bunglehaze on 2012-12-08
Ah thanks Darko, so it would seem I am trying to setup traditional partitions, then software raid (incidentally I do have hardware raid on my Dell server but read that software is often better) and THEN trying to create LVM.

I didnt see anywhere in the LVM settings to create mount points and thought I must have got it wrong somehow - I was just going to go back to standard partitioning through frustration but really could use the flexibility.

thanks

---

### Post by darkod on 2012-12-08
The filesystem and mount points are not set in the LVM settings in the true meaning of the word. You just create the LVs.

After that the LVs will show in the partitions list, the same way normal partitions show when you are installing without raid and lvm. So, you select them one by one, and set the correct filesystem and mount point for each.

When you are done, you continue the installation.

---

### Post by bunglehaze on 2012-12-08
Thanks, i'll give it a go and hopefully not be banging my head against my office wall in a little while :)

---

### Post by bunglehaze on 2012-12-08
You Sir, are amazing. That seems so much more painless than I have been making it and now appears to be belting along nicely. 

Thanks

---

### Post by darkod on 2012-12-08
No problem. Glad you got it going. Please mark the thread as Solved. You can do this in Thread Tools above the first post.

---

