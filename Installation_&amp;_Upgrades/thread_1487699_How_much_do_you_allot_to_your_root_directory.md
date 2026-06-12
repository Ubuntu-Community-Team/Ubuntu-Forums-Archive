---
title: "How much do you allot to your root directory?"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by Rytron on 2010-05-19
Hi.
If you manually partition Ubuntu Linux; how much do you allot to your root directory? If someone installs many games and software, should they use a very large root directory such as 30GB or more?

---

### Post by darkod on 2010-05-19
Another thing it depends on is whether you have separate /home partition or Home is part of /. Because with saving large files (videos/music/photos) in your Home, you have to calculate that space in / also.

For software, ubuntu is not as space demanding as windows. For games, I have no clue, i guess it depends on the particular game.

Otherwise, the basic default install is more or less 3GB - 3.5GB.

30GB sounds very good, but it depends on Home as explained above. If you keep 25GB of photos, that doesn't leave much of the 30GB for the rest, right?

---

### Post by VeeDubb on 2010-05-19
I alloted 155GB to mine.

I have a large amount of games installed, including many commercial games installed through cedega, which I have set up to use /cedega instead of a folder in my home directory, making games installed that way available to all users.

Even at that, I don't have anywhere near my whole / full.  The biggest reason is that I bought a 1TB drive to use for /home, and it was easier just use my existing 160GB drive for / and call it good than to throw it out or get creative with LVM.

---

### Post by Rytron on 2010-05-19
> **darkod said:**
> Another thing it depends on is whether you have separate /home partition or Home is part of /. Because with saving large files (videos/music/photos) in your Home, you have to calculate that space in / also.

For software, ubuntu is not as space demanding as windows. For games, I have no clue, i guess it depends on the particular game.

Otherwise, the basic default install is more or less 3GB - 3.5GB.

30GB sounds very good, but it depends on Home as explained above. If you keep 25GB of photos, that doesn't leave much of the 30GB for the rest, right?

Hi darkod.
Sorry, I should have added that root and home would be separate partitions.

---

### Post by tjajab on 2010-05-19
It depends on many factors.
1) As darkod says, will you have /home on the same partition?
2) Are you planning to install 3rd party games on the same partition or in a separate /home or /opt partition?
3) How much space is available?

I would say at least 20GB if you would like to use it without worrying about space issues. 30GB is even better. I assume you have music and video on another drive or partition.

---

### Post by darkod on 2010-05-19
> **Rytron said:**
> Hi darkod.
Sorry, I should have added that root and home would be separate partitions.

In that case, unless your games are really huge, 30GB is more than plenty.

Another idea: If you will be running only ubuntu (not dual boot with windows), why don't you take a look at LVM? It's perfect tool for single boot systems because it allows you to specify partitions sizes, and then grow them without needing to format them again.

Here is one tutorial for 8.10 but it's the same for the newer versions:
[http://linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/all/1/](http://linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/all/1/)

You can also find plenty of info for reading on LVM on google.

For LVM you will need to install from the alternate image, not the standard desktop (liveCD).

---

### Post by Rytron on 2010-05-19
> **darkod said:**
> In that case, unless your games are really huge, 30GB is more than plenty.

Another idea: If you will be running only ubuntu (not dual boot with windows), why don't you take a look at LVM? It's perfect tool for single boot systems because it allows you to specify partitions sizes, and then grow them without needing to format them again.

Here is one tutorial for 8.10 but it's the same for the newer versions:
[http://linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/all/1/](http://linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/all/1/)

You can also find plenty of info for reading on LVM on google.

For LVM you will need to install from the alternate image, not the standard desktop (liveCD).

Yes, 30GB looks ample. Thank you darkod, I will also check out LVM. :)

---

