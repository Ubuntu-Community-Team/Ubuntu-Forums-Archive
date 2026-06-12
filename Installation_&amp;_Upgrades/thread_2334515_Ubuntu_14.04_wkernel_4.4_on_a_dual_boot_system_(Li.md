---
title: "Ubuntu 14.04 w/kernel 4.4 on a dual boot system (Linux/W10)"
date: 2016-08-20
forum: Installation &amp; Upgrades
---

### Post by Grigoriy on 2016-08-20
Hello!
                          Yesterday I got the system warning from the  Updater that there's an important security update, and I OKed it and  post factum I realized that it was actually an automated kernel upgrade.  I also keep on getting messages from the system that I can upgrade to  16.04, but I choose not to for now and one of the main reason is that  I'm afraid that PHP7 (which is the default for 16.04) won't do any good  to my Joomla script that is hosted on a LAMP stack. Not the Joomla  itself, which is compatible with PHP7, but what comes with it together. I  checked and I'm still on 14.04, PHP 5.5 which is good. Now there are my  couple of questions, regarding the situation:
                          1) What's the advantages of running 14.04 specifically on a new kernel version?
                          2) Do I have systemd? I think I don't, but I'm  not sure. But what I did notice is that now I don't have this boot  issue that kinda corrected itself after the kernel upgrade. I mean, I  used to have this annoying problem of system not booting properly the  first time I turn on the PC. Only after the reboot, I used to get to the  Ubuntu login screen. The first time the system used to be dropped into a  BusyBox shell environment. So could there be a direct connection  between boot process and the new kernel? Does a kernel upgrade can  really change it? So far it looks like it, though I've only been booting  the system a couple of time, so it might be too early to tell.

---

### Post by kansasnoob on 2016-08-20
>  I also keep on getting messages from the system that I can upgrade to 16.04

You can safely disable that in Software & Updates. Under the Updates tab at the very bottom where it says Notify me of a new Ubuntu version just change that to Never:

[ATTACH=CONFIG]270761[/ATTACH]

You will still receive an EOL warning in April 2019 when 14.04 (Trusty) stops receiving updates.

> What's the advantages of running 14.04 specifically on a new kernel version?

None that I'm aware of compared to the original Trusty kernel and X-stack, but the purpose of LTS HWE is to enable support for newer hardware. 

Those who installed Trusty using the 14.04.2, 14.04.3, and 14.04.4 images got the lts-utopic, lts-vivid. or lts-wily HWE stacks respectively which all reached HWE-EOL this month:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support)

[https://wiki.ubuntu.com/1404_HWE_EOL](https://wiki.ubuntu.com/1404_HWE_EOL)

I prefer always using the first point release images (eg; 14.04.1 & 16.04.1) so I can avoid HWE-EOL altogether, so you may want to keep that in mind when you're installing Ubuntu in the future. It hasn't happened to me often but sometimes a new kernel will drop support for older hardware in the process of enabling support for newer hardware so I much prefer to stay on the original kernel series and just get security updates for that kernel series throughout the lifespan of a release.

> Do I have systemd?

No, systemd (in it's entirety) was not introduced until 15.04:

[https://wiki.ubuntu.com/SystemdForUpstartUsers](https://wiki.ubuntu.com/SystemdForUpstartUsers)

> So could there be a direct connection between boot process and the new kernel?

Yes. I have one PC in home that fails to reboot properly with the 3.13 series kernel. Cold boot is fine but it hangs on reboot. Such errors are not at all uncommon.

---

### Post by Grigoriy on 2016-08-20
I see. OK, thanks!

---

