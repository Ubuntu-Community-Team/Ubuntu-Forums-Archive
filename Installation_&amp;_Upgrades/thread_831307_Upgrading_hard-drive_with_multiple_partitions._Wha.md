---
title: "Upgrading hard-drive with multiple partitions. What is the easiest medhod?"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by alperyilmaz on 2008-06-16
I'm using Ubuntu Hardy currently and I'm upgrading my harddrive from 60GB to 160GB. In the old drive there are multiple partitions and /home and / (root) are mounted to separate partitions. 
In the new harddrive I'd like to keep the similar setup (separate partitions for / and /home), only difference will be that they will have bigger sizes. 
I know of the neat dd command which can clone a disk or partition in with single command "dd if=/source/partition of=/target/partition", however as far as I read, this is only true for same size disks/partitions. Is there a way to use dd for an upgrade process? If not, what is the solution for this specific project?

---

### Post by louieb on 2008-06-16
Might be a fairly easy thing. Just use GParted from a live cd such as [SystemRescueCd]("http://www.sysresccd.org/Main_Page"). Create your new partitions and use the copy function to get your stuff from one partition to the other.  

May have some UUID's to change in your Ubuntu install. Once you take care of that, it should work.

---

### Post by Pumalite on 2008-06-16
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by jkwinn on 2010-03-10
I am trying this tomorrow:

[http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk](http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk) 

Hopefully it goes as planned and I can report back tomorrow night.

---

