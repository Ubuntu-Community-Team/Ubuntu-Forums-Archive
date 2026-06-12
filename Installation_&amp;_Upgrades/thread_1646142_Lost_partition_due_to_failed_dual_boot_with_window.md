---
title: "Lost partition due to failed dual boot with windows7"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by tumelo on 2010-12-15
I am a linux noob. Only been using it for less than a year. I wanted to put windows7 on my computer and dual boot because I couldn't get webex to work with linux. So I booted windows from the CD and selected partition 2 to install it. Obviously dual booting is more complex because then all I had was windows and I lost all my files on my main parition that had ubuntu on it. I am sure that I did not write over my main partition. How do I get all my stuff back??

---

### Post by Rubi1200 on 2010-12-15
Hi and welcome to the forums :)

The first thing to do is stop any activity on the drive; i.e. no more read/write actions.

Next, boot the computer with a LiveCD and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here please.

Thanks.

---

### Post by tumelo on 2010-12-15
Boot Info Script 0.55    dated February 15th, 2010     
              

============================= Boot Info Summary:
==============================

 => Windows is installed in the MBR of /dev/sda

sda1:
_________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

=========================== Drive/Partition Info:
=============================

Drive: sda ___________________
_____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   476,327,249   476,327,187  83 Linux


blkid -c /dev/null:
____________________________________________________________

Device           UUID                                   TYPE       LABEL
                        

/dev/loop0                                              squashfs       
                         
/dev/sda1        B89673099672C800                       ntfs           
                         

============================ "mount | grep ^/dev  output:
===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)

---

### Post by Rubi1200 on 2010-12-15
Are you sure this is the full text from the results that were generated?

According to this, there is no Ubuntu, only Windows.

You can boot into Windows normally right?

You could take a look at the options here, but I doubt there is much chance for recovery:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by tumelo on 2010-12-15
I formatted the windows drive hoping it would reverse all the wrong it did and I would have my ubuntu back. 
 
When I loaded the linux live cd. under places > computer it showed a 244GB file system, which I thought was my main partition that I could no longer boot into and then another 6GB file system. That I understood to be the windows partition because windows kept saying I had low disc space. I only had about 10MB left on my C drive with windows. 
 
So I deleted the small filesystem hoping only my original would remain and everything would go back to normal. but as you know it didn't. 
 
That's why I was sure I didn't over right all my stuff and was hoping I could easily get it back.

---

### Post by kansasnoob on 2010-12-15
After that much manipulation I think the best you can hope for is using PhotoRec from an Ubuntu Live CD to save any recoverable data to some external source.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Rubi1200 specifically said, "The first thing to do is stop any activity on the drive; i.e. no more read/write actions."

AFAIK whatever PhotoRec can't recover is gone.

---

