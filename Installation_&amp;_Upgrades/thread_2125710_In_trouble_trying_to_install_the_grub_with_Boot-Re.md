---
title: "In trouble trying to install the grub with Boot-Repair"
date: 2013-03-14
forum: Installation &amp; Upgrades
---

### Post by fizaurie on 2013-03-14
Hi!!!

I'm in trouble with a Lenovo IdeaPad S10-3 from my sister, I don't know why the ubuntu installer is unable to install the grub ('Executing grub-install failed. This is a fatal error.')...

I did use the Boot-Repair with the "Recommended Repair" and finally it said there was an error :( The URL was [http://paste.ubuntu.com/5615125/](http://paste.ubuntu.com/5615125/)

Thank you very much in advance for your help!!!

F

---

### Post by oldfred on 2013-03-14
Is this an UltraBook with Intel SRT. 
You have to remove the RAID meta-data from both drives.
Some have just installed / (root) to the small SSD and used rotating drive for /home or data.

       Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

From other installs:

 > Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.
     
[URL="http://ubuntuforums.org/showthread.php?t=2071242"]
[/URL]
 Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)

[       ]("http://ubuntuforums.org/showthread.php?t=2071242")
 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

---

