---
title: "Reinstalling Ubuntu..."
date: 2005-11-03
forum: Installation &amp; Upgrades
---

### Post by guyomarj on 2005-11-03
Hi, I want to reinstall Ubuntu on a new hard drive, essentially to give him more swap memory. Here is my current system:

```
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hdd1     ext3    3.8G  1.9G  1.7G  53% /
tmpfs        tmpfs    253M     0  253M   0% /dev/shm
tmpfs        tmpfs    253M   13M  240M   5% /lib/modules/2.6.12-9-386/volatile
/dev/hdb6     ext3     18G  866M   16G   6% /home
/dev/hda1     ntfs    9.6G  7.1G  2.6G  74% /mnt/hdc
/dev/hdb1     vfat     39G   20G   20G  52% /mnt/hdd
/dev/hdb5     vfat     20G   13G  7.3G  63% /mnt/hde
```

I dual boot XP. As you can see, my "/home" is on another partition. 

The first thing I want to know: will I keep my current user account after the reinstall?

As I see it, the reinstallation will be "un jeu d'enfant":
[LIST]
[*]Unplug /dev/hdd
[*]Plug the new hard drive
[*]Partition it (giving 1G to swap)
[*]Install Ubuntu
[*]Customize it: Firefox 1.5, Thunderbird, Emacs, Eclipse, Java 1.5....
[/LIST]

I just need your approval :D (or your opinion).

---

### Post by coogor on 2005-11-04
you should mount your /home partition to /home afterwards. On creation of the user, you should be asked if the exisiting /home/jackuser should be used. Answer yes, and it's done.

(At least it worked that way on various SuSE-upgrades)

---

### Post by guyomarj on 2005-11-04
[QUOTE=coogor]you should mount your /home partition to /home **afterwards.** [/QUOTE]

@coogor: I don't understand what you mean by "afterwards"...

---

### Post by Arktis on 2005-11-04
Meaning when you run the installation, you will have to manually set your old home partition as /home during the partitioner phase.  You will find that all of your user account settings will be saved as they were before the reinstall.  Though, when I have done this, the installer has never asked me if I wanted to keep my old user account.  I have always just chosen the same username and password as I had before and everything has worked fine that way.

Anything custom you installed to root will have to be reinstalled of course, and any custom settings kept there will have to be reconfigured by you to get them the way you like again.  If you have any settings in your home dir that refer to custom stuff you added to root, they will obviously point to things that no longer exist, so you'll have to deal with that.  But again, in my experience, I've never had this problem.  But that may be due to the way I manage my files and settings.

In summation, your plan is sound, I've done the same before a few times, and if you are looking for approval as you say, you've got my mine for what it's worth.

---

### Post by guyomarj on 2005-11-04
Thx Arktis I'll try that. I think that I manage my files in such a way that I won't have any problem if the accounts aren't modified during the install.

By the way, I got 512Mg of RAM. How much swap memory do you think Ubuntu need? 1G ?

---

### Post by Arktis on 2005-11-05
I've got 512 megs of ram and I use a 1.5 gig swap which is probably too large... there's no really difinitive answer.  Most people seem to use twice their ram, so 1 gig is probably good.  Here, check [this](http://www.tldp.org/HOWTO/Partition/partition-4.html#SwapSize) out.

---

### Post by guyomarj on 2005-11-07
One hour ago, I opened my box, swap hard drives, put the Breezy CD install and crossed my fingers.... And now here I am :D My Ubuntu has now a 1G swap memory and I didn't lost any data! I'm an happy Geek!

I've just apt-get gdesklet and all my desklets are back... I'm starting thinking that I've been Ubuntized.

Thx for your help

---

