---
title: "problem with installation"
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by natnats92 on 2011-06-11
i was using ubuntu 10.04 on my laptop with dual boot for around 6 months. being a newbie i experimented with something and managed to get myself locked out. not know what to do next i uninstalled wubi and tried to reinstall it. the installation completed successfully but on loading it got stuck before the login screen.

---

### Post by Rubi1200 on 2011-06-12
Hi and welcome to the forums :-)

Did you change any hardware between the time of the first install and the second install?

For example, new hard drive, new graphics card etc.?

Please post the full specifications for the computer, especially RAM and graphics card.

Thanks.

---

### Post by natnats92 on 2011-06-14
hey thanx for the quick reply! i haven't changed the hardware nor have i downloaded any driver updates. my specs are as follows:
Microsoft Windows XP Professional Version 2002 Service Pack 3
Intel(R) Core(TM)2 Duo CPU T6500 @ 2.10Ghz
2.10Ghz, 2.50 GB of RAM
NVIDIA GeForce 8200M G Graphics card
i tried installing ubuntu 11.04 yesterday. same thing! installation completes. then i reboot my system. i choose ubuntu. it starts loading. the dots appear and then disappear and the entire screen is now purple. i can't do anything but press the power button to shut down. HELP!

---

### Post by Rubi1200 on 2011-06-14
Hi,
you can try and set nomodeset as a boot option.

See here for more details:
[http://ubuntuforums.org/showpost.php?p=10089820&postcount=8](http://ubuntuforums.org/showpost.php?p=10089820&postcount=8)

---

### Post by natnats92 on 2011-06-15
thanx 'nomodeset' worked and it installed succesfully. but now the problem is that each time i want to use ubuntu i have to keep adding 'nomodeset' before 'quick splash'. otherwise it gets stuck at the ubuntu loading screen.

---

### Post by Rubi1200 on 2011-06-15
The first thing to check is whether you need to install the drivers for your card. Go to System Settings and Hardware Drivers. If it tells you there is something available then install it and that should solve the problem.

If not, then you can set nomodeset to be more permanent this way:

Open this file from the terminal:

```
gksu gedit /etc/default/grub
```

Find this line:

>  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Change it to this:

>  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

Save and close and then run this command to make it permanent:

```
sudo update-grub
```

Let me know how it works out please.

---

