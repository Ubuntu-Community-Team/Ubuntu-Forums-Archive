---
title: "Installation in Compaq Presario"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by Tacuabe on 2008-04-11
Hi everybody!

I've just purchased a Compaq Presario V3618LA (I'm located in Montevideo, Uruguay) and am experiencing the infamously popular difficulties with the Broadcom WiFi drivers. Needless to say, I have found and read countless reports and solutions both in this forum and others, before asking for help.

In my particular case, installation of Ubuntu 7.10 stops with the usual error message BEFORE entering the GUI session and will not even activate the Live version. So there's no way to apply the many solutions posted or how to find out which Broadcom module is actually installed. There's nowhere to type any command, no CLI.

Upon reading the following thread: [http://backports.ubuntuforums.com/showthread.php?p=4408039](http://backports.ubuntuforums.com/showthread.php?p=4408039) it appeared that using the alternate CD I should have been able to install Ubuntu and THEN tackle the problem. Not so. I cannot boot from that CD. I checked the BIOS for boot order and everything seem OK. Am I missing something?

My other question is the following. The Compaq comes with Vista Home Basic pre-installed (it really sucks!) which I intend to keep for the sole reason of testing installation of a software we produce locally. It is designed to run in Windows systems which still are the majority in many places. The idea is to assign as little space in the HDD as possible to Vista. I read somewhere else, that before installing Linux the space should be shrinked with the own Vista utility, which does so to about 50% (still too much for my liking and needs). I wonder if this can be modified, if and when I reach the point of installing Ubuntu, with the usual partitioning tool.

Any help with this two issues will be much appreciated.

Edit:

Some time ago I downloaded Damn Small Linux (DSL) in order to test a different system (I was already hooked with Ubuntu) and had success with the USB version. It enables me to run Linux in any machine without installation. The Compaq Presario accepts DSL from the USB pen-drive and will also boot from a DSL CD. I wonder if this might be useful to tackle the above problem. Please bear with me, I've been using Ubuntu for only one year!

---

### Post by David Robertson on 2008-04-11
I've seen this before. The reason Vista won't shrink it any further is the Master File Tables. I havn't found any software that will reorganise these well enough to free up space at the end of the partition. And of course if you use the recovery disks it wipes out everything.

The only method I have found to half get there is to use the recovery disks, then immediately shrink the partition before windows starts filling it up with special upgrades.

---

### Post by Pumalite on 2008-04-11
XP used to have Page File that you could set to zero and would allow you to shrink it further.
How much memory do you have?

---

### Post by Tacuabe on 2008-04-17
Thanks David and Pumalite. I don't have any recovery diksfor Vista. It was installed as OEM and the only item available is the sticker on the back of the machine. RAM memory is 1 Gb. Isn't it possible to further shrink Vista partition AFTER or DURING Ubuntu's installation?

Otherwise, I am tempted to wipe-out Vista altogether and rely on VirtualBox for the software testing. However, I'm not quite sure on the correct procedure and still fear the Broadcom drivers will keep on bothering me during the new attempt to install Ubuntu.

Which takes me to the first problem I posted. Any suggestions on how to circumvent the WiFi drivers issue and get along with the installation?

Thanks again folks!

---

### Post by Pumalite on 2008-04-17
If you are going to use Vista, you have to partition with Vista partitioner. You cannot partition with Ubuntu CD.

---

