---
title: "[Karmic] dist-upgrade made system unusable"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by bellurashwin on 2010-02-23
Hi,

I ran sudo apt-get dist-upgrade, it has removed most of the important packages and files, my system is not bootable now. It gives 

Boot from (hd0,0) ext3 5c256729-4288-4e6e-9755-ebe92b514489
Error 15: File not found

Press any key to continue...


I am not even able to boot to recovery mode. 

Thanks,
Ashwin

---

### Post by RJARRRPCGP on 2010-02-23
Looks like GRUB is F-ed or it failed to copy the kernel! :-({|=

Must file a bug report, unless you're able to give further evidence of a hardware failure.

---

### Post by bellurashwin on 2010-02-23
is it possible to repair it without having to reinstall ubuntu.

---

### Post by darkod on 2010-02-23
Boot the live desktop and follow the instructions here and post your results content:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by recluce on 2010-02-23
I would just restore the system from a backup image. If you don't have one, please learn something from this - you will probably have to do a fresh install now.

---

### Post by bellurashwin on 2010-02-24
Attached results.txt. 





> **darkod said:**
> Boot the live desktop and follow the instructions here and post your results content:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by recluce on 2010-02-25
> **bellurashwin said:**
> Hi,

I ran sudo apt-get dist-upgrade, it has removed most of the important packages and files, my system is not bootable now. It gives 

Boot from (hd0,0) ext3 5c256729-4288-4e6e-9755-ebe92b514489
Error 15: File not found

Press any key to continue...


I am not even able to boot to recovery mode. 



According to the results.txt you posted, the uuid of /dev/sda1 that is in grub's menu.lst, is 5c256729-4288-4e6e-9755-2be92b514483. This is different from the UUID from your error message above. While I cannot understand how the UUID could change without reformatting the partition, GRUB trying to a non-existing partition would certainly cause an error 15.

Boot from the live CD, open a shell and type "blkid -L". This should give you all connected drives, mounted or not, and their UUIDs. Verify if the UUID for /dev/sda1 is indeed identical to the one in menu.lst. If not, edit menu.lst to replace all occurences of the (obsolete) UUID of sda1 with the correct one. If not, we will have to look further. Before you edit menu.lst, copy it to menu.bak or something similar, just in case you want to revert to the original version of the file!

---

### Post by darkod on 2010-02-25
As a first step I would try reinstalling grub1 on the MBR of your hdd. Boot with a 9.04 cd (not 9.10 because it has grub2 on it), and in terminal do:

sudo grub
root (hd0,0)
setup (hd0)
quit

Reboot without the cd and see if it helped. I'm not experienced in grub1 commands (I learned the new grub2 faster) but i think the above commands should reinstall your grub1 on the MBR.

---

