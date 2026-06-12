---
title: "Trying 13.10 on Asus 1005pe"
date: 2013-11-08
forum: Installation &amp; Upgrades
---

### Post by pirracas77 on 2013-11-08
Hi:


I'm trying to install 13.10 on a Asus 1005pe via USB stick.


I would like to have W7 and Ubuntu, and choose the boot as as per my decission.


For this reason I'm choosing the option "Install Ubuntu inside Windows7" in the installation menu.When I press "continue", the laptop boots and strangly starts **again **the welcome screen where you chose "Try Ubuntu" or "Install Ubuntu"


What am I doing wrong?

Thanks in advance

---

### Post by Bucky Ball on 2013-11-08
Do you mean install Ubuntu alongside Windows? Inside Windows is not a dual-boot, it is a Wubi install. Stay away from that as it has been phased out.

---

### Post by pirracas77 on 2013-11-08
> **Bucky Ball said:**
> Do you mean install Ubuntu alongside Windows? Inside Windows is not a dual-boot, it is a Wubi install. Stay away from that as it has been phased out.

Yes, I mean alongside Windows. I would like dual-boot. What is the option that I need to chose?

[IMG]http://img822.imageshack.us/img822/6485/9n1t.jpg[/IMG]

---

### Post by Bucky Ball on 2013-11-08
Hmm, alongside may have been left out of 13.10. Not sure, don't use it. DO NOT install inside Windows. Not what you want (Wubi install as mentioned and shouldn't be there anymore).

Choose 'Something Else' and install manually. You can create it there, but do you have the free space ready to install Ubuntu to? Have you backed up your personal data? Do you have a plan?

You will see the Windows partition when you get to the partitioning window (it is Gparted partitioner) so just don't touch it. It will be an NTFS partition. For Ubuntu you need / and a /swap partition (the /swap only need to be 2Gb).

Strange how the 'install alongside' option is not listed, though. You are using the desktop install disk and not a Wubi disk by mistake? Just to make sure ...

---

### Post by pirracas77 on 2013-11-08
> **Bucky Ball said:**
> Hmm, alongside may have been left out of 13.10. Not sure, don't use it. DO NOT install inside Windows. Not what you want (Wubi install as mentioned and shouldn't be there anymore).

Choose 'Something Else' and install manually. You can create it there, but do you have the free space ready to install Ubuntu to? Have you backed up your personal data? Do you have a plan?

You will see the Windows partition when you get to the partitioning window (it is Gparted partitioner) so just don't touch it. It will be an NTFS partition. For Ubuntu you need / and a /swap partition (the /swap only need to be 2Gb).

Strange how the 'install alongside' option is not listed, though. You are using the desktop install disk and not a Wubi disk by mistake? Just to make sure ...

You are right, this option have been left out of 13.10.
I'm downloading 12.04.3 LTS right now.

Thanks for your support!!

---

### Post by heir4c on 2013-11-08
If you just have the message to install IN Windows of to remove Windows, than there are already 4 partitions on your drive.
Start de live-dvd/usb and open gParted (PartitionManager)
Take a screenshot of that and post it here.
Than we can see what's on the partitions.

---

### Post by pirracas77 on 2013-11-08
> **heir4c said:**
> If you just have the message to install IN Windows of to remove Windows, than there are already 4 partitions on your drive.
Start de live-dvd/usb and open gParted (PartitionManager)
Take a screenshot of that and post it here.
Than we can see what's on the partitions.


Yes, you are right. I have 4 partitions. They came by default with the laptop.

[IMG]http://img35.imageshack.us/img35/7800/a8q9.jpg[/IMG]

The unknown one is a fasboot of Asus.

---

### Post by mikewhatever on 2013-11-08
So, 'Inside Windows' - aka Wubi is your only option, unless you are ready to get rid of a partition. Wubi is not the best choice, and may not work reliably well, but, it shouldn't hurt trying.

---

