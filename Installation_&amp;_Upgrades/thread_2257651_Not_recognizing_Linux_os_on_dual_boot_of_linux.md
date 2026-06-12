---
title: "Not recognizing Linux os on dual boot of linux"
date: 2014-12-21
forum: Installation &amp; Upgrades
---

### Post by Barsoom88 on 2014-12-21
Hello everyone,
I have trying to dual boot (any) two linux distros and each one does not recognize the other. The HD is 640gb. I have tried all the variants but the odd thing is the new versions will see the old unsupported ones but not any of the newer ones. Any suggestions or links?
Thanks,
B

---

### Post by sudodus on 2014-12-21
Please describe your installation! Which linux distros and versions? How were they installed?

And please show the partitions and file systems: Post the output of the following commands and put it within code tags.

```
sudo parted -l
```

```
df
```

---

### Post by Barsoom88 on 2014-12-21
Sudodus,
Thanks for the quick reply! There is nothing wrong with my current install only when I try to dual boot another linux os. Currently I am running lubuntu 14.04 but when I try to dual boot ubuntu 14.04 it gives me a "no operating system" and will only allow a full install of ubuntu. I have scoured the internet and have found no answers. I have tried to dual boot many other distros (even switching them) with the same results. I prefer to have two 
linux instead of windows & linux dual boot. 
B

---

### Post by Bashing-om on 2014-12-21
Barsoom88; Hello;

We want to know that you have not used up the 4 primary partitions on the hard disk. With the 'legacy' partition scheme there is a 4 primary partition limit. We need to look and see what is !

As requested by sudodus; provide - between code tags :
```

sudo parted -l
df

```

[INDENT][INDENT]a means to move forward
[/INDENT][/INDENT]

---

### Post by Barsoom88 on 2014-12-21
Here it is!


```

Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   640GB  640GB  extended
 5      257MB   640GB  640GB  logical


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/lubuntu--vg-root: 636GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  636GB  636GB  ext4


Error: /dev/mapper/lubuntu--vg-swap_1: unrecognised disk label            

Error: /dev/mapper/sda5_crypt: unrecognised disk label


```

---

### Post by Bashing-om on 2014-12-21
Barsoom88; Ummphh ....

Out of my league :
> 

Error: /dev/mapper/lubuntu--vg-swap_1: unrecognised disk label 

Error: /dev/mapper/sda5_crypt: unrecognised disk label


As Logical Volume Management (LVM) AND encryption ->
is not a part of my experience pack.
Others here will advise .

[INDENT][INDENT]some times
[INDENT][INDENT][INDENT][INDENT]I just do not want to know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Barsoom88 on 2014-12-21
Thanks, Bash! The problem is that I have 3 laptops and I can't dual boot (2) linux on any of them. I was hoping it was an easy fix.
B

---

### Post by yancek on 2014-12-21
Your parted output in post 5 shows a small boot partition and the rest of the drive taken by an LVM partition.  There is nowhere to install anything.  You could install VirtualBox and run another OS from that or you could shrink the LVM partition to create space to install another OS.  I've never used LVM so don't know how to do it but it can be done.  I don't understand how you would get a "no operating system found" message if you can't install.  More details might help.  I usually have 10 or more different Linux systems installed just to test so it's not that difficult.

---

### Post by Barsoom88 on 2014-12-21
Yancek,
Thanks for the response. The installer gives me no other option "No operating system found" instead of install "along side of" as the older linux distros have done for me with windows. Perhaps, you could give me a link on how to do partitioning for multiple boots? I've looked but don't get any details on how to do it. 
B

---

### Post by sudodus on 2014-12-21
The problem is that you have an encrypted LVM partition, that fills most of the drive. I think most of us know how to help with normal partitions, but quite few know about encrypted LVM partitions and how to manage them. If you want to create dual boot, I suggest that you do not make an encrypted disk. Encrypted home is easier to manage (or no encryption at all).

---

### Post by yancek on 2014-12-21
The link below is an excellent tutorial on a standard installation for Ubuntu which has a lot of detail as well as links to partitioning.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

The link below has some good information on LVM, scroll about half way down the page to 'Resizing a Logical Volume'.

[http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/](http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/)

---

### Post by Barsoom88 on 2014-12-22
Yancek,
After some tinkering it is indeed the LVM! By not booting in LVM I was able to dual boot! However, is the security of my system less than it should?
But that question is for another thread.
Thanks for all your help!
B

---

