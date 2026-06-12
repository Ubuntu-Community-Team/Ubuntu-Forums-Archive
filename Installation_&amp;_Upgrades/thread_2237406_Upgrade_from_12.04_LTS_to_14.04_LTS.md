---
title: "Upgrade from 12.04 LTS to 14.04 LTS"
date: 2014-08-01
forum: Installation &amp; Upgrades
---

### Post by cetoka on 2014-08-01
Upgrade worked without any problems.Everything is working fine.But when I open the synaptic package manager I see ''linux image 3.2.0-67-generic''  in the installed(local or obsolete) menu.Is it safe to remove this?
Also in the residual tab I see oss-compat  I tried to completely remove it,it seems to remove but it comes back.How can I remove it?

---

### Post by kc1di on 2014-08-01
Hello cetoka and welcome to Ubuntu,

you can find which kernel is currently in use on your system with this command in a terminal ```
uname -r 
```

you have already removed oss-compat that entry says it's not installed but it's  available for install should you want it again for some reason.

you may also want to run these commands to clear the apt cashe  -- ```
sudo apt-get clean && sudo apt-get autoclean 
```

---

### Post by ajgreeny on 2014-08-01
Running the command ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
``` will show you all the kernels you have on your machine and ```
uname -a
``` will show you which kernel is now running.  You can then use synaptic to remove completely all except the two most recent kernels. You can then run ```
sudo apt-get autoremove
``` to get rid of the header packages of those removed kernels.

---

### Post by cetoka on 2014-08-04
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
-OptiPlex-390:~$ grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnu
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --cla
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux -
    menuentry 'Ubuntu, with Linux 3.2.0-67-generic' --class ubuntu --class gnu-linux --class gnu --clas
    menuentry 'Ubuntu, with Linux 3.2.0-67-generic (recovery mode)' --class ubuntu --class gnu-linux --
menuentry 'Memory test (memtest86+)' {
menuentry 'Memory test (memtest86+, serial console 115200)' {
OptiPlex-390:~$ 

So I  have only the newest kernel for Ubuntu 14.04.

uname -a
OptiPlex-390 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

---

