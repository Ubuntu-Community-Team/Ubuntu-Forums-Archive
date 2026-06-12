---
title: "[SOLVED] Unable to mount CD or DVD"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by fparedesg on 2008-04-04
I'm having some problems with my DVD and CD drives. I can't mount them, and I can't use them. The DVD is the master, and the CD is the slave. My computer has Windows Vista, and Ubuntu 7.10. The only problem is that my Internet connection is not working yet, and I need to use an installation CD to be able to use it, and I can't do that if the CD drive is not mounted.

This is what I put on the terminal and what I got:
```
federico@tiburon:~$ sudo mount -t udf /dev/scd0 /media/cdrom0/
mount: special device /dev/scd0 does not exist
```
When I check in the /dev folder, there is no scd0 file.

So I put:
```
sudo gedit /etc/fstab
```
This is what I got on the last three lines:
```
UUID=e081e30a-cae5-412b-8f40-dda7ddd868ec none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
```

Please, if you can help me, thank you very much.. :)

---

### Post by sobepmp on 2008-04-13
I'm having the same problem. How did you fix it?

---

### Post by Aim9b on 2008-04-14
I have this as well. I installed ubuntu 7.1 & now I can't mount the CD-Rom.  My /etc/fstab shows it's there, but I get the same message when I try to mount it.  What was the solution?  Thanks.

---

### Post by fparedesg on 2008-04-14
It was a problem with the physical drive, both drives were working fine (I have a DVD master drive, and a CD slave drive), and both worked with Windows Vista, and I even installed Ubuntu with a Live CD, so I don't really know what happened, but I noticed some problems with the DVD master in Vista, so I turned off the computer and disconnected the DVD drive, leaving the CD drive connected (I also removed the Master/Slave jumper), and it worked. I don't think this will help you much, so sorry, but check to make sure that it's properly connected.

---

