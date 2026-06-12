---
title: "Replacing Ubuntu Studio 9.10 32 bit with Ubuntu 9.10 64 bit (Reinstall)"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by Sefram on 2010-01-29
Hello!

I'm new to Ubuntu (Linux in general). Ive recently installed the Ubuntu Studio 9.10 32 bit. I  like it a lot, but i thought i could try the 64 bit version (my processor is a 64 bit). So after some forum research i realised i had to do a reinstall. However after downloading the amd64.iso and trying to install it, the (graphical) install manager only gives me the options to partition the hard drive and keep the 32 bit and the 64 bit versions of Ubuntu along with Vista 32 bit which is also there (dual boot) or to format the whole drive, which isn't an option really.

What i want to do is to get rid of Ubuntu 32 and make a clean install of Ubuntu 64 on the same partition (don't care about keeping settings and data), keeping Vista at the same time, cause I don't really need two versions of Ubuntu :)

Thanks in advance for any help!

---

### Post by audiomick on 2010-01-29
Choose the manual partitioning option and point the installer at the partitions the existing install is on.

---

### Post by myth1914 on 2010-01-29
There should also be an option to "remove all linux partitions"  Is this not an option?

---

### Post by Sefram on 2010-01-30
OK, here are the "screenshots" (sorry, i had to make them with a camera :)).

The first one shows my options. Since I'm not satisfied with the first two options, I go for the third one: "Specify the partitions manually (advanced)".

The second screenshot shows the "manual menu". The sda1 (ntfs) and sda2 (ntfs) (obviously) represent my Vista partition and sda3 (ntfs) is my data partition so i don't alter them. The sda5 (ext4) and sda6 (linux-swap) is the partition currently used by Ubuntu 9.10 32 bit.

What is my next step? I right-click the sda5 and get a window with some options (format, mount point etc), but since I'm ignorant of those I'm too scared to proceed...

:)

---

### Post by oldfred on 2010-01-30
Just choose the mount points. Root (/) will be sda5 and swap sda6. If you had a separate /home you could also choose it (but then without formating). It will reformat and you will lose all data in your old install. 

If you have any settings in /home and it is part of your root you can copy those before reinstalling. Be sure to show hidden files before copying if using Nautilus.

---

### Post by Sefram on 2010-01-31
Thanks for your advice!

The system installed fine and everything works just as it has to!

:))))))))

---

### Post by mmercado on 2010-03-19
I had the exact same problem except I had Ubuntu 9.10 (not Ubuntu Studio) and I had multiple partitions that I was willing to erase. Ubuntu Studio 9.10 64 bit installation interface was not as "pretty" as the installer for Ubuntu 9.10 including the fact that the partition module did not give me the option to use all linux partitions (not sure if the other installer had it either). This was a little intimidating but it's not so bad. Only need to be careful when you press 'Enter','Space' or the arrow keys. What I did was delete all partitions except for 1 and 2 (because I knew those were being used by Windows) and, after that, I chose "Guided partition to use all continuos free space" or something like that. I don't remember exactly if I first chose "Manual" in order to delete the partitions. After deleting them, I had access to the "Guided Partition..." option.

---

