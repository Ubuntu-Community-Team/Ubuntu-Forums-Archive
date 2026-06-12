---
title: "[SOLVED] Ubuntu shows wrong amount of free disk space after cloning disk"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by gully on 2008-11-29
Hi, I recently upgraded from a 250gb IDE drive to a 500gb SATA drive.
I had 3 partitions on the IDE drive: linux swap, reiserfs (ubuntu hardy) and NTFS (win XP), sized about 2gb, 190gb and 25gb respectively.
The reiserfs partition contained about 170gb of files.

On the SATA drive I made the following partitions: 2gb linux swap, 350gb reiserfs and 120gb NTFS.

I used a gparted live cd to clone my disk (but I did reinstall win XP.) After the cloning was complete all I had to do was change the UUID's in grub to get ubuntu back.
The only problem was that ubuntu, as well as the gparted live cd, now display the wrong amount of free space on the reiserfs partition, they both show 20gb of free space, while it should be 180gb.

Gparted shows the reiserfs partition as a 350gb partition with 330gb of files on it, while ubuntu says some content is unreadable (it doesn't display the size of the partition) and says there is 20gb of free space left, while it says there are a lot more files on it then there should be.
Still, my home folder contains the right amount of files.

I've read that this can happen when cloning a disk, but I'd like to get that 160gb of disk space back without having to reinstall ubuntu.

If anyone can help me get my lost disk space back, please help me.

---

### Post by manishtech on 2008-11-29
Boot from Live cd and then find the partition name of the partition where ubuntu is installed e.g. /dev/sdxy which can be eg sdc3 , whatever you get. You can identify it by seeing reiserfs a filesystem named next to it when you do
```
sudo fdisk -l
```

Then for that partition run the command

```
fsck.reiserfs /dev/sdxy
```

or

```
reiserfsck /dev/sdxy
```

Am not sure of which command, since I havent used it personally.
Check this man page
[http://linux.die.net/man/8/reiserfsck](http://linux.die.net/man/8/reiserfsck)

---

### Post by gully on 2008-12-02
Reiserfsck did check my filesystem and all but it didn't fix the free space problem, but thanks anyway.

---

### Post by manishtech on 2008-12-02
You should use the **--rebuild-tree** option for fixing it.
Check it out here
[http://www.cyberciti.biz/tips/repairing-reiserfs-file-system-with-reiserfsck.html](http://www.cyberciti.biz/tips/repairing-reiserfs-file-system-with-reiserfsck.html)

---

### Post by gully on 2008-12-03
I did the rebuilt tree thingy, but now I only get a text based interface when I boot into ubuntu, it doesn't give errors and I can still login but there's no desktop or any gui whatsoever...

---

### Post by gully on 2008-12-03
Btw, the console screen I get is similar to this: [https://bugs.launchpad.net/ubuntu/+bug/103148](https://bugs.launchpad.net/ubuntu/+bug/103148) but it doesn't halt (I can login a few seconds after that message pops up), and I can't get to my desktop environment, I'm stuck in that console.

---

### Post by manishtech on 2008-12-04
When you logged in as command line. Type the command below to get into graphical mode

```
sudo init 3
```

---

### Post by gully on 2008-12-04
Doesn't work, neither do sudo dpkg-reconfigure xserver-xorg, sudo startx or sudo apt-get install ubuntu-desktop.

I'm beginning to suspect I'm really screwed and all because I ran reiserfsck, is it just me or is hardy the most bug-ridden OS ever?

I'm thinking about installing intrepid (hey, it can't be worse than hardy) on another partition and keep the current ubuntu partition as my home folder, of course that still doesn't fix the free disk space problem...

---

### Post by gully on 2008-12-07
I solved it using this: [http://pennsyvlania.ubuntuforums.org/showthread.php?p=6326576#post6326576](http://pennsyvlania.ubuntuforums.org/showthread.php?p=6326576#post6326576) .

---

