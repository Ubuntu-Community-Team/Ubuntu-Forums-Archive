---
title: "Boot repair output - what now?"
date: 2015-02-01
forum: Installation &amp; Upgrades
---

### Post by russab on 2015-02-01
Hello - I am a complete newbie.

I have tried to install various versions of ubuntu on my old Dell D600 laptop. I intended it to be solely ubuntu and begin to learn about this OS and apps etc..

After installing ubuntu 14.04 - and failing due to the 'pae' issue...I started trying alternatives xubuntu - lubuntu and versions going back...back until I reached ubuntu 12.04

I booted ubuntu 12.04 from CD, used the 'forcepae' command line parameter at the appropriate place and eventually the system actually installed.

Upon re-booting I got
error: out of disk
grub rescue

I then re-booted on the CD - used the "try Ubuntu" option - ran a terminal window - ran the boot-repair commands as recommended on this forum - and got the following URL 

[http://paste.ubuntu.com/9997801/](http://paste.ubuntu.com/9997801/)

Would someone please advise me what I do now?

Many thanks :-)

---

### Post by oldfred on 2015-02-01
Some older BIOS will not let system boot from any files beyond 137GB, your hard drive is 160GB and many of your boot files ended up at 141GB on drive, see line 258 of Summary report.

About half of users I have suggested just shrinking / (root) to 100GB with gparted could then boot or maybe needed a full uninstall/reinstall of grub with Boot-Repair. Some it did not work.

I normally suggest 20 or 25GB / so all the main working files are closer together on hard drive and use rest of drive for /home or just  a /mnt/data partition. The /home is easier to configure when installing than a data partition is after the install. But you can only have the separate /home if you use Something Else and manually create partitions, mounts like / & /home, and formats like ext4 for each partition.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

---

### Post by russab on 2015-02-01
Dear oldfred

Thank you so much - all up and running now with the help of the great tip you gave and the links.

Very very grateful

Russ :-)

---

### Post by oldfred on 2015-02-01
Glad it worked. :)

---

