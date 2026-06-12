---
title: "Installing Ubuntu 10.10 on unallocated space"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by JackVDB on 2010-10-31
Hey, guys. I want to install Ubuntu 10.10 on a machine that has Windwos 7 with 2 partitions on it:

1. C: (100 gb) - main;
2. Z: (200 gb) - secondary.

My plans are to shrink (2) so that I have 40 gb of unallocated space, which I can install Ubuntu on.

My question is how do I do that: can I just click "Free Space" in the installer, or do I need to partition it myself, and if so how do I partition?


Thank you very much.




P.S. I have both the LiveCD and the alternate installer CD.

---

### Post by A_T on 2010-10-31
For some reason in Maverick the "free space" option has gone - you have to use the advanced partitioner.

---

### Post by P4man on 2010-10-31
Yeah the option to install in free space has gone for some weird reason, but then the solution is rather simple; dont create that free space, and let the ubuntu installer do it for you (it can shrink windows partitions and create the ones you need). This is a slooow process, and you probably want to defrag your drive in windows before doing this.

---

### Post by jroa on 2010-10-31
In Windows, you can use a program called EASEUS to change the size of the partition.  I am not sure what format Z: is, but you may have to reformat it too.  Then, run Ubuntu and install on that partition.

---

### Post by theozzlives on 2010-10-31
> **P4man said:**
> Yeah the option to install in free space has gone for some weird reason, but then the solution is rather simple; dont create that free space, and let the ubuntu installer do it for you (it can shrink windows partitions and create the ones you need). This is a slooow process, and you probably want to defrag your drive in windows before doing this.

NOOOOOOOOOOOOOOO! Use Windows Disk Manager (control panel > Administrative > computer manager > disk manager) and re-size your partition first!

---

### Post by P4man on 2010-10-31
> **jroa said:**
> In Windows, you can use a program called EASEUS to change the size of the partition.  I am not sure what format Z: is, but you may have to reformat it too.  Then, run Ubuntu and install on that partition.

Windows (vista and 7) has tools built in to resize partitions. That is making it harder though, since the only way to install ubuntu on to unpartitioned space, is doing it manually and a new user may not know or understand he needs a / and a swap partition (at least) or what filesystem they should be. Just let the ubuntu installer handle it.

---

### Post by P4man on 2010-10-31
> **theozzlives said:**
> NOOOOOOOOOOOOOOO! Use Windows Disk Manager (control panel > Administrative > computer manager > disk manager) and re-size your partition first!

Fine but then do explain how to create the extended, root and swap  partitions in the advanced setup, or a new user wont manage.

---

### Post by theozzlives on 2010-10-31
> **P4man said:**
> Fine but then do explain how to create the extended, root and swap  partitions in the advanced setup, or a new user wont manage.

1.Choose "advanced" then create a new partition, say 10 GB (10240 MB).
2.Mount it as root (/), ext4.
3.Do the same and call it swap (1.5-2 times your RAM).
4.Mount the rest as /home (ext4).

you'll be all set.

---

### Post by P4man on 2010-10-31
except if the OP has a windows recovery partition, which he will since he has windows 7. That,  plus 2 windows paritions plus 2 linux partitions makes 5 and 4 is the maximum number of primary partitions. Hence you need to create an extended partition first to hold the 2 linux partitions. 

Either that, or you could just drag a slider in ubuntu setup to determine how much space you want to allocate to ubuntu and be done with it. Choice is yours.

---

### Post by JackVDB on 2010-10-31
> **theozzlives said:**
> 1.Choose "advanced" then create a new partition, say 10 GB (10240 MB).
2.Mount it as root (/), ext4.
3.Do the same and call it swap (1.5-2 times your RAM).
4.Mount the rest as /home (ext4).

you'll be all set.
OK, so I've shrunk (2) and now I have 40 gb of unallocated space. Can I install now, and if so do I need to do as mentioned?


> **P4man said:**
> except if the OP has a windows recovery partition, which he will since he has windows 7.
I don't have a Windows Recovery Partition, I installed the OEM. I only have two partitions. Plus the 100 mb partition that Windows created by itself, it think for booting.

---

### Post by theozzlives on 2010-10-31
> **P4man said:**
> except if the OP has a windows recovery partition, which he will since he has windows 7. That,  plus 2 windows paritions plus 2 linux partitions makes 5 and 4 is the maximum number of primary partitions. Hence you need to create an extended partition first to hold the 2 linux partitions. 

Either that, or you could just drag a slider in ubuntu setup to determine how much space you want to allocate to ubuntu and be done with it. Choice is yours.

1. system
2. windows
3. /
4. extended
5. /home (logical)
6. swap (logical)

If there's a recovery partition Ubuntu will boot from a logical drive. You need a separate /home.

---

### Post by P4man on 2010-10-31
Jack if you want to do it manually, in the installation process when it asks you where to install, select manual (or advanced I think its called).

In the unpartioned space create a new extended partition that uses all the available space. Then inside that extended partition, create two logical partition as explained above (one "/" as ext4 and one swap as linux-swap). It should look like this:

[IMG]http://img5.imagebanana.com/img/toipwy8f/devsdaGParted_002.png[/IMG]

although with an extra windows partition that I dont have.

---

### Post by theozzlives on 2010-10-31
> **P4man said:**
> Jack if you want to do it manually, in the installation process when it asks you where to install, select manual (or advanced I think its called).

In the unpartioned space create a new extended partition that uses all the available space. Then inside that extended partition, create two logical partition as explained above (one "/" as ext4 and one swap as linux-swap). It should look like this:

although with an extra windows partition that I dont have.

Where's the /home, you NEED a /home incase you upgrade or have to re-install!

---

### Post by P4man on 2010-10-31
My home is where my stella is (sorry inside joke, belgian beer commercial).
I dont have a separate home on this machine, and you dont really NEED it, especially not, if like me, you put all your files that matter on the ntfs partition and backup externally. 

Not that its a bad idea, but for a first install, its not exactly crucial.

---

