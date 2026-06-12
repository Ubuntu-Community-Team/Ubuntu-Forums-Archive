---
title: "Partitioning HD for dual boot."
date: 2013-08-24
forum: Installation &amp; Upgrades
---

### Post by sysone on 2013-08-24
My AsusQ200E with Win 8 has 6 partitions. I need to  install Ubuntu and plan on shrinking sda4 and deleting sda5. On the new empty space I intend to reserve 4GB for swap  and  install Ubuntu on of the new partition.  
 
Here is a pic of the Screen: 

   [http://o31i.img-up.net/AsusQ200E893e.jpg](http://o31i.img-up.net/AsusQ200E893e.jpg) 

    What is on /dev/sda1 ?  

 And what is installed on /dev/sda5 ? Can it be deleted safely?

Thanks

---

### Post by oldfred on 2013-08-24
Windows requires a lot of partitions. Best not to delete any. It looks like your system was just configured with a NTFS data partition which is good to have.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

