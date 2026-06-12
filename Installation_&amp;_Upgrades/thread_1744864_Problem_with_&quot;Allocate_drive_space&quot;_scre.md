---
title: "Problem with &quot;Allocate drive space&quot; screen"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by garble on 2011-04-30
On the Ubuntu website, they have [a screenshot]("http://www.ubuntu.com/sites/www.ubuntu.com/files/active/natty/04-allocate-drive-space.jpg") of installing 11.04 from 10.04. The options are: Install 11.04 alongside 10.04, Upgrade 10.04 to 11.04, Erase 10.04 and reinstall, Something else.

Erase 10.04 and reinstall is the option I want, but that is not an option when I actually try to install it. The installer detected that I have Ubuntu 10.04 and Windows XP, and gave me the following options: Install 11.04 alongside both, Erase both OSes and install 11.04, Something else.

I want to install 11.04 over 10.04 and leave Windows alone. I guess I have to do the partition stuff, but I don't want to screw anything up. Can someone please tell me what to do? Here's how my partitions are currently set up.

/dev/sda1 ntfs 54303MB
/dev/sda3 ext3 19567MB
/dev/sda5 swap 896MB
/dev/sda2 fat32 5248MB

---

### Post by Quackers on 2011-04-30
If you choose the "something else" option then just use sda3 as your new Ubuntu root partition, with a mount point of "/" and a file system type ext4. That will over-write 10.04.

---

### Post by garble on 2011-04-30
Thank you for the quick response, I will give that a try and report back.

---

### Post by garble on 2011-04-30
Worked like a charm, thanks again!

---

