---
title: "Version 9.10 on old Sony Vaio Laptop"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by mac-christian on 2010-02-03
Hi all

I tried to installed Ubuntu 9.10 on an older Sony Vaio laptop (model PCG-XG9) with 20 GB HD and 128 or 256 MB RAM (not sure). There is no ethernet port, but I have a PCMCIA WLAN card "Cabetron RoamAbout 11 Mbit/s, which should work perfectly with any Linux. 

The computer had Win98 on it originally (which, of course, after all installation attempts is now destroyed). The problem is that I cannot install to the end at all - no matter what I try:

1) Having the disk as a single FAT partition (made by a Win98 installation CD), it appears that Ubuntu cannot create the correct partitions needed for Linux. 

2) Having deleted the DOS partition with FDISK from Windows98 - which is like buying a completely new, unformatted HD from a store - the installer just stops and does not do anything.

Is there a manual / instruction page somewhere how I should partition the disk manually (how to do it, and what sizes are recommended for each partition)? I do _not_ want to have any Windows partition left, if not absolutely necessary.

This would be great. Thank you, Christian

---

### Post by audiomick on 2010-02-03
I think your problem is not enough RAM
> 
                [SIZE=2]A Pentium 4, 1GHz system is the minimum recommended for a desktop system.  [/SIZE]
                                                                    [SIZE=2]**Table 3.2. Recommended Minimum System Requirements**[/SIZE]                 
                                                                                                                                                                                                                                               [SIZE=2]Install Type[/SIZE]                         [SIZE=2]RAM (minimal)[/SIZE]                         [SIZE=2]RAM (recommended)[/SIZE]                         [SIZE=2]Hard Drive[/SIZE]                                                                                                                 [SIZE=2]No desktop[/SIZE]                         [SIZE=2]64 megabytes[/SIZE]                         [SIZE=2]256 megabytes[/SIZE]                         [SIZE=2]1 gigabyte[/SIZE]                                                                       [SIZE=2]With Desktop[/SIZE]                         [SIZE=2]64 megabytes[/SIZE]                         [SIZE=2]512 megabytes[/SIZE]                         [SIZE=2]5 gigabytes[/SIZE]                                                                                
               
               

from here
[https://help.ubuntu.com/9.10/installation-guide/i386/minimum-hardware-reqts.html](https://help.ubuntu.com/9.10/installation-guide/i386/minimum-hardware-reqts.html)

I am not really up on which variations are really lightweight systems, but you could look at xubuntu.
[http://www.ubuntu.com/products/whatisubuntu/xubuntu](http://www.ubuntu.com/products/whatisubuntu/xubuntu)

---

### Post by mac-christian on 2010-02-04
Thank you, Michael. I'll try to see whether I find some more RAM in the attic, or give Xubuntu a try. 

Christian

---

