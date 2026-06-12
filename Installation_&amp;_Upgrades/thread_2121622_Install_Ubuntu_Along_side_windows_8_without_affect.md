---
title: "Install Ubuntu Along side windows 8 without affecting my Local Drives of windows."
date: 2013-03-02
forum: Installation &amp; Upgrades
---

### Post by Noor Ahmed on 2013-03-02
After Trying it so many times i have come here.
I have windows 8 on my laptop. I installed ubuntu 13.04 along side windows 8. But when I opened, windows 8, one of the local drives was not there.
Then I uninstalled both of them. Again I installed windows 8 and then ubuntu 13.04. But Again the same problems.

And one more problem is that I can install any software on Ubuntu 13.04. It Just gives a simple error and terminate.
On windows 8 there is no matter.

Still one more problem. That is I do not have DSL connection, I use EVDO wireless Internet USB. When USB is inserted into computer. There is a software in that internet USB, that you install to use internet on that USB. Now when I am on windows 8 and plug in the Internet USB, if software is not installed it tell me to install software. and by just clicking the .exe of that USB, it is installed and I can use Internet from USB. But on Ubuntu I don't know that whether USB is pluged or not. And it does not appear in the launcher too.


Any suggestions on how to fix these problems???

---

### Post by darkod on 2013-03-02
1. The version 13.04 is still not released. It is not advised to use a version still in development as your main OS. Only if you want to test it, and be prepared that things will break. If you want a stable version, and supported long time, get the 12.04 LTS. The LTS versions are supported for 5 years.

2. If you installed ubuntu on one of your disks taking the whole disk, windows will not see it because it can't read linux partitions. So, if looking in Computer, it will not be there. If you still want to use part of that disk for keeping files accessible from windows, you will have to create one ntfs partition on the disk and use the rest for ubuntu.

3. Usually you don't need the software for 3G usb dongles in ubuntu. But you do need to know your provider APN details. Then go into Network Manager and create the connection. It doesn't matter that the software doesn't start automatically in linux, you don't need it.

---

### Post by Mark Phelps on 2013-03-02
If the EVGO USB dongle is 4G, it's likely not to work. 

 I have a 4G LG USB dongle and it works in windows ONLY because I am able to install software there that installs special drivers for the USB dongle.  I researched this at length, and in Linux, there are no drivers that will work the the LG device.  

It may be because it's 4G, or simply because it's LG, but either way -- it does not work.

---

