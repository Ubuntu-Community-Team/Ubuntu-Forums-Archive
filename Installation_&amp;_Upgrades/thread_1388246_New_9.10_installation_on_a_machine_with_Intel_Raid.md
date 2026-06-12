---
title: "New 9.10 installation on a machine with Intel Raid"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by ucuntu on 2010-01-22
Hello everyone.


This question is going to flag me as being a bit green to Ubuntu, but I must confess that in 15+ years in I.T., I have never had such a hard time understanding the partitioning scheme........

Here's where I'm at.

I installed from the 9.10 live CD and selected the option to use the entire disk.  The system has an Intel raid controller built in to the motherboard and two 80GB hard drives in a mirrored configuration.  The system has previously been used with both XP and FreeBSD and never had an issue with partitioning or, more importantly, getting the boot manager to work.

So the live CD partitioned my hard drives, installed all the software and mount points, and claims that everything is finished.  When I reboot, no boot device is found.  If I then boot again from the live CD and select the option to boot from the hard disk, it does and I am in fact typing this message from the system.  However, nothing I can do will make the thing boot without the bloody CD.

I've spent hours trying to figure out how to make grub work, or how to fix the MBR but no luck.  The drives don't show up as /dev/hda or as anything logical that I can discern, so I can't even construct a workable install-grub command.  Doing a df gives me this:

/dev/mapper/isw_bijdhbibeb_Volume01
                      73955516   2750748  67447972   4% /
udev                    508404       188    508216   1% /dev
none                    508404       368    508036   1% /dev/shm
none                    508404        88    508316   1% /var/run
none                    508404         0    508404   0% /var/lock
none                    508404         0    508404   0% /lib/init/rw
none                  73955516   2750748  67447972   4% /var/lib/ureadahead/debugfs
/dev/sr0                706532    706532         0 100% /media/cdrom0

which is not very informative, is it?  FreeBSD was never such a pain to make boot.

Frankly, I'm not very impressed that a clean install (non dual boot) on such a standard hardware configuration could be so difficult to make the boot loader work.  Documentation on this subject is voluminous but very shabby.  I have searched and searched and I cannot find any mention of hardware mirrored IDE or SATA drives, nor what dev they would show up as.  Very frustrating.  Every tutorial I've read on installing grub2 or grub just doesn't work, usually because the dev is not right.

Can anyone shed some light on this bizarre behavior and perhaps offer some advice that will allow me to boot this system without the use of a live CD?


Thanks!

---

### Post by limey_rick on 2010-04-26
When you say that it will not boot, do you see any messages that indicate errors or other problems?

With the Intel Raid setup, you are trying to install on a LINUX DMRAID setup or FakeRaid most likely. I had problems getting GRUB to recognize a windows partition I had that was a RAID setup, so this may be a GRUB problem, but here is a link that may help you figure out the issue.

[https://help.ubuntu.com/community/FakeRaidHowto#Ubuntu%209.10%20%28%20Karmic%20Koala%29](https://help.ubuntu.com/community/FakeRaidHowto#Ubuntu%209.10%20%28%20Karmic%20Koala%29)

Please let me know how this goes.

---

