---
title: "GRUB2 Install Help"
date: 2009-01-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Streeterer on 2009-01-17
I am having problems with GRUB after switching my filesystem to EXT4 and I believe the problem is with my current GRUB not having EXT4 support. Currently GRUB boots directly to the console, ignoring my menu.lst, and thus I cannot access Ubuntu. How would I go about installing GRUB 1.96? Or, better yet, what might I do to remedy my current GRUB?

Thanks!

---

### Post by ShirishAg75 on 2009-01-17
grub does have ext4 support.

[https://edge.launchpad.net/ubuntu/+source/grub](https://edge.launchpad.net/ubuntu/+source/grub)

> 

            **[0.97-29ubuntu47]("https://edge.launchpad.net/ubuntu/+source/grub/0.97-29ubuntu47")**     
                                       Published        in        [jaunty]("https://edge.launchpad.net/ubuntu/jaunty/+source/grub")-release                        on 2009-01-06                                  
           grub (0.97-29ubuntu47) jaunty; urgency=low

  [ Colin King ]

  * New patch, ext4_support now allows grub to boot from ext4 partitions.
    This patch orginated from Quentin Godfroy <godfroy@clipper.ens.fr>

 -- Tim Gardner <[[IMG]https://edge.launchpad.net/@@/person[/IMG] tim.gardner@canonical.com]("https://edge.launchpad.net/%7Etimg-tpi")>   Tue, 06 Jan 2009 17:24:26 +0000  



If you are not getting it you should file a bug.

---

### Post by caryb on 2009-01-17
I built my pc with the 16th Jan daily build & the 1.x grub works perfectly with my ext4 install. I have 1 partition for / (ext4) 1 for swap so the boot is on ext4 with no problems.


Cary

---

### Post by ShirishAg75 on 2009-01-17
caryb, 
 did you use the alternate or the daily live to install?

---

### Post by caryb on 2009-01-17
Daily but I couldn't use the install partitioner to create the ext4 partition I had to use a console & activate the root account (sudo passwd root) & use fsck to create & format the / partition & when back in the installer use manual & point to the new partition & tell it not to format otherwise it crashes.


Cary

---

### Post by ShirishAg75 on 2009-01-17
> **caryb said:**
> Daily but I couldn't use the install partitioner to create the ext4 partition I had to use a console & activate the root account (sudo passwd root) & use fsck to create & format the / partition & when back in the installer use manual & point to the new partition & tell it not to format otherwise it crashes.


Cary

which means ubiquity still needs some work.

so what command did you use 

mkfs.ext4 what after that?

---

### Post by caryb on 2009-01-17
mke2fs -t ext4 /dev/sda3


You might want to check what your mount point is though & amend accordingly.


Cary

---

### Post by ShirishAg75 on 2009-01-17
> **caryb said:**
> mke2fs -t ext4 /dev/sda3


You might want to check what your mount point is though & amend accordingly.


Cary

caryb, 

I came to know these two commands :-

```

$ mke2fs -t ext4 /dev/sda1

```and 

```

$ mount -t ext4 /dev/sda1 /boot

```

and while this is fine, I guess you used gnu-fdisk to do partitioning.

---

### Post by Slug71 on 2009-01-17
> **Streeterer said:**
> I am having problems with GRUB after switching my filesystem to EXT4 and I believe the problem is with my current GRUB not having EXT4 support. Currently GRUB boots directly to the console, ignoring my menu.lst, and thus I cannot access Ubuntu. How would I go about installing GRUB 1.96? Or, better yet, what might I do to remedy my current GRUB?

Thanks!

Are you sure this is a grub error? Its sounds like it might be X?

---

### Post by Slug71 on 2009-01-17
If you want to try grub2 though then this is how i did it.
I might have the first code wrong because i installed from Synaptic.
```

sudo apt-get install-grub2
```

```
sudo update-grub2
```
```

sudo upgrade-from-grub-legacy
```

```
sudo update-grub
```

Are you dual booting?

---

### Post by Norm24 on 2009-01-17
> **Slug71 said:**
> If you want to try grub2 though then this is how i did it.
I might have the first code wrong because i installed from Synaptic.
```

sudo apt-get install-grub2
```

```
sudo update-grub2
```
```

sudo upgrade-from-grub-legacy
```

```
sudo update-grub
```

Are you dual booting?

I just did this and dual booting was not an issue as os-prober is now now part of the initial installation.

Btw I did this in Intrepid using Synaptic to install grub2.

You the dude slug.You helped me big time the last few days.You should change your nic to HUGE!

[http://ubuntuforums.org/search.php?searchid=54563416](http://ubuntuforums.org/search.php?searchid=54563416)

---

### Post by adult swim on 2009-01-17
what file do we edit?  is it /boot/grub/grub.cfg?

---

### Post by Slug71 on 2009-01-17
> **adult swim said:**
> what file do we edit?  is it /boot/grub/grub.cfg?

What do you want to edit? You shouldnt need to edit anything in there.

---

### Post by Slug71 on 2009-01-17
> **Norm24 said:**
> I just did this and dual booting was not an issue as os-prober is now now part of the initial installation.

Btw I did this in Intrepid using Synaptic to install grub2.

You the dude slug.You helped me big time the last few days.You should change your nic to HUGE!

[http://ubuntuforums.org/search.php?searchid=54563416](http://ubuntuforums.org/search.php?searchid=54563416)

Lol, thanks, glad it worked out.

---

### Post by adult swim on 2009-01-17
> **Slug71 said:**
> What do you want to edit? You shouldnt need to edit anything in there.

just looking under the hood :)

---

### Post by RAOF on 2009-01-18
The things to edit are:
```

/etc/default/grub - This contains the most useful user-changable options
/etc/grub.d/* - This contains the scripts which build /boot/grub/grub.cfg.  These are what you need to edit to do fancy stuff

```

---

### Post by Streeterer on 2009-01-18
It was an error with GRUB not being able to read the ext4 partition properly while it was installed on it. I fixed this problem by booting with the Alpha 3 Live CD, making a small partition ant the end of my drive, copying /boot/grub/ there, and then running sudo grub and writing GRUB to the MBR from that partition. GRUB2 was not necessary. Thanks for all the input!

---

### Post by Slug71 on 2009-01-18
> **Streeterer said:**
> It was an error with GRUB not being able to read the ext4 partition properly while it was installed on it. I fixed this problem by booting with the Alpha 3 Live CD, making a small partition ant the end of my drive, copying /boot/grub/ there, and then running sudo grub and writing GRUB to the MBR from that partition. GRUB2 was not necessary. Thanks for all the input!

Thats strange as Grub should have no problem booting Ext4. Did you file a bug?

---

