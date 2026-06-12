---
title: "NVIDIA driver will get me crazy !!!!!"
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by c_omran on 2011-02-10
I'm a windows user and installing Ubuntu 10.10 for the first time
my laptop is sony VPCCW21FX
using windows 7 64 bit
and using wubi to install Ubuntu 10.10 64 bit alongside with windows
 - i didn't see the installation process cause of the blank screen issue, so I did as you suggest here
 - Deleted quiet splash and typed nomodeset single, then startx
 - Then I downloaded the driver from Nvidia website which is 256.53.run
 - Then I restarted the machine and the same process as before, and then installed the driver with the next two lines
     sudo chmod +x NVIDIA-Linux-x86.......run
     then
     sudo ./NVIDIA-Linux-x86.........run
and kept pressing yes till I finished the installation
then typed startx
I saw the NVIDIA display then the ubuntu started but I didn't see the boot display
and inside the SYSTEM>ADMIN> menu there's no NVIDIA 
and I keep got the message about the restricted driver, and the nvidia driver is not activated, but I can see that the graphic performance has been changed  and I can set the visual effects to extra in appearence menu !!!!!!!
and if I choosed to log off, the screen became blank
and every time I shut down or restart I have to do the , nomodeset single and the startx command
can anyone help me

---

### Post by P4man on 2011-02-11
Hi, and welcome.

First a few general remarks; avoid wubi if you can. I mean it. Its a nice idea, and cool if it works, but more often than not, it doesnt work and causes problems.

A second remark; ubuntu is not windows. Dont go chasing drivers from websites, typically thats both unneeded, and a cause for trouble. For most things you dont need any drivers (they are part of the kernel), videocards are an exception, but to install the correct nvidia drivers, all you had to do was click that popup telling you there where restricted drivers for your card. It would fetch, install and configure the correct ones for you.

Now to fix your problem, Im afraid I have successfully avoided wubi for long enough that I dont know enough about it anymore. Heh. But in my signature there is a long explanation how to set nomodeset and make the change permanent for a regular (non wubi) install, and someone added a post with the changes needed for wubi. I havent tried that, but feel free to give that a try, although Id urge you to uninstall wubi, boot from the ubuntu cd using the nomodeset as explained in the link below and install that way.

---

### Post by c_omran on 2011-02-11
Hi P4man, and thanks alot for your reply, i'm gonna take your advice and install it without Wubi, I just wanna make sure about the partitioning thing before go ahead
I have five partitions all NTFS
One for win7 50 GB
Two for my data about 400 GB
One 20 GB to install linux on it 
One 10 GB to swap and etc files which I will format it and prepare it from inside Ubuntu with the live CD before installation 
so, is this right ???

---

### Post by grahammechanical on 2011-02-11
20GB is fine for Ubuntu. The partitioner will create a swap partition out of the 20GB partition unless you set the 10GB partition as swap. You do not need 10GB for swap, in my opinion. My swap is just over 3GB as set by the partitioner.

A home folder will also be created on the 20GB partition unless you set one of the 400GB partitions to mount as /home. Or, the 10GB partition. Having the Home folder on a separate partition is useful. It means you can re-install Ubuntu without losing your data. If you set one of the 400GB partitions as /home do not set the partitioner to format the partition. You will loose your data. Is it possible to transfer the data from one 400GB to the other as a backup? Protect your data.

Regards.

---

### Post by P4man on 2011-02-11
You can only have 4 primary partitions per disk (bios limitation); so you will need to create an extended partition in wich you can create more logical partitions for  ubuntu and ubuntu swap. I just helped this guy here with the same problem, have a look there:
[http://ubuntuforums.org/showthread.php?t=1685684](http://ubuntuforums.org/showthread.php?t=1685684)

---

### Post by realzippy on 2011-02-11
Since your laptop seems to be an Optimus laptop
(means hybrid graphics) there is no nvidia driver you can install unless you disable the Intel integrated graphics in your BIOS.
To confirm if it is an optimus laptop,open a terminal,type:

```
lspci | grep VGA
```

---

