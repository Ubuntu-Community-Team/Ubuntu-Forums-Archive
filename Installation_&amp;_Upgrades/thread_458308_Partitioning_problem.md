---
title: "Partitioning problem?"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by Asian_Wannabe on 2007-05-29
I'm completely new to Linux and am trying to dual-boot ubuntu and XP, but every time I get to the partitioning part of the install I choose "Resize and use free space" and hit Forward...but then it says that the operation failed..can anybody help?

---

### Post by gimmy_bond on 2007-05-29
are you using Gparted to do the partitioning?.

---

### Post by Asian_Wannabe on 2007-05-29
What's Gparted? I just put in the burned ubuntu cd and booted the computer.

---

### Post by eapache on 2007-05-29
What version of Ubuntu? (probably 7.04, but I'd like to be sure before continuing). Your system specs would also be useful.

---

### Post by Asian_Wannabe on 2007-05-29
7.04, umm...my computers ann HP Pavillion if thats what you mean.

---

### Post by eapache on 2007-05-30
I meant your processor speed and ram and stuff like that, but it doesn't really matter. Try again, but choose 'custom' instead. When that has loaded, take a screenshot (the 'printscreen' button on your keyboard) and post it here.

---

### Post by Asian_Wannabe on 2007-05-30
I can't manage to connect to the internet on ubuntu :( but i wrote down what the thing said :)

Prepare Partitions

Device       | Type | Mount Point | Format? |   Size           |     Used

/dev/sda1    ntfs    /media/sda1  (square)    241156MB     230000MB
/dev/sda2   fat32   /media/sda2  (square)    8899MB         8300MB

also those squares were not checked

---

### Post by eapache on 2007-05-31
You don't have enough space left on your hard drive to install Ubuntu. Go into XP and run the disk-cleanup utility, then the defragmentation utility. Then try again.

---

### Post by Asian_Wannabe on 2007-06-02
i defragmented and used the disk cleanup but I still get the error when I try to install :( is there no hope for me?

---

### Post by eapache on 2007-06-02
What is under the 'used' column for the ntfs partition in custom mode now? It should be somewhat less since you have run the disk cleanup utility...

---

### Post by floke on 2007-06-02
A common error is for the partitioning to fail since the partitioner mounts the drive during the process (dumb, really dumb). This sounds scary but its simple, honestly. 

(1) Go into Gparted (system/admin/gparted). 
(2) Resize your NTFS (XP) partition. 
(3) Create a new partition out of most of the remaining space (leaving aside around 1 1/2x your RAM size for the swap file) - i.e. if you have 1Gig of ram, leave around 1.5-2 gigs partitioned. Format the partition as a primary partition and in the ext3 format. 
(4) For the remaining space, format it as an extended partition. Then inside this create a logical partition and format it as ext3 (it might even let you designate it as swap).
(5) Your partitions are ready. Proceed to the install and choose custom/manual partitioning.
(6) When asked where to install ubuntu, point it to the relevant partitions (right click the large ext3 partition and select '/' as a mount point to designate it as root), and the installer 'should' do the rest.

If not, your remaining option is the alternative installer.

Hope this helps.

---

### Post by pcit on 2007-06-10
Hello,

I followed almost the same procedures, except I forgot to unmount the ntfs drive first (I am dumb:oops:)
Hence, I got an error message that the drive resized failed and everything was unpredictable until you reboot...
So, I rebooted into XP, now my fresh installed xp only show 20GB...The whole drive before I format in gparted was 40 GB, but it only remain 20GB now. I decide to go to the manage page in xp, the system information showed that the 40GB drive is "healthy" but my capacity only remain 20GB :-s
Any idea how to fix this problem? I have invisible 20 GB now T_T

P.S. I have the Diskkeeper and when I ran the analysis the drive, I saw there was a huge system reserved area, did that help to analyze the problem at all?

Thanks for spending the time read my post...

---

### Post by merlinus on 2007-06-10
This is by far the best way to partition drives:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Since it is a live cd, you do not have to worry about mounting and/or unmounting partitions in order to size and format them.

Good luck!

-merlin

---

### Post by pcit on 2007-06-10
Thanks for the link, I will try it now and post back the result!

---

### Post by pcit on 2007-06-10
> **merlinus said:**
> This is by far the best way to partition drives:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Since it is a live cd, you do not have to worry about mounting and/or unmounting partitions in order to size and format them.

Good luck!

-merlin
One quick question, will this Live CD also recovery the drive space that was missing due to the fail format?

---

### Post by pcit on 2007-07-07
Hello everybody,

I am sorry that I come back so late (three weeks after...)

But the instuctions in this post DOES solve my probelms. I have dual boots (XP, Xubuntu) in my PC.

Thanks!!

---

