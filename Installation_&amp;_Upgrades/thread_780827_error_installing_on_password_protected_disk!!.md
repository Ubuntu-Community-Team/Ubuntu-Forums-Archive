---
title: "error installing on password protected disk!!"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by adamantivm on 2008-05-03
Hi,

I just spent about two hours trying to install Ubuntu or Debian on a hard drive I had saved from an old IBM notebook a while ago until I just found the reason of the problem (obvious if you read the header), just thought I would share it in case somebody else runs into the same problem.

The symptom was that, whenever I got into the partitioning part of the installation I always got the following error and was unable to move on:

"Input/output error during read on /dev/ide/host2/bus0/target0/lun0/disc

ERROR!!!

Retry
Ignore
Cancel"

Searching in Google gave me possibilities such as:
- broken cable
- faulty disk

Since I had just bought the adapter for notebook HDD to regular desktop ATA and really wanted this working I got a little stubborn and searched for low-level formatting tools to see what was really up with this disk. Btw, at least for my hdd, a good resource turned out to be: [http://www.hgst.com/hdd/support/download.htm](http://www.hgst.com/hdd/support/download.htm)

To my surprise, when trying to run tests using the "Drive Fitness Tool", I got the error:

"Device is password protected and can not be tested - Disposition Code = 0x22"

That was a "slap in the forehead" moment to me. I should have thought about this before! Now I have to find an older IBM ATA-capable notebook or some other way to remove my password for the disk. But I'm happy! the disk is probably not broken!!

Hope this helps others.

Regards,

Julian

P.S.: Would be happy to hear if anybody knows of any tool to change (remove) the HW password of a HDD, assuming I know the password

---

