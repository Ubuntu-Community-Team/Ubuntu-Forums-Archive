---
title: "Grub Error 2"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by Ozonecy on 2008-02-04
Hello all.
i hope this will be small and easy to fix problem.
After some months of having Fedora 8 i decided today to install Ubuntu. 
I think the error is on MBR or reading my raid configuration.
Before i enter ubuntu setup my fedora system has disk raid 1.2 hd of 80gb was join and make 160. ( i dont remember the function if this job do  1 or 2 raid)
i installed ubundu without any problem. the only option that makes me to think is the time when the setup asked me to create or use entire disk space on HD. it let me to choose from 2 different partitions. but i choose the first one and auto create!
the installation finished but when GRUB tries to boot failed.
the error message is:

Grub Loading Stage 1.5
Grub loading please wait
Error 2

i think my raid is software raid and not hardware. i have Fujitsu SIemens amilo 3438. 
in my opinion the problem is on raid and not MBR problem because i eneter windows xp setup to format all drivers and i recreate MBR using the recovery console !
and then i tried to install Ubundu but same problem.
note : on windows xp setup i saw my hard disks like Raw1
                                                                            Raw 2
                                                                              Raw 4
                                                                                  Raw 5
i also read this help page to found closer my problem:
[http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)

any suggestions?
thanks!

---

### Post by Pumalite on 2008-02-04
Quoted from the GNU/GRUB manual

    2 : Bad file or directory type
        This error is returned if a file requested is not a regular file, but something like a symbolic link, directory, or FIFO. 

(from Super Grub)
Did you use this?:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

