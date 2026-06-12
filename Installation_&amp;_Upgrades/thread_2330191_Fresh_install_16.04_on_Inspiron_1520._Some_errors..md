---
title: "Fresh install 16.04 on Inspiron 1520. Some errors."
date: 2016-07-09
forum: Installation &amp; Upgrades
---

### Post by vmittal on 2016-07-09
[FONT=arial]Gurus,[/FONT]
[FONT=arial]I am new to Linux and Ubuntu Both. Trying to switch from Windows.[/FONT]
[FONT=arial]Need your help.[/FONT]
[FONT=arial]I installed Ubuntu 16.04 on my old laptop Inspiron 1520 .[/FONT]
[FONT=arial]Startup takes long and laptop gets hot after some times. I noticed below errors in the system log. Can someone help me ?
[/FONT]
1) Jul 9 08:55:58 vipin-Inspiron-1520 gpu-manager[579]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf

2) Jul 9 08:56:00 vipin-Inspiron-1520 thermald[581]: I/O warning : failed to load external entity "/var/run/thermald/thermal-conf.xml"
Jul 9 08:56:00 vipin-Inspiron-1520 thermald[581]: error: could not parse file /var/run/thermald/thermal-conf.xml

3)Jul 9 08:55:58 vipin-Inspiron-1520 kernel: [ 13.560200] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro

4)Jul 9 08:55:58 vipin-Inspiron-1520 gpu-manager[579]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf

5) Jul 9 08:55:58 vipin-Inspiron-1520 systemd[1]: Started Detect the available GPUs and deal with any system changes.
Jul 9 08:55:58 vipin-Inspiron-1520 systemd[1]: Starting Light Display Manager

...[FONT=arial]thanks,[/FONT]
[FONT=arial]Vipin[/FONT]

---

### Post by mörgæs on 2016-07-09
Hi, welcome to the fora.

With a 1520 I recommend that you in stead do a fresh install of Lubuntu. Ubuntu might be too heavy for semi-old hardware.

---

### Post by Bucky Ball on 2016-07-09
Welcome. Yea, something lighter will be a better experience. I'd go for Xubuntu first and failing that, Lubuntu, as suggested previously, as that's lighter again.

I find Xubuntu a better fit, you might like Lubuntu. They are similar but definitely not the same. Xubuntu is very easily customisable. You can 'Try' either from the installation media and see which rolls best for you. Good luck.

(PS: Presuming you have the [standard hardware configuration as described here]("https://www.google.com.au/search?client=ubuntu&channel=fs&q=Inspiron+1520+specs&ie=utf-8&oe=utf-8&gfe_rd=cr&ei=i7WAV_W1H7HM8gerv4H4Cw")?)

(PPS: Just a tip. When posting terminal output, use code tags. Copy the terminal output and paste it directly into a post then add code tags whichever way you want (see the green link in my signature for how). 

This will keep all terminal formatting and make it easier to read and something helpers are more accustomed to seeing, something like the example below. Cheers. :))

```
Jul 9 08:55:58 vipin-Inspiron-1520 gpu-manager[579]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf
Jul 9 08:56:00 vipin-Inspiron-1520 thermald[581]: I/O warning : failed to load external entity "/var/run/thermald/thermal-conf.xml"
Jul 9 08:56:00 vipin-Inspiron-1520 thermald[581]: error: could not parse file /var/run/thermald/thermal-conf.xml
Jul 9 08:55:58 vipin-Inspiron-1520 kernel: [ 13.560200] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Jul 9 08:55:58 vipin-Inspiron-1520 gpu-manager[579]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf
Jul 9 08:55:58 vipin-Inspiron-1520 systemd[1]: Started Detect the available GPUs and deal with any system changes.
Jul 9 08:55:58 vipin-Inspiron-1520 systemd[1]: Starting Light Display Manager
```

---

### Post by vmittal on 2016-07-09
Thanks for you quick response Bucky Ball and Morgaes.

Actually , I did a fresh install of  Ubuntu on my Inspiron 1520. It has Intel core 2 duo processor and 4 gb ddr2 ram.  Most of the things are working fine . I am really impressed with Ubuntu.

Only problem is that It takes long in booting and back side of the lapotop gets hot.  The errors which I have sent are pointing toward that but I don't know, how to fix those. Can you please check those errors messages and let me know to fix those ?

---

### Post by mörgæs on 2016-07-10
> **vmittal said:**
> I did a fresh install of  Ubuntu

Yes, so we recommended X/Lubuntu, not Ubuntu.

---

### Post by vmittal on 2016-07-10
I will install that for sure.  Since I struggled so much to install it and I have a fully functional Ubuntu,  please help me for heating issue.  Can you please looking into thermal related errors only?  Thanks Vipin

---

### Post by vmittal on 2016-07-10
i think the heating issues are happening because of this 

   Jul 11 06:30:26 vipin-Inspiron-1520 systemd[1]: Started Accounts Service.
Jul 11 06:30:26 vipin-Inspiron-1520 thermald[592]: I/O warning : failed to load external entity "/var/run/thermald/thermal-conf.xml"
Jul 11 06:30:26 vipin-Inspiron-1520 thermald[592]: error: could not parse file /var/run/thermald/thermal-conf.xml
Jul 11 06:30:26 vipin-Inspiron-1520 thermald[592]: Unsupported cpu model, use thermal-conf.xml file or run with --ignore-cpuid-check
Jul 11 06:30:26 vipin-Inspiron-1520 thermald[592]: THD engine start failed

---

### Post by gordintoronto on 2016-07-11
Your 1520 probably needs a good cleaning to keep it cool.

You might install lm-sensors (in Xubuntu!), then run sensors-detect

If it suggests adding a module, say yes. (the default is no.) After rebooting, you can get temperature information by running sensors

My office has several 1520s which are still in use.

---

