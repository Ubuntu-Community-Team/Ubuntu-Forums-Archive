---
title: "Multiple Hardisk and Ubuntu 6.10 Desktop"
date: 2006-12-20
forum: Installation &amp; Upgrades
---

### Post by blahfod on 2006-12-20
Hey guys, 

I have made the move to Ubuntu and will never look back, however, looking forward, i need a little help.

This is my issue. I have one 80GB IDE harddrive and one 300GB Sata drive all in the same box. I have installed ubuntu 6.10 and all it's partitions on the 80GB drive. I want to use the 300 gb drive as a data drive only (ie. music, movies, pictures, emulator games). I have painstakingly got to the point now (with a lot of reading in these forums) where i have managed to format the 300gb hardrive from ntfs into ext3. I moved all of my media that was on there previously by mounting the sata drive in ubuntu. I had hoped that once i formated it into ext3 and moved all my files back that it would be "recognized", for lack of a better word, by ubuntu and displayed in the places->computer menu. But alas it is not. Am i stuck with having to mount this drive to access it. Is there a way to have it displayed in the places ->computer menu? Also, I am also a little frustrated by the permissions required to access the sata drive while mounted. As i plan to share this drive with the other 2 computers running ubuntu on my network i would like to have unrestricted access to it, what would be the quickest way of accomplishing that?

great community, a wealth of knowledge and forgive my if i am asking silly questions!
thank you in advance
FOD

---

### Post by kidders on 2006-12-21
Hi there,

> Am i stuck with having to mount this drive to access it.Any filesystem you want to use has to be mounted. Perhaps you'd rather it happened automatically though? You can add a line to your /etc/fstab for that :-)

Permissions-wise, your Ubuntu box will do whatever you ask it to ... check out who owns the files and directories you want more access to, and what their permissions are. You can change these with "chown" and "chmod", to make them a little less restrictive.

Additionally, you'll need to add a line to /etc/exports (assuming you're using NFS to share files with your other Linux boxes) to give them access to your stuff.

So, try something like this:

/etc/fstab:```
/dev/sdb1 /mnt/shared ext3 defaults 0 0
```
/etc/exports:```
/mnt/shared 192.168.0.0/24(rw,async,root_squash)
```

```
mount /mnt/shared
chown -R username:group /mnt/shared
chmod -R 644 /mnt/shared
chmod -R ugo+X /mnt/shared
```

---

