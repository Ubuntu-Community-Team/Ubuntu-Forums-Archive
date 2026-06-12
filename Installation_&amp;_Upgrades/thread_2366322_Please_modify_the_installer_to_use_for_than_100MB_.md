---
title: "Please modify the installer to use for than 100MB for the boot volume!"
date: 2017-07-16
forum: Installation &amp; Upgrades
---

### Post by mnealbarrett on 2017-07-16
There is a change that I would like to see done to the Ubuntu installer. I find it totally annoying that when I install Ubuntu on my 2 TERABYTE hard drive, the installer only allocates a measly 100 megabytes for the boot volume. This is annoying because Linux kernels are slowly growing in size (as they obviously always have been), and I have to manually perform an "apt-get autoremove" every single time I want to do an extensive update. Yes, there are work-arounds, but it isn't easy when you want to set up a Ubuntu install with LUKS and LVM. The work-around takes 10 times as long and it is easy to make a mistake while doing it.

I would like to see the Ubuntu installer modified slightly to have the option of asking the user for the size of the boot volume, or detecting that Ubuntu is being installed on a drive with plenty of space on it and setting the boot volume to a much bigger size. On my 2 TB drive, an extra 500 MB for the boot volume would not be missed.

---

### Post by oldos2er on 2017-07-16
Developers don't usually hang out here, so if you want your request to be seen by them I suggest you file a bug on launchpad.net. 

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

