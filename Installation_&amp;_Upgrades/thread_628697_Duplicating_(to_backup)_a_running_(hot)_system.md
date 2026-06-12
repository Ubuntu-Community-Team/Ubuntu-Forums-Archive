---
title: "Duplicating (to backup) a running (hot) system"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by lptr on 2007-12-01
This is a somewhat unusual place for posting this - I know because it only has rudimentarily to do something with Ubuntu.

Because it may be needed to some folks here, too - and of course because I know of the tolerant nature of this community I am asking it.

Is it possible to backup a running remote system so it will boot and act as the original one?

What I did until now so far:

I partitioned a new HDD as the old was (not the size but its nature like fs type where boot /var etc. was and so on).

I found there is sshfs. This can be used to mount a remote filesystem via ssh. I used it to transfer a complete fs over to a brand new drive (cp -a)

After this I moved data to its place. hda5/sda5 contained / with /boot and so on. Did all this and finally tried boot. Well did not boot. One Symlink was broken - this was a somewhat easier task to find. Another message regarding initrd unmounting stated out that it was only a trivial warning to be solved by creating dir /initrd. Next issue no console could be opened. Here /dev/console had flags c 0 0 instead of c 5 1. So: mknod /mnt/dev/console c 5 1 from a live-cd. 

But now it was getting difficult: INIT: cannot execute /etc/init.d/boot

We all know this is the central of all services being loaded during boot. Worse thing. Yes I know it would be much easier to start from scrap. Data are all there - but this is no option because it is no Ubuntu but a SuSE / SLOX installation which is VERY old (running since 2002 unpatched - no it is only a server located inside a LAN that's why not fully patched but has some patches). It has some patches that are not available anymore (well, the damned Novell thing - I dislike em - but this is another story). The worst thing of all is, that I am afraid to shut down hardware to simply one by one copy from a live-cd directly disk to disk. I have the feeling, that this od box will not boot anymore after shutting down (I saw this once many years ago - and that admin was really p***** - no not me - but it sticks in my head that this could happen).

Ok to my question:  
What can I do to automate finding out the differences between the still running old box and the new installation that does not completely boot right now. Is there a way to collect all in a some sort of locatedb, that contains all infos about files being on the one box and to diff it with the fs of the replica? 

I strongly believe that anybody has had the same trouble in the past and did find a way to solve this maybe wrote some scripts that collected infos. If this has been seen anywhere - pls let me know.

Thanks in advance

rob*

---

### Post by lptr on 2007-12-04
In very short words:

I did successfully transfer an old SuSE SLOX installation from a hot running box to a brand new harddrive that mounts the old machine over SSHFS to a temporary Ubuntu installation. The new machine SLOX clone boots from a completely different hardware. The only thing being same was the NIC (but w. different manufacturer ID). 

Prepare a new harddrive in the same kind as the old system was. I simply installed SLOX on this new harddrive so it had the chance to prepare all as it should be. Because new drive is such big I safed the default installation into a backup dir.

Be safe that one partition is big enough to hold all data from old box. Maybe you need to manually unmount/remount /NEW for each partition - same with /OLD. Think about strategy yourself.

Setup a minimalistic Ubuntu box (Transferbox). This of course one needs a direct LAN connection to old box (the faster the better) and after up and running mini Ubuntu...

On Transferbox:
$ sudo su
$ aptitude install sshfs
$ modprobe fuse
$ cd /
$ mkdir NEW
$ mkdir OLD

mounting new sda5 (hda5 under SLOX) contains / mountpoint 
$ mount -t reiserfs /dev/sda5 /NEW

mounting old SLOX box
$ sshfs username@IPaddress:/remote/folder/to/mount /home/user/local/mountpoint
Ex: sshfs _root_[EMAIL="bobbrown@bobserver.net"]@10.1.1.100[/EMAIL]:/ /OLD

Be carefull! Now under /OLD you are WORKING on the old box !!!!
Well and then you can simply cp -a for all dirs to copy data from old to new. But pay attention not to cp **/dev** and **/proc. YOU NEED TO TAKE INSTEAD THAT OF DEFAULT INSTALLATION.  **Mentioned it before, how I did it.

I used this - a little bit boring two lines to cd into every directory but the safe way:
for example
$ cd /OLD/etc
$ tar -cSp --numeric-owner -f - . | ( cd /NEW/etc && tar xSpvf - )

and so on.

It is very possible that you will have a broken link namely boot in /NEW/boot. Just delete this and make it new
$ cd /NEW/boot
$ ln -s . /boot

This is a very rough HowTo I know. Maybe it will safe another one some time - or at least telling another one that **IT CAN BE DONE**!

rob*

---

