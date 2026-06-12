---
title: "ubuntu installation dies at 77%"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by pontifex3 on 2007-05-14
Hi, im currently trying to install xubuntu on a laptop, i used the alternate cd (xubuntu-7.04-alternate-i386.iso), i checked the md5 sum when i downloaded it and after burning to its ok, when i start installing it first cant configure the network card but i dont mind that, the problem is that when it reaches 77% en the installing base system part, it stops working (ive left it over an hour and it wont get over it), in the lower part of the bar it says, collecting data for the installation report (im installing it in spanish to im not sure what it says in english but it should be something like that), and when i switch to the F4 console this is what it says

May 14 11:13:30 apt-install: Reading package list...
May 14 11:13:30 apt-install:
May 14 11:13:30 apt-install: Creating dependency tree
May 14 11:13:30 apt-install:
May 14 11:13:30 apt-install: Packages created
May 14 11:13:30 apt-install: reportbug
May 14 11:13:30 apt-install: the next new packages were installed:
May 14 11:13:30 apt-install: installation-report
May 14 11:13:37 kernel: [ 941.104000] hdc: media error (bad sector): status=0x5 1 { DriveReady SeekComplete Error }
May 14 11:13:37 kernel: [ 941.104000] hdc: media error (bad sector): error=0x34 { AbortedCommand LastFailedSense=0x03 }
May 14 11:13:37 kernel: [ 941.104000] ide: failed opcode was: unkown
May 14 11:13:37 kernel: [ 941.104000] hdc: error code: 0x70 sense_key: 0x03 asc:0x02 ascq: 0x00
May 14 11:13:37 kernel: [941.104000] end_request: I/O error, dev hdc, sector 308
May 14 11:16:57 init: Starting pid 2920, console /dev/vc/2: 'bin/sh'

and thats when it dies, does this mean i need a new harddrive or something? in the partitioning i gave root 5gb, swap 256mb, and home 15gbm any help appreciated, thanks!

---

### Post by pontifex3 on 2007-05-14
in the output, i wrote
packes created:
reportbug

i mean
packages recommended:
reportbug!

---

### Post by Death_Sargent on 2007-05-14
i recomend making the swap file twice the size of your physical ram. (mas swap, el swap necisito mas)

Also be sure to give root more space than your home unless you intend to never install anything (you could just have a 10gig root and 10 gig home) (mas root y menos home)

if it still fails try cleaning the CD lense if you can. oh  and be sure to reburn the CD

im sorry my spanish sucks

---

