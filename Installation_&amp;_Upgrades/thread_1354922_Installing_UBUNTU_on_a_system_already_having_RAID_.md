---
title: "Installing UBUNTU on a system already having RAID 0"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by goofy_goof on 2009-12-14
I have existing RAID 0 on which windows is installed. Now, I want to install UBUNTU 9.10 on a separate HDD and configure in such a way that GRUB is installed on the same HDD. I tried but looks like RAID 0 is recognized as MBR partition and GRUB cannot be configured on the same. I want the installer to recognize 2nd HDD as the primary HDD and configure GRUB on that one. I know there were some jumper settings on IDE but I have SATA HDDs. One way of doing this to disconnect RAID 0 HDDs and install UBUNTU. Once the installing is finished, connect those two HDDs back. But I am not sure if they'll be recognized as RAID 0 and I will not loose anything on that partition!

Can someone help??


Thanks,

Bimal

---

### Post by goofy_goof on 2009-12-14
Found a thread confirming my solution:
[http://ubuntuforums.org/archive/index.php/t-817122.html](http://ubuntuforums.org/archive/index.php/t-817122.html)

Looks like it should work for me too! I'll image all RAID 0 partitions before proceeding though.

I hope this thread may help someone like me :).


Thanks,

Bimal

---

### Post by darkod on 2009-12-14
> **goofy_goof said:**
> I have existing RAID 0 on which windows is installed. Now, I want to install UBUNTU 9.10 on a separate HDD and configure in such a way that GRUB is installed on the same HDD. I tried but looks like RAID 0 is recognized as MBR partition and GRUB cannot be configured on the same. I want the installer to recognize 2nd HDD as the primary HDD and configure GRUB on that one. I know there were some jumper settings on IDE but I have SATA HDDs. One way of doing this to disconnect RAID 0 HDDs and install UBUNTU. Once the installing is finished, connect those two HDDs back. But I am not sure if they'll be recognized as RAID 0 and I will not loose anything on that partition!

Can someone help??


Thanks,

Bimal

If you want grub2 on the same hdd as ubuntu, a different drive from the RAID0 array, what has the raid got to do with it? Just specify in Advanced options before clicking the Install button on the final screen, where to install grub2. Can't you do it that way?
It's a different question whether ubuntu will "see" your raid0 data, I don't know that.

---

### Post by goofy_goof on 2009-12-14
Oh well, I overlooked that option! Thanks for pointing that out. Installed and running on Ubuntu 9.10 and having fun, already!:guitar:

---

