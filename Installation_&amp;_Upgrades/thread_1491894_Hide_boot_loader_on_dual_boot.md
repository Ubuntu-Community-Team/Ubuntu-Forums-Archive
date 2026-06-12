---
title: "Hide boot loader on dual boot"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by kafedzou on 2010-05-24
Hi, 

I recently switched from Windows Vista to Ubuntu 10.04. 
There were two partitions on my hard drive. The first one contains the Windows Vista installation files from the OEM. I kept these files since there was no CD included in when I purchased my laptop. In case I would ever want to sell my laptop and the new owner wants Windows on it, I would still have the installation files. 

So basically, I only formatted the second partition and installed Ubuntu on it. Everything works just fine there. 

Now, every time that I start up my laptop, I get this boot screen where I can choose between Windows loader or Ubuntu with some different kernels. 

What I want: 
When my computer boots, it should not show this boot manager/loader. I want it to boot Ubuntu right from the beginning without to wait until these nine seconds are over or until I press "enter". (Since Windows is not actually installed, it's just the recovery file, so I don't need the boot menu). If I ever need this boot menu I still want to be able to access it through a special key command or something similar. Otherwise I want it to immediately boot Ubuntu. 

Can someone help me to achieve this? 

Thanks.

---

### Post by darkod on 2010-05-24
The boot menu is your 'special key'. The recovery partition contains boot files and grub2 detects them like an OS.

You can temporarily remove it from the menu by disabling the os-prober file which looks for other OSs.

Do:

sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub

That should work. If later you want to put the recovery partition back in the grub2 menu, just execute the first command but change the -x in +x.

---

### Post by ajgreeny on 2010-05-24
Alternatively you can simply hide the grub menu and set the timeout to a lower figure of 1 or 2 seconds.  You will need to edit the file /etc/default/grub to do this, as follows:-
```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```
Change to:-
```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

---

### Post by kafedzou on 2010-05-24
> **darkod said:**
> The boot menu is your 'special key'. The recovery partition contains boot files and grub2 detects them like an OS.

You can temporarily remove it from the menu by disabling the os-prober file which looks for other OSs.

Do:

sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub

That should work. If later you want to put the recovery partition back in the grub2 menu, just execute the first command but change the -x in +x.

Hi, thanks both for your replies. 
I tried this option first and it does hide the Windows part. Only, the boot menu is still there and still gives me the following options: 

Ubuntu, Linux 2.6.32-22-generic
Ubuntu, Linux 2.6.32-22-generic (Recovery mode)
Ubuntu, Linux 2.6.32-21-generic
Ubuntu, Linux 2.6.32-21-generic (Recovery mode)
Memory test (memtest 86+)
Memory test (memtest 86+ serial console NUMBERS)


I also tried this solution, it's an improvement but It doesn't completely hide the menu for now. 

> **ajgreeny said:**
> Alternatively you can simply hide the grub menu  and set the timeout to a lower figure of 1 or 2 seconds.  You will need  to edit the file /etc/default/grub to do this, as follows:-
```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```Change to:-
```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

---

### Post by dino99 on 2010-05-24
Grub_timeout=0

open synaptic and right click on the kernel(s) you want to completly remove

then sudo update-grub

---

### Post by kansasnoob on 2010-05-24
I've tried it this way and it worked just fine:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:hide_menu:](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:hide_menu:)

---

### Post by ubeautu on 2010-06-22
Thanks. Grub seems to be in a different location in 10.04 than other versions of Ubuntu. This forum was the right one for me. After editing  /etc/default/grub and then doing 'sudo update-grub', the grub menu is now hidden.

---

