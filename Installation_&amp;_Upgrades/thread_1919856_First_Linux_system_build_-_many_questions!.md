---
title: "First Linux system build - many questions!"
date: 2012-02-03
forum: Installation &amp; Upgrades
---

### Post by QuadraQ on 2012-02-03
Hello all,

I just ordered the parts to build my first PC with a full native install of Linux on it. I've played with Ubuntu in the past and was very impressed, but this is the first time I've been able to build a separate machine that will use Ubuntu as it's primary OS.

The basic specs of the machine are:

Intel Core 2 Quad Q6600 @ 2.4 GHz
3 GB of DDR2 memory
1 TB SATA 3.0 hard drive
AMD Radeon 6870 1GB video card

The plan is to dual boot it with Win7 64-bit and Ubuntu 64-bit. The only reason I want to install Win7 is for the occasional gaming session with friends (such as StarCraft II, some MMO's, etc.) Other than that it will be dedicated to Ubuntu.

That said, I'm not sure how to best go about doing this. 
How should I partition the hard drive? 
How much space should I dedicate to each OS?
Which OS should I install first?
What version of Ubuntu is recommended?

Any suggestions would be most appreciated!

---

### Post by oldfred on 2012-02-05
I prefer to keep operating systems on separate drives, but you can install both systems on one drive as long as you do not run Windows software that uses DRM that interferes with grub2's boot code, just after the MBR.

It is slightly easier to install Windows first as it will overwrite the MBR with its boot code and you have to reinstall grub2's boot loader. But after reinstalling boot loaders to MBRs several times you may find it not really difficult but you do need a Windows repairCD/USB and Ubuntu liveCD/USB. 

I do not know how much space your games may take. Generally I prefer to keep system partitions smaller and keep data in separate shared NTFS partitions or Linux /home and/or data partitions.

With a 1TB drive you have lots of room. I might be a bit more generous in system partitions, but you do not want them too large or system is not quite as quick. But NTFS partitions do need 30% free space to keep working well.

You also could leave some unallocated space in the extended partition in case you want to experiment with other systems. I left about 200GB on my drive and keep adding 25GB root partitions to install some system I want to test.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

