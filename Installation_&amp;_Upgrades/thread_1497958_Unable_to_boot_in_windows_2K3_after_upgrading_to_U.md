---
title: "Unable to boot in windows 2K3 after upgrading to Ubuntu 10.4"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by OCS on 2010-05-31
Hi,

I am new to Ubuntu. 

I recently upgraded my Ubuntu from 9.10 to 10.4 (64bit) since then I am unable to dual boot to WIN2K3 from the same HDD as my Ubuntu. 

I have ran some of the suggestions like:

Sudo update grub and Testdisk 

both did not provide any errors on my partitions and my primary partition displayed in Testdisk was WIN2K3, now when I reboot and select it from the boot menu it just simply show a blinking cursor.

I am out of ideas and I need a solution to suit my configuration. I prefer not to re-install or repair any WIN2K3 OS....

Can someone assist and let me know what you need from me to further understand my issue.

Cheers,
OCS

---

### Post by darkod on 2010-05-31
Did you try this testdisk procedure:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You should in fact run the boot info script first and see if the results confirm that article. If yes, run that fix and it should be fine.

More details about running the boot info script:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by OCS on 2010-05-31
Hi, 

Thanks for helping me out. 

I have attached my results.txt file from running the boot info script and I can not make much sense from it. Apart that the grub is installed on the MBR (whole disk) but still sees WIN2K3 as the boot master OS. 

But this is not the case. 

Any ideas?

Cheers,
OCS

---

### Post by darkod on 2010-05-31
Yes, you have grub2 installed on /dev/sda1 and is getting into the way.

You need to perform the fix from the first link I posted on /dev/sda1, so that's partition #1 on disk /dev/sda.

---

### Post by OCS on 2010-05-31
Thank you for your help. 

I had to run the testdisk twice and rebooted it both times. Then ran a third reboot and seemed to work since then. 

I can now boot to my windows or ubuntu machine. 

I tried as the bottom part of the site suggesting to run sudo update-grub but I'm not sure what that command did because my booting in ubuntu still takes some time. So any idea on how I can make it to boot quicker?

Cheers,
OCS

---

