---
title: "how to configure dual boot to best effect with express cache"
date: 2013-04-08
forum: Installation &amp; Upgrades
---

### Post by geekyhawkes on 2013-04-08
Hello,

So I'm expecting to have my new laptop delivered and want to dual boot with windows7 as effectively as possible.  The details of the machine are here [http://www.overclockers.co.uk/showproduct.php?prodid=LT-127-SA]("http://www.overclockers.co.uk/showproduct.php?prodid=LT-127-SA")

I haven't used Linux on a machine with specs like this before,  do I need to be aware of any setup issues,  traps?  What is the best way to use the express cache ssd,  are they hardware managed or should I place the cache for xubuntu there? 

Any tips are welcome,  I am used to using Linux on an nvidea desktop PC that's a few years old, not exotic hardware at all.  

Andy

---

### Post by mikewhatever on 2013-04-08
> **geekyhawkes said:**
> Hello,

I haven't used Linux on a machine with specs like this before,  do I need to be aware of any setup issues,  traps?  What is the best way to use the express cache ssd,  are they hardware managed or should I place the cache for xubuntu there? 

Well, if it has dual graphics, Intel + AMD, you might have problems with that. The description leaves little doubt that the machine is designed for Windows, you'll need to run Ubuntu from DVD/USB to test what works, and what doesn't.
Not really sure what you mean by 'cache for xubuntu'. What's that? If, by any chance, you meant the swap partition, then no. In fact, with 8GB of RAM, there is no need for swap at all.

---

### Post by oldfred on 2013-04-08
That looks like it has Intel SRT? That cause issues. Is it still Windows 7 as that would avoid the issues of secure boot, but some of the last Windows 7 were still UEFI not the older BIOS boot.

 Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)
Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

      
  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

Brand not important as the implementation of Intel SRT is the Intel standard.

 Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by geekyhawkes on 2013-04-09
Thanks for the reply.  This is new tech for me to actually use, but it seems like I should be able to get it working.  I was thinking of putting swap on the ssd, but maybe I will just stick to installing Xubuntu on its own HDD partition and then use the SSD in windows as cache.  

If I have success or issues I will post back, might save someone else asking the same question in future I guess.  

Andy

---

