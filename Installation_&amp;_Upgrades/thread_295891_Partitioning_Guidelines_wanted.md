---
title: "Partitioning Guidelines wanted"
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by Omicron1 on 2006-11-08
Linux/Ubuntu newbie here. 
Best I can tell, the Ubuntu updates, and repository downloads are installed in the / (root) partition.
Assuming that to be correct, would I also be correct in thinking that when I set up the partitioning on my hard drive, I should make the root partition the biggest of all the partitions?
I have only a 40 GB drive to play with (and 512MB RAM) so this is my partitioning thinking:
/boot (100 MB)
/ (28.9 GB)
/home (10 GB)
swap 1 GB

I'm gathering that the /home partition is where I put any of the stuff I create like docs, images, music, etc.

Does this seem OK? 
Also, once I set these partitions while using the live-CD, all I do afterward is just continue with the installation? In other words, the Ubuntu installer will put the proper files in the /boot and / partitions  with no other intervention from me?

If I were to have 200 GB hard drive, would my partitioning thinking still be sensible?

Thanks for any help.

---

### Post by o_fortuna on 2006-11-08
A lot of that stuff isn't really necessary -- separating the boot partition just makes it more complicated.

Also, you want most of the data in /home -- your music and pictures will take up the majority of the space on your computer. That said, with a 40 GB hard drive, the best way to make sure you don't run out of space is to not separate anything out at all, and leave the installer with only /

If you're intent on splitting out, 10 GB is usually enough for /, and if you really want, keeping /boot won't hurt (but it just makes it more complicated). Once you set the partitions and press next, the installer takes care of everything, so nothing to worry about.

With a 200 GB hard drive, I would definitely recommend splitting out /home with something like 175 GB for /home and 25 GB for / and everything else.

---

### Post by Omicron1 on 2006-11-08
Thank you for your very quick reply.
I'm a bit surprised to hear that the /home partition will be the most used. Was I correct that any software and updates will go into root?
Also, if I partition as I described, will I be able to re-install Ubuntu (for whatever reason) and NOT lose my data?
Thanks again.

---

### Post by o_fortuna on 2006-11-08
To not lose your data, you'll need to have a separate home partition. Also, I'm absolutely positive that /home needs more space.

As an example, with a fresh Edgy installation (with a bunch of additional junk installed), I'm currently using just 2.5 GB. On /home, I'm using 18.6 GB -- about 3.5 GB of music, 3 GB of photos, and the rest are application files.

While the executables and apt downloads are installed in the root partition, they generally take up a pretty small amount of space compared with music and photos. Also, your home directory contains all the configuration for your apps, which take lots of space -- mine are almost a full gigabyte alone.

So yeah, /home definitely takes more space, and if you plan on reinstalling, you will lose your files and configuration for apps if you reinstall without a separate /home partition (so you should probably consider it, I guess) -- having /home separate will preserve your data through a re-installation.

You should still back up your music and documents and stuff, though.

---

### Post by Omicron1 on 2006-11-09
OK,
Thanks for all the info.
I'll set up my partitions accordingly.
Regards  :p

---

