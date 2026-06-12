---
title: "I need help partitioning my ubuntu install"
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by nullbyte0 on 2008-07-06
Alright, so I'm a complete linux newb.

So far I understand that I need a /, /usr/,/home/, and swap partition.  I already have windows xp installed on the same drive though.  I'm supposed to make an extended partition to include all those, but I'm not too sure about how to do that.

Here is a screenshot of how I have it now.
[http://img365.imageshack.us/img365/644/partitiongp0.png](http://img365.imageshack.us/img365/644/partitiongp0.png)

Can you provide me with step by step instructions on how to proceed?

sda1 is my main xp partition.
sda2 is a back up partition for xp.
sda3 is my current /.
sdb1 is a storage drive that is not to be touched.

Thanks :)

---

### Post by nullbyte0 on 2008-07-06
Oh and the cd is version 7.10.

---

### Post by Shai Hulud on 2008-07-06
It is not mandatory to have /usr and /home at separate partitions. You can go with just / and a swap partition :)

---

### Post by wpshooter on 2008-07-06
> **Shai Hulud said:**
> It is not mandatory to have /usr and /home at separate partitions. You can go with just / and a swap partition :)

Although it is not mandatory to have a /home partition, I would suggest that you would be VERY wise to have one.

---

### Post by Sef on 2008-07-06
> Although it is not mandatory to have a /home partition, I would suggest that you would be VERY wise to have one.

It is best to have a home partition in case something happens to the root partition.  If they are separate, usually you won't lose your information.

---

### Post by eto_D on 2008-07-07
> **nullbyte0 said:**
> Alright, so I'm a complete linux newb.

Can you provide me with step by step instructions on how to proceed?

Thanks :)

I am sitting in the same boat and would also be curious to hear about more detailed instructions on how to proceed with the partitioning as originally requested by the op.

---

### Post by VMC on 2008-07-07
This topic has come up a few times of late. You will get many opinions on the subject. To the person new to Linux this can be confusing at best.

So here's mine. What good will it do to have multiple partitions if the hard drive fails. I keep hearing its good have a "/home" in case something happens to "/" partition. Well in reverse, what will you do if something happens to the "/home" partition.

I used the default setup with just one partition "/" and a swap "/swap" partition. I could eliminate swap partition and just have a swap file instead.

I think for the average home user, you don't need all those partitions. It's old school.

Instead, backup is the best solution. Backup to an external hard drive somewhere.

 The only time I've seen a need was in large servers or some exotic system.

I just keep a current backup of my ONE partition and that's it. It's easy to re-create swap. Unless your running some sort of RAID system, data will be lost anyway.

If its valuable pictures or financial data, or anything of vaule keep a backup off-site.

I believe in the "KISS" concept.

---

### Post by estyles on 2008-07-07
I think the reason that it's smart to have a /home partition is that there's always a chance of screwing up your installation by messing with setting and installing programs.  If worst comes to worst and you mess up your Ubuntu installation beyond repair, you can always blow up the entire partition and reinstall Ubuntu.  If you do so, it'll be easier to save your documents if you have them 100% separated from your OS partition.

---

### Post by eto_D on 2008-07-07
Guys, you are fixated on how many partitions are to be created. 
Not sure about the op, but I would just like to get started and I am willing to go with either suggestion. If only I knew how to proceed 

> Can you provide me with step by step instructions on how to proceed?

sda1 is my main xp partition.
sda2 is a back up partition for xp.
sda3 is my current /.
sdb1 is a storage drive that is not to be touched.

Thanks 

---

