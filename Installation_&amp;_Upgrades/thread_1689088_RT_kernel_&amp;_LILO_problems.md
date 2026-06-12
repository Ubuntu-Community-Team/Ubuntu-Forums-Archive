---
title: "RT kernel &amp; LILO problems"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by khelgar on 2011-02-16
Hello

I wanted to give Ubuntu Studio a try, for music production purpose, as a musician and composer-writer. So I started with a Ubuntu 10.10 generic install then processed with the installation of Ubuntu Studio packages, including RT kernel at last.
Everything ran smoothly until I installed this RT kernel...The problem appears to be LILO and its config, as well as fstab. I fear all of this is far above my abilities, this is why I submit my problem to the community.

Here's what I've discovered when trying to configure LILO :
$ sudo liloconfig

Fichier de configuration incompatible                                     &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Le fichier de configuration /etc/fstab (« fstab ») n'indique pas que      &#9474; 
 &#9474; UUID=2f245c2a-67ae-4f2f-abc4-fc81bb0a9884 est le système de fichiers      &#9474; 
 &#9474; principal. Celui-ci ne semble pas être un périphérique de type bloc       &#9474; 
 &#9474; « ordinaire ». Soit le fichier de configuration « fstab » est corrompu,   &#9474; 
 &#9474; soit vous utilisez du matériel tel qu'un ensemble RAID, ce qui n'est pas  &#9474; 
 &#9474; géré par ce simple programme de configuration.                            &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Vous devriez soit corriger la situation, soit écrire votre propre         &#9474; 
 &#9474; fichier de configuration /etc/lilo.conf ; vous pouvez alors relancer      &#9474; 
 &#9474; /usr/sbin/liloconfig pour essayer le processus de configuration à         &#9474; 
 &#9474; nouveau. La documentation de LILO se trouve dans /usr/share/doc/lilo/.

English : configfile fstab found wrong UUID as primary filesystem. Whether fstab config is corrupted or using RAID devices. To recover, write your own /etc/lilo.conf then run liloconfig again.

I really don't know where to find the correct UUID and devicepath for the RT kernel. I just know that I installed the generic kernel under sdb1, alongside my win7 install.

When I try to boot under RT kernel, I get a kernel panic and complete freeze, with lots of errors such as "boot device not found or wrong boot device specified", while the boot process shows "Kernel alive" at the bottom of the screen.

Can someone please help me correctly configure my new RT kernel install, in a manner I can easily understand as I'm not very aware of command lines?

Thanks


Install info :
Ubuntu 10.10 with Ubuntu Studio basic packages
RT kernel 2.6.24-28.81

---

### Post by grahammechanical on 2011-02-16
Are you able to boot into another kernel or into a recovery kernel? I did not know that Ubuntu Studio used LiLo? If Grub was your boot loader I would say run sudo update-grub or sudo update-grub2. You need to tell Lilo where the Rt kernel is. How you do that in LiLo I do not know.

Look in Places>Home Folder>File System>boot. That is where the kernels are stored.

Regards.

---

