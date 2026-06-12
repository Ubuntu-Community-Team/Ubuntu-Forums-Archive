---
title: "Multi-boot"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by Kinildson Persegueiro on 2010-07-20
Hi  folks,  
  
     First I installed Win XP in /dev/sda5, Win Vista in /dev/sda6  and Win 7 in /dev/sda7. 
     Then I installed Linux Ubuntu 10.04 in /dev/sda1, mounting "/"  in /dev/sda1 and "/home" in /dev/sda9. 
  
     How can I make grub2 to recognize all the four operating  systems and use them?! 
  
     Thanks! [IMG]http://www.coderanch.com/images/smilies/jr-tongue.gif[/IMG]  
      
 im@mycomputer:/# fdisk -l 
  
   Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1   *           1        1275    10241406   8e  Linux LVM 
 /dev/sda2            1276       19457   146046884+   f  W95 Ext'd  (LBA) 
 /dev/sda5            1276        2550    10241406    7  HPFS/NTFS 
 /dev/sda6            2551        3825    10241406    7  HPFS/NTFS 
 /dev/sda7            3826        5100    10241406    7  HPFS/NTFS 
 /dev/sda8           19124       19457     2682823+  82  Linux swap /  Solaris 
 /dev/sda9            5101       19123   112639716   83  Linux 
  
 PS. tried many things until now, and no deal... 
 
                                                                                                                                                          [IMG]http://www.coderanch.com/templates/default/images/spacer.gif[/IMG]

---

### Post by oldfred on 2010-07-20
Windows will only boot thru a primary partition. If you installed all the windows in primary partitions then it would be possible.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

Linux does not care if it is installed in a primary or a logical partition. Windows is just about impossible to directly boot from a logical as it is not designed to do that.

---

### Post by Kinildson Persegueiro on 2010-07-22
Thanks for the info...
But I've given it up for now...
I'll check out virtual box from Oracle...

---

