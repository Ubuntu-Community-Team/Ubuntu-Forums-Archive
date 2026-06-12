---
title: "problem with partitions when installing"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by marie-p on 2010-01-07
I have a asus eeepc and after running the version of linux that came with the computer, I changed to ubuntu netbook remix 9.04 a little while ago. However, I ran into problems because when installing ubuntu, the other system was not removed. I was therefore left with only 4GB of space for ubuntu. 
I reinstalled ubuntu today (9.04 again, I could not find a 9.10 usb image) and specified "use full disk"
Once again, I only had 4GB of space.

I tried again and realized that my memory is divided into two drives, one of 16GB and one of 4GB. After trying unsuccessfully to merge the two (playing around in the "manually specify partition" section without really knowing what I was doing), I installed ubuntu on the 16GB drive. But my computer still boots from the 4GB drive. 

How do I merge the two drives?

---

### Post by darkod on 2010-01-07
It is possible that the 16GB and 4GB drives are separate and in that case you wouldn't be able to merge them at all.
Boot with the Try Ubuntu option, and in terminal execute:
sudo fdisk -l

Copy the result here. That should show you your partitions and you will know more.
Otherwise, go into BIOS and try to set the 16GB drive as first boot device and that should allow you to boot your Ubuntu 9.04.

---

### Post by marie-p on 2010-01-07
I was not able to connect the eeepc to the internet, so it's a bit hard to copy and paste, but the results listed three disks:

Disk /dev/sda: 4034MB....
/dev/sda1...
/dev/sda2...
/dev/sda5...

Disk /dev/sdb: 16.1GB...
/dev/sdb1...
/dev/sdb2...
/dev/sdb5...

Disk /dev/sdc: 4013MB


I am not sure what the sdc could be (the usb installation drive maybe?) but the other two look like the ones I saw when I was installing ubuntu.

---

### Post by ronniestamps on 2010-01-07
Your 16g and 4g hard drives are physically separate. When installing, choose sdb, that's your 16g hard drive.

---

### Post by marie-p on 2010-01-07
ok, thanks.

I now have ubuntu installed on both drives and I set the computer to boot from the 16GB drive. How do I remove ubuntu from the other drive now?
Once in ubuntu, I can see the 4GB drive but I cannot delete what is on it or format it.

---

