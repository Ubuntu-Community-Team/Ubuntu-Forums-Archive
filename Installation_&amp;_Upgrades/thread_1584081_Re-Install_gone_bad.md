---
title: "Re-Install gone bad"
date: 2010-09-28
forum: Installation &amp; Upgrades
---

### Post by mmcl on 2010-09-28
Here you have a technically challenged granny.  Having used Ubuntu 7.04 for 2.5 years, when the 10.04 upgrade wouldn't take, a few weeks ago, I felt optimistic about re-installing, using 10.04.1 (about 2-3 weeks ago). It was waaaay harder than the first time -- I burned my own CD (which I'd never done before), and maybe that had something to do with it.  The re-install was confusing; I kind of muddled my way through it.  Ended up with various issues, and now am thinking a do-over may be in order.

The first indication that all wasn't well was a notice that there wasn't much hard drive left.  It didn't seem like a huge problem, so I ignored it. I had learned how to to tar.gz backups and was able to restore Evolution intact, which was great.  Had to go looking for a printer  driver, and found it (a triumph, in my mind). I had done something to the CD player in burning the CD and installing 10.04.1, and haven't been able to undo it, so my CD player icon now says, U3 System and I can't get anything to play on it, I can't even seem to connect with anything but "U3 system," which has "autorun", "Launchpad", and "LaunchU3" on it.  

I let that sit and had some adventures loading and then deleting some videos, which convinced me that I need to deal with the lack of space on the hard drive.  (This was never a problem with 7.04, but I hadn't tried videos).
I've sort of recovered from that, (can do most applications again, but Evolution is being dicey). I'm wondering if I somehow messed up the original installation.

When I look at Computer, it says:
20 GB Hard Disk
14 GB filesystem

Questions:
So...if I try to re-install again, can someone point me towards an clear  path? (If there was guidance on my CD, I didn't look hard enough for it.)
Maybe I should re-burn the CD? (It took over 24 hours). 
Is there a version that is idiot-proof for installation, as I had found 7.04 to be?
Someone has mentioned partitions to me -- I only vaguely understand this term; can I create a partition and save myself some work?

Any guidance would be much appreciated!

Thanks,

Martha

---

### Post by mörgæs on 2010-09-28
On a 20 GB hard disk, there should be more than enough space for Ubuntu. 

A backup copy of your files and then a reinstall of 10.04 will probably be a good choice. On a certain step in the process, you can select 'use entire drive for the new Ubuntu installation' (or something similar) - just choose this and everything should go well. Best is to have internet access by wire during the installation.

There is no need to restore Evolution or other applications from a backup. It comes automatically in the installation. 

If your computer is low on memory, trying the alternate 10.04 installer might be the best option.


Say hello from me to the troll under the bridge :-)

---

### Post by mikewhatever on 2010-09-28
> **mmcl said:**
> Here you have a technically challenged granny.  Having used Ubuntu 7.04 for 2.5 years, when the 10.04 upgrade wouldn't take, a few weeks ago, I felt optimistic about re-installing, using 10.04.1 (about 2-3 weeks ago). It was waaaay harder than the first time -- I burned my own CD (which I'd never done before), and maybe that had something to do with it.  The re-install was confusing; I kind of muddled my way through it.  Ended up with various issues, and now am thinking a do-over may be in order.

Can you detail what was hard about the 10.04 installation. Sometimes, simply defining the hardship helps to see it in the proper proportion. Did you install 7.04 to a blanc disk?
As an aside, upgrading from 7.04 to 10.04 is not supported.

> The first indication that all wasn't well was a notice that there wasn't much hard drive left.  It didn't seem like a huge problem, so I ignored it. I had learned how to to tar.gz backups and was able to restore Evolution intact, which was great.  Had to go looking for a printer  driver, and found it (a triumph, in my mind). I had done something to the CD player in burning the CD and installing 10.04.1, and haven't been able to undo it, so my CD player icon now says, U3 System and I can't get anything to play on it, I can't even seem to connect with anything but "U3 system," which has "autorun", "Launchpad", and "LaunchU3" on it.  

I let that sit and had some adventures loading and then deleting some videos, which convinced me that I need to deal with the lack of space on the hard drive.  (This was never a problem with 7.04, but I hadn't tried videos).


The lack of hard disk space suggests that you did not reinstall 10.04 (removed 7.04 and installed 10.04 in its place), but rather installed 10.04 on to another partition next to 7.04.
I am simply guessing, but you could show us the partitions on the disk by posting the output of the following command from Applications->Accessories->Terminal.

> I've sort of recovered from that, (can do most applications again, but Evolution is being dicey). I'm wondering if I somehow messed up the original installation.

When I look at Computer, it says:
20 GB Hard Disk
14 GB filesystem

Questions:
So...if I try to re-install again, can someone point me towards an clear  path? (If there was guidance on my CD, I didn't look hard enough for it.)
Maybe I should re-burn the CD? (It took over 24 hours). 
Is there a version that is idiot-proof for installation, as I had found 7.04 to be?
Someone has mentioned partitions to me -- I only vaguely understand this term; can I create a partition and save myself some work?

Any guidance would be much appreciated!

Thanks,

Martha

The problem with idiot-proof installation guides is they are a myth. Everyone's initial setup and knowledge are different, and often are the goals, so that taking all these into account would either be impossible, or will turn the guide into a dissertation.
Anyway, here is a guide -> [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
It shouldn't take longer then 20 minutes to burn a cd.

---

