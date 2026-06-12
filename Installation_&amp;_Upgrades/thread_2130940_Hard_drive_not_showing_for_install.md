---
title: "Hard drive not showing for install"
date: 2013-03-31
forum: Installation &amp; Upgrades
---

### Post by devin0 on 2013-03-31
I have had Debian installed on a machine for a while now and want to install Ubuntu 12 64 bit on it. I fire up the CD, the installer launches, but when it comes time to pick my hard drive, it will not let me. /dev/sda is the selected choice, however it wont allow me to create partitions.I cant click any of the buttons, and when i click proceed it tells me there is no root partition. I opened up Gparted and deleted all my old debian partitions on /dev/sda, i thought the might be getting mounted automatically or something, preventing me from using that drive, gave it a restart but still no luck. 


Any help is appreciated.

---

### Post by carl4926 on 2013-03-31
Post a screen of what you see in Gparted

---

### Post by devin0 on 2013-03-31
[[img]http://s20.postimg.org/m67l0du3t/ubuntu_Issue2.jpg[/img]](http://postimg.org/image/m67l0du3t/)

[[img]http://s20.postimg.org/wrrgce0fd/Ubuntu_Install_Issue.jpg[/img]](http://postimg.org/image/wrrgce0fd/)

Buttons New partition table, add, cahage, etc are not clickable.

---

### Post by carl4926 on 2013-03-31
So is the drive partitioned?
Try creating a new partition table (msdos)
Then create the partitions you want
eg:
swap
ext4 for root
ext4 for home

Then reboot and try the install going the 'Something else route'
[https://www.dropbox.com/s/zci3ny43zwh1u1w/12.10_advanced.png](https://www.dropbox.com/s/zci3ny43zwh1u1w/12.10_advanced.png)

Then set the mount points
[http://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png](http://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png)

---

### Post by darkod on 2013-03-31
This might be an error in the partition table, so it doesn't display them correctly. Creating new partition table may solve it if this is the case.

It can also be a case of the disk naving raid meta data leftovers if it was ever used in fakeraid. Boot ubuntu in live mode, open terminal and try:
```
sudo dmraid -Er /dev/sda
```

If that tells you it removed meta data, try to install and it should be fine.

---

### Post by devin0 on 2013-04-01
Thanks darkod, that command fixed it right up. I don't recall having a fakeraid but it seems to have fixed the problem, Ubuntu is installing now. Thanks.

---

