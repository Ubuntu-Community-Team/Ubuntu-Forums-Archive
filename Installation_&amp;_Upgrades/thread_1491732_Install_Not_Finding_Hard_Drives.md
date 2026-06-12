---
title: "Install Not Finding Hard Drives"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by Razorback on 2010-05-23
Having a little problem with 10.04 installation.  I have two hard drives installed on my PC.  One that had Hardy Heron and one data.  When the install program launches from a CD boot, it fails and drops me to a live session to check out the problem.  I can see both drives and mount them but if I then launch the installer, it does not give either as an option for installation.  Any insight would be much appreciated.

---

### Post by bckerr on 2010-05-24
I have the same problem, I have the PC restart and have my Ubuntu CD in. It loads the first couple of screens asking the time and the keyboard layout. Then it goes to install I guess, but can't find my partitioned drive. It worked fine on the older Ubuntu. 

What's with this crappy Linux so far?

---

### Post by darkod on 2010-05-24
That usually happens if the disk has been used in raid and has metadata remains on it. Ubuntu doesn't show it in the installer, I guess to prevent overwriting the raid by error.

If you are not running raid, load live mode and in terminal do:

sudo dmraid -r -E /dev/sda (and for /dev/sdb too if needed)

That should ask you to confirm you want to remove the raid settings. After that it should be fine.

---

### Post by Razorback on 2010-05-24
OK, I will give a try.  I am not running a RAID setup nor has either disk been used in that fashion.  Funny that both disks are being ignored.

---

### Post by dino99 on 2010-05-24
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

