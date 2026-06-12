---
title: "Re-mounting my /home (which is on a separate partition)"
date: 2011-04-11
forum: Installation &amp; Upgrades
---

### Post by linkunderscore on 2011-04-11
I haven't been using Ubuntu for a couple of years. Yesterday I decided to fire up my ubuntu box and upgraded from 8.04 to 10.10. 

The upgrade went fine, but when I boot it tells me that the /home dir cant be mounted. It allows me to Wait, Skip, or Manually mount it. If I skip I can log in and mount the partition that contains my /home folder so I know that nothing is corrupt. I'm sure my fstab just got overwritten during the upgrade, but, since its been so long, I don't recall how to (correctly) fix it back. 


[B]Cliffs: 
--Upgraded from 8.04 to 10.10
--/home dir is on a separate partition & is not mounting properly
--How do I set it up so that my /home dir mounts on boot? [/B]

I'd just try messing around with fstab myself, but I really don't want to lose any data. Hopefully someone on here can help me out.

---

### Post by coffeecat on 2011-04-11
Post the contents of your /etc/fstab file as well as the output of this terminal command:

```
sudo blkid
```

Then someone will be able to help you with whatever needs editing in /etc/fstab.

Don't forget to post both in code tags to keep the formatting.

---

### Post by linkunderscore on 2011-04-11
Will do. I'm at work atm so I will post as soon as I get home.

---

### Post by linkunderscore on 2011-04-11
The weirdest thing happened....

I shut down my computer before I went to work this morning, made this post while at work, then when I get home and boot up...its working? I don't know what happened but it found my /home dir I guess and everything seems to be in order. 

fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=469624e5-3217-4a7e-82c0-2dd69d75dba6 /               reiserfs notail          0       1


# /dev/sda3
UUID=eee54719-d059-4f16-9f40-6af60e24212e none            swap    sw              0       0
/dev/sda4             /home               reiserfs notail          0       1
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

blkid:
```
/dev/sda1: UUID="7EB866BBB8667197" TYPE="ntfs" 
/dev/sda2: UUID="469624e5-3217-4a7e-82c0-2dd69d75dba6" TYPE="reiserfs" 
/dev/sda3: UUID="eee54719-d059-4f16-9f40-6af60e24212e" TYPE="swap" 
/dev/sda4: UUID="fb13423e-6cd2-40de-8683-b85dafa6bde3" TYPE="reiserfs" 
/dev/sdb1: LABEL="PENDRIVE" UUID="525D-EBBE" TYPE="vfat" 
```

Let me know if there is something in there that is "buggy", but it seems to have fixed itself. :D

---

### Post by Dutch70 on 2011-04-11
Are you sure it's working correctly? 
lol, somebody had to ask...;)

I'm thinking you should have something like this in there...
[COLOR="Red"]
*I'm not advising you to add this, I'd just like to see what others have to say about it*.[/COLOR]

# home on /dev/sda4
UUID=fb13423e-6cd2-40de-8683-b85dafa6bde3 /home   reiserfs   auto,user,rw,  0    2

---

### Post by coffeecat on 2011-04-12
I agree with Dutch70 about using the UUID instead of '/dev/sda4' in the first field of your /home fstab line. It would be more reliable. I don't know about ideal mount options for reiserfs - I've not used reiserfs since it was the default filesystem in opensuse, about 2005/6.

---

### Post by Dutch70 on 2011-04-12
Yeah, I've never used reiserfs, so I certainly don't know about mount options for it. Maybe this site will offer some info.
[[COLOR="RoyalBlue"]What is the Linux fstab and How Does It Work?[/COLOR]]("http://www.howtogeek.com/howto/38125/htg-explains-what-is-the-linux-fstab-and-how-does-it-work/")

Edit: After looking it over, it doesn't look like they say anything about reiserfs mount options either.

I think yours would be more like this...
# /dev/sda4
UUID=fb13423e-6cd2-40de-8683-b85dafa6bde3             /home               reiserfs notail          0       1

---

