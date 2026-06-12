---
title: "Wrong disk formated for ubuntu install"
date: 2011-09-16
forum: Installation &amp; Upgrades
---

### Post by subsailor20 on 2011-09-16
Ubuntu 11.04 install over Linux mint.

Install has 3 choices presented, 1. Add ubuntu along side of Linux mint, 2. Add ubuntu over Linux mint use entire disk, 3. Other

The install function obviously recognised Linux mint install location!!! I selected number 2. The install should have automatically used the already identified disk /dev/sda for install.  It didn't! Instead it started to install to /dev/sde.  With GREAT HORROR I tried to stop the install, but as anyone knows is not possible by this time.

/dev/sde contained the complete backup of 3 months of detailed work.

How does one un-screw-up this mistake made by the install system.  By the way don't bother to tell me that I should have looked up at the question "What disk do you want to install to" message.

Install should have known since my selection of questions 2 provided install with the unique and  precise disk to have used.

I'm not a beginner, that happened a long long time ago.  This is a basic failure by a software/system designer and poor test procedures.

I've tried ddrescue and looked at others and would appreciate any help in trying to regain some of the lost files. I've had no luck sofar.

---

### Post by Megaptera on 2011-09-16
Is this guide any help?
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Or this "PhotoRec  is  file  data  recovery software designed to recover lost
       files including video, documents and archives from Hard Disks and CDRom
       and lost pictures (Photo Recovery) from digital camera memory. PhotoRec
       ignores the filesystem and goes after the  underlying  data,  so  it&#8217;ll
       work  even if your media&#8217;s filesystem is severely damaged or formatted.
       PhotoRec is safe to use, it will never attempt to write to the drive or
       memory support you are about to recover lost data from."

From: [http://manpages.ubuntu.com/manpages/intrepid/man1/photorec.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/photorec.1.html)

---

### Post by ottosykora on 2011-09-17
somehow depends also as what file system was used on that data partition. If the partition was not too full, it is also possible to recover the partition with program called testdisk and then try to recover from there.
If it was a windows partition, there is fair chance that you recover most, as there contents are rather written at the begining of the volume, where the linux parts would be located rather in the middle of the volume.

We had here one guy who recovered whole xp installation even the partition was formated to ext3 and ubuntu installed on it.

Important may be: do not run anything on that computer, all attepmts to recover something should happen from some bootable media as CD or so from now.

As far as the installer behaivour, well if you tell ubuntu staff they will tell you such thigs are not possible, those hundreds or thousands of help requests in forums are because the user did all wrong.
I know personally that the installer is kindly expressed suboptimal.

---

