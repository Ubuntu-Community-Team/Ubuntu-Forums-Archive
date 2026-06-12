---
title: "Messed up mounts points."
date: 2012-04-06
forum: Installation &amp; Upgrades
---

### Post by nipunshakya on 2012-04-06
Hello everyone. I recently moved completely to ubuntu. The installation was successful, but i messed up something pretty bad. Here's the scenario..please refer to pic attached.

1. sda1 had windows previously, still has the boot flag.
2. i booted to live cd, selected sd1, formatted it and made it free space.
3. unknown to what the option under **'mount as: do not use this partition' **during the formatting process would result to, i just mounted the free space as /usr ...and thats anoying.

I know /usr is just for installed programs, which eventually wouldn't take up my 60 Gib. I feel i had been a fool to completely mess up my installations... 

So gurus,
1. is there a way that i can do something with the /usr being moved back to my root?
The /usr partition is a primary one and my whole system has been installed to extended partition. But I wish to move all my current /usr stuffs to the root itself and then free the sda1 with 60 gb and then extend it to sda4. Is it possible? How can i achieve it?


2. Even if i go for a clean install, i will eventually use only the extended partitions (sda5.sda6.sda7) for linux setup and format the sda1. But while formatting, what should i select on the **mount as:  **option so that i can use the partition in future? i just want it to be used as sda3 and sda4 in future. Any ideas gurus?


Regards,WinuxUser

---

### Post by darkod on 2012-04-07
I would suggest you never format partition that you do not plan to use immediately with the installer. You have Gparted for partitions management once you get ubuntu installed. If you plan ot use a partition immediately, then in mount as you use the mount point according to what you plan using it for. If not, don't touch that partition during the install, you can always use it later.

So, for example, if in future you want to use the 60GB simply as general storage space, make your install on sda5, sda6 and sda7 as normal. Don't touch the 60GB.

After ubuntu is running, delete that partition and create one ntfs or ext4 partition from that space. That's it.

Now, here is what you could try to move /usr to /. I am no guru, so make a FULL BACKUP FIRST!!!

Boot into live mode with your ubuntu cd, you need to work from live mode, not from your hdd ubuntu.
1. Open /dev/sda5 and create usr folder in it.
2. Open /dev/sda1 and copy everything to /dev/sda5/usr.
3. On /dev/sda5 open /etc/fstab and comment out the /usr entry. Just put the # symbol in front of that line mounting /usr.

That should stop it mounting /dev/sda1 as /usr and trying to use the /usr folder created in /. At least in theory.

If it doesn't work, you can undo the fstab and delete the usr folder you created on / and it should continue working.

In case it works, use it like that for a while to make sure it's working fine. After that you can delete the /dev/sda1 partition (again from live mode), and expand first /dev/sda2 to include that unallocated space, and later /dev/sda5 to include it.

Since your ubuntu is on logical partitions, I believe you first will need to expand the extended partition /dev/sda2 and only after that the /dev/sda5.

---

### Post by nipunshakya on 2012-04-07
> **darkod said:**
> 
After ubuntu is running, delete that partition and create one ntfs or ext4 partition from that space. That's it.


Thats the information i needed. It was fool of me to not to dig things in first place. :p Such a simple thing it seems now, and back then it was a big issue for me.

> **darkod said:**
> Now, here is what you could try to move /usr to /. I am no guru, so make a FULL BACKUP FIRST!!!

Boot into live mode with your ubuntu cd, you need to work from live mode, not from your hdd ubuntu.
1. Open /dev/sda5 and create usr folder in it.
2. Open /dev/sda1 and copy everything to /dev/sda5/usr.
3. On /dev/sda5 open /etc/fstab and comment out the /usr entry. Just put the # symbol in front of that line mounting /usr.

That should stop it mounting /dev/sda1 as /usr and trying to use the /usr folder created in /. At least in theory.

If it doesn't work, you can undo the fstab and delete the usr folder you created on / and it should continue working.

In case it works, use it like that for a while to make sure it's working fine. After that you can delete the /dev/sda1 partition (again from live mode), and expand first /dev/sda2 to include that unallocated space, and later /dev/sda5 to include it.

Since your ubuntu is on logical partitions, I believe you first will need to expand the extended partition /dev/sda2 and only after that the /dev/sda5.

I didn't give a second thought to that.:mad: Could have been great if i tried that out too...but i hurriedly formatted the sda1,sd5,sda6 and sda7 and went on with fresh installation on the combined free space created from those partitions. 

Though i have a fully functioning system running now, still my confusions are, lets say my sda1 was labeled **unknown** during the installation process (seeing which made me panic and i formatted it to /usr previously:mad:) , then what would be the scenario of that partition?? Will still not touching it during installations and formatting it using gparted later after installation do the work? 

And, if , during the installation, i select the sda1 and change it to **do not use this partition** , then will that partition still show up after installation? will i be able to use that partition in future for storage ??


Just curious about future partitioning things so that i don't mess up again. I really appreciated your help. Thanks. :)

Regards,WinuxUser):P

---

### Post by darkod on 2012-04-07
Linux works with mount points. The 'do not use' as I understand it, will not create any mount point for that partition. In other words, leave me alone...

So, after that you end up with ext4 partition for example, with no mount point. Regardless whether you used the 'do not use' or used Gparted later and created a new partition from the 60GB. Once you have it as new, unused ext4 partition, you will need to edit /etc/fstab and add something like:
/dev/sda1 /data ext4 defaults 0 0

That will mount /dev/sda1 as mount point /data at every boot. You can use that partition at mount point /data.

This is just one example, you can use another mount point, or even /data1, /data2, etc for better organization of your structure.

More or less, that is how you could use existing partition that was not used during installation. You are flexible to do many things by simply defining mount points and making entries in /etc/fstab.

---

### Post by skabople on 2012-04-07
Hello,

Ok, the "Label" of a partition or drive is nothing more than a label. For example

/dev/sda1 could be mounted as /usr but is labeled WTF

Generally the purpose of labeling a partition is for simple reading for what the partition is for. Example:

Lets say /dev/sda2 is mounted at /home.
```
e2label /dev/sda2 /home
```

Then in /etc/fstab you can put something like:
```
LABEL=/home    /home      ext3  defaults,noatime,nodiratime 0 2
```

Now as for your partitioning "scheme" I will say is not too good... 
/dev/sda1 should be mounted as /boot with approx 106MB of space
/dev/sda2 extended
/dev/sda5 mounted as /
/dev/sda... and so on and so on.

I'm not exactly sure what you're confused about but I hope this answers your question.

---

### Post by nipunshakya on 2012-04-07
> **skabople said:**
> Hello,
I'm not exactly sure what you're confused about but I hope this answers your question.


My clear query was available on the first post which was then updated on third post. But thanks for the piece of info u gave too.

---

