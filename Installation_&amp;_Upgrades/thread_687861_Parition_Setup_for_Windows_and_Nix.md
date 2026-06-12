---
title: "Parition Setup for Windows and *Nix?"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by Pharoz on 2008-02-04
Hello,

I currently have one harddrive and I would like to install multiple linux flavors (ubuntu, fedora, centos, etc) and also windows xp. I'm wondering if there's anything special I need to do to the partition. For example, should the windows partition be first or last? Should I install all the linux os first, then windows, or vice-versa? I would like the data to reside on an NTFS partition so I can access it from windows and linux easily without installing any readers.

I currently do have ubuntu and windows running on the same drive, but am unable to install additional linux OS (error saying it can't allocate free space). Partition is as follows:

ext3 - Ubuntu
ntfs - Windows
ntfs - Data
linux-swap

Thanks!

---

### Post by Odrodzona-Sarmacja on 2008-02-04
The windows must be primary partition. The rest i think you can safely park in logic partitions.

---

### Post by Pharoz on 2008-02-04
Thanks. I will repartition the system then and set up Windows as the first primary partition then with the following format. Hope it works...

ntfs - windows
ntfs - data
ext3 - ubuntu
ext3 - fedora
ext3 - centos
ext swap

---

### Post by Odrodzona-Sarmacja on 2008-02-04
Remember to have 8 gb for partitions and 512kb-1mb for swap... Also you maybe want to set up /home partition (ext3) between centos and swap just only for your ubuntu's sake as it is somehow unstable and prone to reinstallation due sudden problems with it :D

Good luck!

---

### Post by Pharoz on 2008-02-08
Ok, so far so good. Here's the final partition layout in case anyone else decides to do this in the future.

ntfs - primary - windows
ntfs - primary -  data
ext swap 
ext3 - logical - ubuntu
ext3 - logical - fedora
ext3 - logocal - centos

Tried setting up a ext3 primary partition, but that errored out, so you'll have to set it up as logical. Also, I used the Ubuntu LiveCD to set up the partition on a new HD and then restarted with Ghost 8.3 and ghosted my current windows and ubuntu partition (yes, you can ghost the ext3 partition) onto that new drive. Booted up with error about finding grub files, so I had to reload the grub config using the LiveCD and that allowed me to boot perfectly into Ubuntu or Linux.

Interestingly enough, I have Wine installed in Ubuntu and can lauch some applications from the windows or data partition just fine. :) Sweetness!

---