### Post by heir4c on 2013-11-08
I don't use Windows, so you must know where Windows is on your drive.
sda4 is a unknown partition of 17MB. Is there something on there? Look with nautilus (Filemanager) of there is something on. If not, you can delete that partition. (maybe it is used by BIOS "Boot Booster". I read that somewhere, but don't know what that is, so look for it in your manual or via internet) 
Edit: I find something about Boot Booster: [http://blog.pew.cc/blog/eee+PCs+Boot+Booster/](http://blog.pew.cc/blog/eee+PCs+Boot+Booster/) and: [https://www.youtube.com/watch?v=dR5eJP43vTk](https://www.youtube.com/watch?v=dR5eJP43vTk)

You can also delete the Recovery Partition, BUT: !!!! you must first backup that data on a extern drive (or cd/dvd) And if you don't have a RecoveryDVD, than make one first before you change the partitions/install Ubuntu.!!!!
And make a backup of al your stuff on the windows partition that is not from the system (docs, photo's, image, and other data)!!!

If you delete one of them than you have only 3 partitions left.

Than you you choose the partition with Windows on (I think it is the sda2 but the sda1 is very big and that is strange because the 'loader' is on that one. So take your time to find out what's on each partition). 
You can then reduce that partition with some GB (min. 25GB) for Ubuntu. 
if you have reduced the partition where Windowssystem is on, than you have a space that is empty. Change that first to a Extended partition and make in that Extended partition 2 Logical partitions, 1 for / (25GB or more) and 1 for a swap (RAM size + 500MB or so. It's not needed so much if you have enough RAM because he had enough space then).
Normally in the new version of the installer you can't choose for a Extended partition but directly for a Logical partition, so he make the Extended partition itself.

---

### Post by Bucky Ball on 2013-11-08
Don't go for Wubi, as I already mentioned. It is being phased out and, even though it is presented as an option, really shouldn't be there. 

Yes, you need to make some space by removing a partition and leaving free space for Ubuntu (or putting the existing partitions in an extended partition so all up you have less than four) and I would recommend 12.04 LTS as a great starting point for a beginner in any case.

---

### Post by fantab on 2013-11-09
When the Ubuntu installer does NOT see either 'Unallocated Space' or a Linux partition it may NOT offer to 'Install Alongside Windows'.

Can you post the screen-shot of you Hard Disk from Windows? It may help us determine which parttion will be safe to delete. 

This Thread might be useful: [http://ubuntuforums.org/showthread.php?t=2186301](http://ubuntuforums.org/showthread.php?t=2186301), especially see post #8 and #9.

---

### Post by pirracas77 on 2013-11-09
Thanks all for your awesome support!!


I finally solved my problem.


I downloaded the adequate 32 bit-ISO in the same wubi path (because wubi tried to download a 64bit version and it is not my case). That means ubuntu-12.04.3-desktop-i386.


Then in the prompt I ran exactly "wubi.exe --32bit". The installation was completed successfully!!


Now I have dual-boot and I can choose the OS that I need  every time.

---

### Post by fantab on 2013-11-09
WUBI isn't exactly a dual-boot... It installed as a 'program' in within windows. It meant for Windows users to 'try' Ubuntu for sometime before they do a real dual boot.
In real-dual boot Ubuntu will be installed to its own partition and works independently of Windows.

Anyways...Good Luck.

---

### Post by Bucky Ball on 2013-11-09
Wubi is not a dual-boot and you have gone ahead and done exactly what was advised against. Wubi is being phased out, you will find little support if things go wrong, and it is/was intended to try Ubuntu before you do an install to hard drive (meaning a partition other than Windows). A dual-boot is Windows on one partition, Ubuntu on another.

Please mark thread as solved by following the instructions in my signature. Thanks.

---

### Post by pirracas77 on 2013-11-09
> **Bucky Ball said:**
> Wubi is not a dual-boot and you have gone ahead and done exactly what was advised against. Wubi is being phased out, you will find little support if things go wrong, and it is/was intended to try Ubuntu before you do an install to hard drive (meaning a partition other than Windows). A dual-boot is Windows on one partition, Ubuntu on another.

Please mark thread as solved by following the instructions in my signature. Thanks.

Oh, ok I now understand what it means. Anyway I think this installation way is enough for me at the moment. I'm not feel sufficient brave to play with the partitions that my laptop has. To be honest, I wouldn't know where to start.
I needed Ubuntu to feel my laptop smooth again and I got it!!!

Thanks again, you are a great community!!

---

