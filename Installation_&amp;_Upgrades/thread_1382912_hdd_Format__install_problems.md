---
title: "hdd Format / install problems"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by dcory on 2010-01-16
I'm having trouble installing a 64-bit version of 9.10 on a new WD 1tb hdd.  

Symptoms: When I attempt to format the drive using the 9.10 liveCD, the system freezes right as the format begins (the install process is at 5%).

I have another drive with a more or less working version of 9.10 installed - this installation needs to be replaced, but it is still functional enough for me to attempt the following: I booted to this installation and attempted to use gparted to format my new drive.  This freezes the machine in exactly the same way as it did with the liveCD.

[NB: I've tried to format to both ext4 and ext3]

Some people with similar problems have been having trouble with their burns of the liveCD, so I tried to make other copies with slower burns and do md5sums.  This has been no help.  I have also tried other (older) versions of the live CD, including 8.04.3 LTS.


Now here is the strange part: I am able to format the hard drive to ext3 using an older 32-bit liveCD (8.10).  I can then install that os (8.10 32bit).  I cannot, however, install a 64bit version of 9.10- it crashes during the 'selecting and installing software' stage of the installation.


I can, strangely, install an older version of the 64 bit system (8.04.3 LTS).  I tried using that install to upgrade using the repositories, but this fails as well.

I have reason to think that the memory in my computer is not the issue, because I can successfully boot to my other hard drive with a 64bit install.  I also don't think that the hard drive is the problem [although I'm running a long test to confirm this], because it can hold an install.  

I'll be happy to add any other information people would like.  I have found some similar posts on this issue but either they have been closed or marked as solved and the solutions given in them have not helped me.

Thank you in advance to anyone willing to help me; I know that nobody is obliged to help, but it is the willingness of knowledgeable people to help that lets users like me keep going with ubuntu.  

Regards,
dcory

---

### Post by sytoby on 2010-01-17
I am having a similar problem.  I start the install with the live CD - I have 2, one came with the Ubuntu User magazine and the other I downloaded.  After selecting the desktop language (English USA), location (Eastern USA) and keyboard layout (USA) the partitioner is started but after the green thermometer is completed nothing happens.  If I click Forward, I get an error.  I have waited several hours for the partitioner to display something but to no avail.  I have installed 9.04 successfully but want to upgrade to 9.10.  The machine I use is just a test machine with an AMD processor, 2GB memory, 320 GB SATA hard drive.

---

### Post by dcory on 2010-01-17
It turned out that my problem was hardware related.  Specifically, I had bad memory.  This surprised me because the memory had worked well before.

Threads about this issue all seem to say that it is either a) bad memory, b) a bad cd, or c) a bad CD-drive.  C seems very unlikely, and is not frequently mentioned.

I won't mark this thread as solved so you can try to get help with your issue.

---

### Post by shatul_in on 2010-01-18
I've has a same problem a few months ago...
I tried booting my system with a USB Thumb drive then doing the Net Install(provided, if you've a 24*7 Web Connection)...It works if the CD media is bad.
sometimes, Ubuntu is unable to read ISO images from the NTFS partition...
Well, do reply..if you need more help..

---

