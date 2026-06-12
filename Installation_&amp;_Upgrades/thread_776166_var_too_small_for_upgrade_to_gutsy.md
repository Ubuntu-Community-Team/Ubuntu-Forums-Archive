---
title: "/var too small for upgrade to gutsy"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by Námo Mandos on 2008-04-30
Hi.  I tried to upgrade from feisty to gutsy.  But tragically, my /var is in its own partition, and that partition is too small!  Anyway to redirect the upgrade to use another partition?

---

### Post by forestpixie on 2008-04-30
Try doing an apt-clean to empty the archive - that will get some space in the /var

sudo apt-get clean

---

### Post by Námo Mandos on 2008-04-30
It wants 1.2GB.  After doing the clean thing, I only have 400MB.  It's a small /var.  Didn't expect this problem when I partitioned it.

---

### Post by forestpixie on 2008-04-30
Can you not resize it?

---

### Post by Námo Mandos on 2008-04-30
gparted is not happy with that.

---

### Post by forestpixie on 2008-04-30
What is it unhappy about then - I assume you're trying with a livecd.

---

### Post by Námo Mandos on 2008-04-30
Nope.  But is there anyway to do this without changing partition sizes?  Like via symbolic links or something?  The drive is partitioned the way it is for a reason and I was hoping not to fiddle with the partitions that *do* have space.

---

### Post by forestpixie on 2008-04-30
I don't know I'm afraid you'll have to wait for someone else - never looked at symbolic links. Sorry :(

---

### Post by Námo Mandos on 2008-04-30
bûmp

---

### Post by lemming465 on 2008-04-30
Yes, you can use symbolic links to rearrange things.  Assuming you have enough space somewhere else, try this:
> sudo -i
cd /var/cache
cp -a apt /some/where/else
mv apt apt.old
ln -s /some/where/else/apt .
When you are happy with the new apt symlink, you can do *sudo rm -rf /var/cache/apt.old*

---

### Post by malapradej on 2011-05-02
Hi, I also have the same problem upgrading from maverick to natty. I  also partitioned my system like a server a year ago in ignorance  when I just started  using Linux Ubuntu. 
It seems like it is the whole /var folder that needs to be symlinked, as  the /var/cache only has 45MB of files and folders. My /var folder has  its own partition of 1.9GB, which is exactly what natty narwhal needs to  upgrade.
Is it possible (i.e. will I have a working system) if I symlink the whole /var folders content?

example:

sudo -i
cd /var
cp -a apt /some/where/else
mv apt apt.old
ln -s /some/where/else/apt . 			 		

and to fix it after upgrade:

[I]sudo rm -rf /var/apt.old

[/I] Many thanks for the advice in advance.
Jacques

---

### Post by malapradej on 2011-05-02
> **malapradej said:**
> Hi, I also have the same problem upgrading from maverick to natty. I  also partitioned my system like a server a year ago in ignorance  when I just started  using Linux Ubuntu. 
It seems like it is the whole /var folder that needs to be symlinked, as  the /var/cache only has 45MB of files and folders. My /var folder has  its own partition of 1.9GB, which is exactly what natty narwhal needs to  upgrade.
Is it possible (i.e. will I have a working system) if I symlink the whole /var folders content?

example:

sudo -i
cd /var
cp -a apt /some/where/else
mv apt apt.old
ln -s /some/where/else/apt .                      

and to fix it after upgrade:

[I]sudo rm -rf /var/apt.old

[/I] Many thanks for the advice in advance.
Jacques

Or is there another way to upgrade without starting from scratch as in reinstall the whole system?.

---

### Post by dino99 on 2011-05-02
do you really need that custom install ?
here is the standard one:
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

