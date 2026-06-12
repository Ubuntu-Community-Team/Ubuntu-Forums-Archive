---
title: "upgrade from 7.04 to 7.10"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by shinigamicpt on 2008-11-22
Hey i am tryin to upgrade step by step to 8.10 so i dont lose any data. I am using the update manager but everytime i try i get an error which is:

Failed to fetch [http://my.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://my.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb) Size mismatch
Failed to fetch [http://my.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://my.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb) Size mismatch
Failed to fetch [http://my.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb](http://my.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb) Size mismatch


how am i to solve this? thankyou

---

### Post by tommcd on 2008-11-22
> **shinigamicpt said:**
> Hey i am tryin to upgrade step by step to 8.10 so i dont lose any data. I am using the update manager but everytime i try i get an error which is:

Failed to fetch [http://my.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://my.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb) Size mismatch
Failed to fetch [http://my.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://my.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb) Size mismatch
Failed to fetch [http://my.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb](http://my.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb) Size mismatch


how am i to solve this? thankyou
Ubuntu 7.04 reached end of life in October:
[http://www.ubuntu.com/news/ubuntu-7.04-end-of-life](http://www.ubuntu.com/news/ubuntu-7.04-end-of-life)
If you are trying to go from 7.04 --> 8.10, I would just do a clean install of 8.10. It will be faster, and will be much less likely to cause problems. If you have a separate /home it will take less than 30 minutes for a clean install. If you don't have a separate /home, now would be a good time to repartition your drive to create one.

---

