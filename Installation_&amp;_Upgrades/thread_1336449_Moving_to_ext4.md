---
title: "Moving to ext4"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by smoczyna on 2009-11-24
I'm wondering about save and efficient move to ext4 system. It is said that live upgrade don't make the system fully use the advantages of ext4 so how to do that without reinstalling the system and all of the applications.

If I do this like that:
- move everything from the ext3 partition to the spare one
- upgrade partition to ext4 using GParted
- move all files back 
Is it right way and enough to do to enjoy faster system?

---

### Post by phillw on 2009-11-24
Well, it's sorta what I'm going to be doing. I use a backup script based on [http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)  For anything major, like updating from 9.04 --> 9.10, major stuff for my LAMP installation etc.

You end up with a tar file which is, basically, a 'photo-copy' of your installation - which can then be extracted back onto the system.

Sounds like a plan to me !! - If everything goes horribly wrong, you can always put it back to ext3 - your backup will be safe. Doing the backup from a LiveCD is a good bet, as that means your current installation will not be actively being used. (Although I don't)

```
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/media --exclude=/mnt --exclude=/sys --exclude=/home/phillw/Desktop/PhillzMuzic --exclude=/tmp /

```  Is mine, reading that thread will let you learn all about it & customising it for your own use.

Regards,

Phill.

---

