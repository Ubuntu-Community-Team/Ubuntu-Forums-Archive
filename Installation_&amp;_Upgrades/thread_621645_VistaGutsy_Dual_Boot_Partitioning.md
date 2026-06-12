---
title: "Vista/Gutsy Dual Boot Partitioning?"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by KTK on 2007-11-23
Noob here: I'm not sure what's the best approach to partitioning for a Vista/Gutsy dual-boot system.

I have a brand new Dell Athlon 64 X2 5000+ system with a 250GB SATA hard drive, and 128MB NVIDIA 8300GS video driver. Vista came installed; the hard drive is otherwise clean. I'd like to keep Vista because I have to deal with a lot of people using Windows and MS Office, but have Ubuntu as my main OS. I've burned the Ubunto 7.10 Desktop install CD, but haven't run it yet. This is my first Linux install and I'm a bit hesitant.

After reading a lot of threads here and at [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning), I'm thinking along these lines: set up individual partitions for Windows and Linux, a small swap partition, and a large /home partition for all my data. I would like /home to be dual-readable by Windows and Linux applications, so I don't get data files trapped in just one OS or the other. I know that it can be done by setting up /home as a FAT32 partition, and also that there are utilities I can use to make /home Ext3 and mountable by Windows. But I'm sort of stuck at that point. All input welcome.

What partition sizes should I use for Vista and Gutsy? (10GB is a common suggestion, but that seems small, especially if I have to load a bunch of bloatware into the Vista partition. I've got that huge disk - why not create big partitions for both OSes?)

Should I create the Vista partition using the built-in partitioning utility in Vista, or by running the Ubuntu 7.10 Desktop CD?

Are the Windows/Ext3 file-reader utilities at:

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs) and
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

really stable and reliable? Is there any danger in using them? Is one better than the other?

Would I be better off just going with FAT32 - given that my priorities are data security and system stability? (I.e., the translator utilities may be great but I don't want to mess with them if there's any danger of corrupting the files, or even just needing a lot of maintenance. I want something I can install and forget.)

Aside from the partition issue, I see some suggestions in the forum that the 64-bit distro is not well supported with drivers and codecs. Is that right? I thought I was doing well in getting a cutting-edge system at a good price - am I hosed instead?

Thanks very much for any feedback.

---

### Post by Onay on 2007-11-23
All I have to say is that I ***Highly*** recommend that you partition in vista and DO NOT install GRUB, it will ruin your vista installation and make it virtually impossible to access.

---

### Post by meierfra on 2007-11-23
> All I have to say is that I Highly recommend that you partition in vista

I agree.

> DO NOT install GRUB, 

I disagree. Since Grub does not touch the Vista partition, it definitely  will not ruin Vista.

---

### Post by torgrot on 2007-11-23
I would second that.  Search the forums for EasyBCD and read the tutorials.  As I understand it, EasyBCD will allow you to use the Vista BootLoader to load Ubuntu.  I would also strongly suggest that you make a system backup of your drive prior to starting.

torgrot

---

### Post by cancertoast on 2007-11-27
> **Onay said:**
> All I have to say is that I ***Highly*** recommend that you partition in vista and DO NOT install GRUB, it will ruin your vista installation and make it virtually impossible to access.

So how do I go about installing Ubuntu without GRUB, if I already have Vista installed as my primary OS?  And along similar lines, would I benefit from using Easy BCD?  Would that fix/prevent my dvd-rom drive issues (i.e. my drive disappears in Vista and Linux after I install Linux for a dualboot)?

I would love to learn more about Linux and use it more often, however, without a working dvd-rom that is simply ridiculous to even imagine doing considering how many games I play and cds I rip.

Maybe someone can actually help me this time.

---

### Post by rsambuca on 2007-11-27
> **KTK said:**
> After reading a lot of threads here and at [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning), I'm thinking along these lines: set up individual partitions for Windows and Linux, a small swap partition, and a large /home partition for all my data. I would like /home to be dual-readable by Windows and Linux applications, so I don't get data files trapped in just one OS or the other. I know that it can be done by setting up /home as a FAT32 partition, and also that there are utilities I can use to make /home Ext3 and mountable by Windows. But I'm sort of stuck at that point. All input welcome.
Do not use FAT32.  It is basically an antiquated filesystem that is prone to problems and requires excessive maintenance.  I suggest that you make a shared data/media partition for both OS's to use.  If you think you will be using Windows more, then format it as ntfs.  If you think you will be using linux more, than format it is ext3 and use the fs-drivers for Windows.  Both ways work well, but they are a tiny bit slower using the other type of filesystem.  If you ever need to re-install ubuntu for some silly reason, you can always just copy the /home files you require.
> **KTK said:**
> What partition sizes should I use for Vista and Gutsy? (10GB is a common suggestion, but that seems small, especially if I have to load a bunch of bloatware into the Vista partition. I've got that huge disk - why not create big partitions for both OSes?)

Should I create the Vista partition using the built-in partitioning utility in Vista, or by running the Ubuntu 7.10 Desktop CD?10GB is way too small for Vista.  I suggest at least thirty.  And definitely use the Vista Disk Manager to shrink the partition.  Defrag, defrag, and then defrag again.  Then shrink.

> **KTK said:**
> Aside from the partition issue, I see some suggestions in the forum that the 64-bit distro is not well supported with drivers and codecs. Is that right? I thought I was doing well in getting a cutting-edge system at a good price - am I hosed instead?

Thanks very much for any feedback.That is just pure outdated and incorrect FUD.  The 64-bit distro is very well supported for both drivers and codecs.  Of the 20,000+ packages available in the repositories, there is less than 1% difference between the 32 and 64 bit versions.  Unless you are going really obscure with your packages, you should be safe.

---

### Post by meierfra on 2007-11-27
cancertoast:  I'll answer you in your other thread

[http://ubuntuforums.org/showthread.php?t=528216]("http://ubuntuforums.org/showthread.php?t=528216")
just give me a minute.

---

### Post by Computer Guru on 2007-11-28
Picture walkthrough for dual-booting Vista and Ubuntu: [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

