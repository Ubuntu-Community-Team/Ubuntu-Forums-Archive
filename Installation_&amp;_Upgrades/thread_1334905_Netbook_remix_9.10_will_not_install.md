---
title: "Netbook remix 9.10 will not install"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by FailureToLoad on 2009-11-22
Hello folks, having some frustrating errors here I'm trying to diagnose. I had the netbook remix installed successfully on a small partition and was loving it. I tried to install it on the entire drive and the partitioner hung, gave me an error saying parted_server closed expectantly. So I did a force shut down and tried all over again... still stalling. 

I'll note here I'm using an acer aspire one with the 8gb SSD. I know, not exactly the best thing around.

So, I went out and deleted all the partitions using gparted. I'm thinking right around here is bone headed move #1. Now I can get to the install phase but I recieve and error saying "I/O error when writing to /sda1". Any ideas on things I can try? I'm not looking for a miracle cure (though I certainly won't refuse one!) but any suggestions or resources would be greatly appreciated.

---

### Post by articfox on 2009-12-16
I am having the same exact problem.  I have an Acer Aspire One.  An installation of Ubuntu Remix hung during installation.  Now every time I attempt to install, parted_server crashes.  Any ideas anyone?

---

### Post by darkod on 2009-12-16
Since you already wiped the drive, I guess it doesn't hurt using TestDisk. Haven't used it myself but basically it repairs the disk especially the partition table if it has any errors. And they are likely if the forced shutdown was during creating partitions last time.
Google will take you to TestDisk.

---

