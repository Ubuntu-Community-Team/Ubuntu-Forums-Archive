---
title: "No Resume Image - AGP Graphics - Please Help!"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by matt123h on 2008-11-09
I had installed Ubuntu 8.10 a while ago, and it was running perfectly on standard Intel graphics. This morning I installed an nVidia AGP card, and Ubuntu offered to activate nVidia drivers when it was detected. After doing this and rebooting, the computer loads the Ubuntu loading screen before going into the console. This is the text:

> Boot from (hd0,0) ext3  ca3668dd-c483-447a-b44d-4050672d5ae3

Starting up ...

Loading, please wait...

usplash:setting mode 1600x1200 failed

usplash:Using mode 1280x1024

19+0 records in

19+0 records out

kinit: name_to_dev_t(/dev/disk/by-uuid/9dc1ac7e-1f92-40c0-a476-a1b861976392) = dev(8,5)

kinit: trying to resume from /dev/disk/by-uuid/9dc1ac7e-
1f92-40c0-a476-a1b861976392

kinit: No resume image, doing normal boot...


Ubuntu 8.10 Ubuntu ttyl1

Ubuntu login:

I have read of similar errors on the internet, but none of the fixes seems to work for me.

I should add that I am very inexperienced with Ubuntu, and I would appreciate any help!

---

### Post by ericesque on 2008-11-09
I had the same issue with kinit: No resume image

I simply reinstalled over top of my previous install.

If you pop in the live cd and start a standard install,
select manual for partitioning when you get there. You'll
want to select your linux partition and click edit partition.
Select the correct mount point, but do NOT select 'format partition'.
Repeat the same process if you have other linux partitions,
then proceed with the install.  It will warn you that you're 
not formatting and ask you if you want to continue-- just click
okay.

The only thing you'll lose is any updates you've installed
and any programs you've installed.  Your data will be intact
and any settings you've set for default packages 
(pidgin, firefox, etc) will also be there.

I'll try to keep an eye on this thread, but PM me if you
get stuck.

---

