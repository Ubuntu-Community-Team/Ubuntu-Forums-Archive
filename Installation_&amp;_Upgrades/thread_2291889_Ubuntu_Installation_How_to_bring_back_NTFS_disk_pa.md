---
title: "Ubuntu Installation: How to bring back NTFS disk partitions from logical volume LVM"
date: 2015-08-23
forum: Installation &amp; Upgrades
---

### Post by KP_Singh on 2015-08-23
Hi,

I am new to ubuntu. I removed my windows OS & tried to switch to ubuntu 13.04.
My system had 4 partitions (NTFS). When I tried to install ubutu 13.04 with boot-able USB today, During installation process at the window "Installation type", by mistake, I chose option "use LVM with new installation" instead of "something else : create partition yourself". So all partitioned converted to one LVM partition. I have very important data and I am not able to mount it or revert it to back in previous 4 partitions.

Some body suggested about testdisk tool. it is also not able to install at boot-able USB....

Please help me to get my data back & all partitions as well.

thanks

---

### Post by Bashing-om on 2015-08-23
KP_Singh; Yuk !

I do feel your you.
I do think at this point 'testdisk' is your better option. Best done from an image of the hard drive.
see:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)
[http://ubuntuforums.org/showthread.php?t=2112112](http://ubuntuforums.org/showthread.php?t=2112112)

[INDENT][INDENT]good luck
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-08-23
I can't help with the LVM problem (I try and avoid LVM!) but I can advise that 13.04 is dead and has reached end-of-life. No longer supported. Once you're back up and running, I suggest a supported release, 14.04 LTS, a long-term support release which is supported until 2019, or 15.04, January 2016.

Good luck unravelling it. You are on the right track realising that 'Something Else' is the way to go. :)

---

### Post by KP_Singh on 2015-08-23
Hi Bashing-OM,

Thanks for the reply.
I went through to links but they are not working for me.
Testdisk is not geting downloaded/installed in boot-able USB.
As per m understanding, you are sayin that I must install the ubuntu at my hard drive. But due to installation I can lost the data. 

Pls correct/suggest me if I'm wrong.

---

### Post by Bucky Ball on 2015-08-23
Download [System Rescue Disk]("http://www.sysresccd.org/SystemRescueCd_Homepage") and create a bootable USB. Testdisk is included on it. I also advise [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec").

An LVM volume manager guide is also on the first link above. Might give you some clues.

---

### Post by yancek on 2015-08-23
I don't believe Testdisk/Photorec software is available as a bootable medium but as suggested above, the SystemRescueCD (as well as a Knoppix DVD) contain both.  You would be better off downloading either and putting them on a bootable medium, CD for SystemRescueCD or DVD/flash drive for Knoppix.  The more often you boot or use the computer you want to recover data from, the less data you will be able to recover.

---

