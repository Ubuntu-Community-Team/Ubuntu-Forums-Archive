---
title: "Dual Boot Newb issues"
date: 2014-11-04
forum: Installation &amp; Upgrades
---

### Post by mittleiderja on 2014-11-04
Hello,

I just built my first gaming computer and started with a fresh windows 8.1 install, followed by a fresh Ubuntu 14.10 install. Windows was installed first on the first partition, followed by Ubuntu on the next partition, with a small amount left for swap.

I have my SSD set to boot first on start up (both OS' are on the SSD) and Ubuntu automatically boots. Every guide I've seen and followed seems to think I'll get an option at boot up for which OS to start, but I am not getting that. If anything, with the way I have it set up, I feel like windows should be booting and not Ubuntu. What am I missing to give me the option of which OS at start up?

I do have a 2TB HDD also installed in the computer, but is currently 'clean' (empty and unformatted), and no USB sticks in it, so my only boot option at the moment is the SSD or the BD-RE, which does not have a disc in it.

I know windows was successfully installed because I was using it to download the Ubuntu ISO to make my install USB.

Any help greatly appreciated!



Other info: the build is a Gigabyte GA H87M mobo, haswell processor, GTX750Ti gpu and a LG BD-RE. Like I said, windows installed flawlessly (I partitioned the SSD before the install, leaving half of it for Ubuntu), and then Ubuntu did as well (after a couple problems with the video card that I got sorted out). Now it only boots into Ubuntu and I have no option of using Windows.

---

### Post by mittleiderja on 2014-11-04
Solved by editing the grub file. GRUB_HIDDEN_TIMEOUT_QUIET was =true. Setting it to =false gave me the boot options at startup and can now freely boot into windows or ubuntu.

---

### Post by Bucky Ball on 2014-11-05
Good news and took the words right out of my keyboard!

Please follow the second link in my signature to mark the thread as solved. Thanks and good luck. ;)

---

