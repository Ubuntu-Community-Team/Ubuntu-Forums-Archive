---
title: "installing ubuntu &quot;no root file system is defined&quot; with more problem."
date: 2013-07-31
forum: Installation &amp; Upgrades
---

### Post by sinan_ar_kurt on 2013-07-31
Well i got brand new ultrabook.I wanted to install ubuntu.Windows 8 is pre-install and I got uefi.I disabled secure boot and rapid start up.But still i cant see "allocate drive space" question.Instead i see blank page and i can click continue button.After that installtion is normal until i see "no root file system is defined". I mean i cant choose my drive because dropbox doesnt show any hdd.What am i suppose to do next?(Btw I tried to install both 12.04 and 13.04)

---

### Post by grahammechanical on 2013-07-31
How are you installing? Are you using the Install Alongside option? Or the something else option? I think that you are using the Something else option but when you get to the partitioner section you are not giving the partition you want Ubuntu installed into a mount point of /

Select the partition, click Change and a dialog box will appear. Change Do Not Use to Ext4 as the file system. And at the mount point menu select /  and accept these settings. Now you have defined a root file system.

But I wonder about the failure to show you any information under the Allocate Drive space section. I guess that the hard disk has a partitioning scheme that the Installer cannot read or that there is not a partition available for Ubuntu to install into.

I have heard that if you have UEFI them you must run the live session as UEFI. I cannot advise you further.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by sinan_ar_kurt on 2013-07-31
Thanks for your answer but The problem is that; it doesnt ask me "along side" or "something else" question.

---

