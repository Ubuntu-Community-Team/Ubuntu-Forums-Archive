---
title: "[SOLVED] XP &amp;amp; Ubuntu dual-boot: reinstall Ubuntu"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by zoopzoop on 2008-03-09
Hi!

I installed Ubuntu 6.4 parallel to XP about 8 months ago but couldn't find time to dig into it yet.
Now I have this time and thought I might as well install 6.10 before I start using / learning Ubuntu.
This is my current partition configuration:

c (NTFS) - Windows XP
d (EXT3) - Linux home and lots of data (Pictures, music etc.)
e (FAT32) - More data
f (EXT3) - Linux

c, d and f are partitions on a single hard drive, e is a separate hard drive.
I followed the reasoning in [this guide]("http://www.psychocats.net/ubuntu/partitioning") when I created d as my linux home partition. I am using [FSDrive]("http://www.fs-driver.org/") to read and write from Win XP to d.

Now the problem is I cannot backup my data on d anywhere because it is too much. c, e and f don't have enough space.

Is it possible / safe to reinstall Ubuntu using d as my home partition without formatting that partition?
Thanks!

---

### Post by Gouz on 2008-03-09
Greetings

As far as I know, no.
If you reinstall ubuntu all your data will be lost, because in the installation you will be asked to set " / "
Which is your directory.
Now, you can make a new account on your linux, and then copy your /home directory.

you can do it from terminal or command line. 

Gouz

---

### Post by Pumalite on 2008-03-09
If you have a separate /home directory in d, you can do it. Just reinstall root to where it was, then pick /home as /home (don't format it). For all this you have to go Manual.

---

### Post by Gouz on 2008-03-09
ok here it is the code

```


:~$ sudo adduser
[sudo] password for rosi:
adduser: Only one or two names allowed.
rosi@Heaven:~$ sudo adduser test
Adding user `test' ...
Adding new group `test' (1001) ...
Adding new user `test' (1001) with group `test' ...
Creating home directory `/home/test' ...
Copying files from `/etc/skel' ...
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for test
Enter the new value, or press ENTER for the default
        Full Name []: 
        Room Number []: 
        Work Phone []: 
        Home Phone []: 
        Other []: 
Is the information correct? [y/N] y
:~$ sudo adduser test admin
Adding user `test' to group `admin' ...
Done.



```

that is how you can make a new user
from the terminal

OR

System>administration>Users and groups>
enter pass
add user (when you are done go to) manage groups add the new user to the admin group and you are done :P
Then all the only thing you have to do is to copy all your data.

If you don't know how to do it tell me :P

Gouz

---

### Post by Gouz on 2008-03-09
Pumalite

you can do that with live CD?
(I should I have expiriment more with the live cd :/ )

---

### Post by zoopzoop on 2008-03-10
Gouz & Pumalite, thanks for your answers.

Gouz,
I don't really understand how creating a new user could help me in my situation.
Won't that just create a new user directory on d?

Pumalite,
Unfortunately my linux home partition is d, not d:\home.
I started the Ubuntu install and, quite honestly, I'm too scared to rely on it keeping all my data intact.

Now, I thought of splitting d into two partitions, and copying my data to that new partition (which would probably become g), so that d really just contains my linux home.
Then I could reinstall Ubuntu (formatting f and d) and merge d and g afterwards again.

However, I tried that (using GParted) but my disk already contains four primary partitions (c, d, f and a swap partition [e is a separate drive])... now I'm out of ideas. Does my linux home partition need to be a primary partition? And if not, is there a way to make it a logical partition without losing my data?

---

### Post by Pumalite on 2008-03-10
One of those primary part5itions will have to go. From the third, you make an extended partition and within that one, as many logicals as you want. Ubuntu works in both, but the beauty is that it works in logical.
Google>Psychocats>Partitioning

---

### Post by zoopzoop on 2008-03-11
I solved the problem by extending the size of my Win XP partition c, moving over my data from d and then installing Ubuntu on f and d, formatting both partitions.
Thanks for the help, Pumalite & Gouz!

---

### Post by Pumalite on 2008-03-11
You are welcome. Good luck.

---

