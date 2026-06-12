---
title: "Boot"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by EduardoAB on 2008-01-03
I have one 20 GB HD used just for data and a 80 GB HD where Windows XP is installed. The former HD is already empty and I´d like to install Ubuntu in it and also not to do any change on the 80 GB HD to be able to boot either way. Is it possible? If so, could you explain me how to proceed during the installation.
Thanks

---

### Post by Pumalite on 2008-01-03
What hard drives do you have?
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Do this with your 20 GB drive:
10 GB for '/'
1 GB for /swap
The rest for /home
Install Ubuntu, go Manual and use the already made partitions. Let Grub install to MBR (you'll have dual boot)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

