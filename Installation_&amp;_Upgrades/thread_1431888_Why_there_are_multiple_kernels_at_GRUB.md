---
title: "Why there are multiple kernels at GRUB"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by siemprepeligroso on 2010-03-17
Dear Friends,
After I messed up badly with my netbook I have to reinstalll the OS, it is a government property netbook that came up with Edubuntu 7.04 insalled on it. I shouldn't mess with the filesystem but I did and now I have to install Edubuntu from the beginning, but I must be sure that everything will just like I have done no change, so I am afraid that I can make some mistakes at this point
The first thing that I want to know is: Why there are multiple kernels listed at the 
GRUB (v 1.5)...this is the full list:

[FONT=Fixedsys][SIZE=1]Ubuntu, kernel 2.6.28.9 Default
Ubuntu, kernel 2.6.28.9 Default (recovery mode)
Ubuntu, kernel 2.6.28.9 
Ubuntu, kernel 2.6.28.9 (recovery mode)
Ubuntu, kernel 2.6.20-15-generic
Ubuntu, kernel 2.6.20-15-generic (recovery mode)
Ubuntu, kernel 2.6.20-15-generic
Ubuntu, kernel 2.6.20-15-generic (recovery mode)
Ubuntu, memtest86+[/SIZE][/FONT]

[FONT=Verdana]Now I wonder how can I get this also after I reinstall the OS, plus this time I will try to make dual boot with xp installed first[/FONT].

Thanks in Advance :)


PS: Also when I access the HDD from livecd Ubuntu 9.10 the partitions listed are:

/dev/sda1                                 ext3 [File System]                                  146.19 GiB [size]                                        6.42 GiB [used]                             boot [Flags]
/dev/sda2                                  extended                                                             2.86 Gib                                                              ----                                                               -----

(under /dev/sda2  afer expanding appears: )
     /dev/sda2                linux swap                            2.86 Gib                         ----                                    -----


waht about this LINUX SWAP

---

### Post by Kakers on 2010-03-17
The Kernels listed at boot are your current Kernel and previous ones which you have upgraded from if you wish to backtrack or restore a previous kernel, if you install the same version you should get the same screen (Versions such as Ubuntu 9.10 the Kernels are not displayed unless you push "Esc" at boot when prompted)

As for your question about SWAP, this is Virtual memory on your HDD set up as a separate partition, you can find more information here: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

The above link will also include recommended sizes for your system but the default option on installation should be sufficient.

---

### Post by oldos2er on 2010-03-17
7.04 hasn't been supported for a long time, so you might want to consider upgrading to 9.10.

---

### Post by siemprepeligroso on 2010-03-19
Thanks for your help, both of you :)

---

