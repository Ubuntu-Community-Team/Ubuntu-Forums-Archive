---
title: "Ubuntu upgrade failed, want to restore other operating system"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by pcambodia on 2010-02-04
Hello.
 
On my laptop I dual boot Ubuntu 8.04 and Windows XP. During the last upgrade of my Ubuntu distro something went wrong and now I get a messed up GUI. In the meanwhile I got a new laptop on which I only run Ubuntu 9.10. So my question is: I want to delete the linux partition on my old laptop and use only Windows XP but since I use grub to dual boot, I'm afraid that deleting the linux partition and extending the Windows partition will cause problems to boot my computer.
 
Here's a screenshot of my partitions:
 
[IMG]http://www.pceulen.be/partition.jpg[/IMG]
 
Any help would be much appreciated.
 
Thank you!

---

### Post by yogesh.girikumar on 2010-02-04
Hi,


     You might be able to fix your windows master boot record after you remove the linux partition in case you run into any trouble.[INDENT]      > For this you will need your Windows XP installation CD. Boot into it now.
       You will get to a part where it asks if you want to repair or recover. To do so, press "r".
    If prompted, enter your Windows XP administrator password. This will leave you at at a command line, so type in the following two commands:
```
fixboot
``` ```
fixmbr
``` Then type ```
exit
```     then remove your XP cd. If everything has gone well, you should come to your XP bootloader.[/INDENT]Here is some pretty solid help in this link from which I stole the above lines ;-) : [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

HTH

---

### Post by pcambodia on 2010-02-04
Much thanks! That should work. Making a backup of my data now and will try it later :)

---

