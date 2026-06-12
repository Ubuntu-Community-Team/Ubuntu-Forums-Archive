---
title: "[SOLVED] mounting LVM on startup"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by markdavidoff on 2008-08-12
I just re-installed ubuntu server 8, now with 2 HDDs.

My setup as follows:

80gb HDD:
8GB OS ext3 partition
3.3GB Swap Partition
(the remaining) LVM Partition

40GB HDD:
40GB LVM Partition

I created the LVM with a group called FileServer_LV_Group
and within that, a volume called FileServer_LV

I can successfully boot the OS, but I'm having trouble mounting the FileServer_LV volume to a directory /home/public

"public" has read-write-execute access to the owner and read-execute access to anonymous users.

naturally, i want the volume mounted as this directory with those permissions.

I also want the volume to mount on boot (in the fstab file)

Can anyone guide me through this? I have never done this before.

---

### Post by markdavidoff on 2008-08-13
*bump*

---

### Post by markdavidoff on 2008-08-15
come on! surely someone has had experience with LVM!!!???

---

### Post by markdavidoff on 2008-08-15
I figured it out:

Create a filesystem for each volume:

```
sudo mke2fs -j /dev/(VOLUME GROUP)/(VOLUME NAME)
```

(without the brackets)

I was then able to mount the volume without error!

I then gave the directory permissions:

```
sudo chmod u=rwx,g=rwx,o=rx
```

This allows read-write-execture access to the owner of the drive and the owner's group, and read-execute access to others (anonymous users)

I then assigned myself as the owner of the directory (and, thus, the drive):

```
sudo chown (username).(group) (directory)
```

in my case, sudo chown mark.users /home/public

and my smb.conf section for those that want:

```
[PUBLIC]
comment = Public Share
path  = /home/public
browseable = yes
guest ok = yes
read only = no
```

hope this helps!

---

