---
title: "Ubuntu doesn't boot after installing updates"
date: 2012-01-17
forum: Installation &amp; Upgrades
---

### Post by jerm1027 on 2012-01-17
So I did a fresh installation of Ubuntu 11.10 64bit on my Acer Aspire AO-722, which runs AMD's C-60 Fusion APU with the HDD upgraded to a Crucial M4 64GB SSD. After enough nagging, I finally updated for the first time, which consisted of about 280MB of data being downloaded. After the updates were completed, I needed to restart the system, so I did, but it hangs at the Ubuntu logo when booting without any warning or error messages. I went on my lunch-break while it was restarting, so there is definitely something wrong. This exact thing happened when I was Xubuntu on the same laptop. I just erased the disk and installed Ubuntu, but I'd really like to spare my SSD unnecessary writes, as this will be about 6th time installing an operating system in less than a month.

I can still get into the recovery menu, and drop into a root shell, but when the system seems to freeze when I try to start X. I already checked the filesystem and checked for broken packages, but neither are a problem. Any help would be much appreciated.

---

### Post by Bucky Ball on 2012-01-17
Try the previous kernel. It should be in the selection in the grub list at startup.

Incidentally, Xubuntu *is* Ubuntu, just with a different desktop environment and apps. The base install is same. Prob why you're having the same problem. More about 11.10 than X K or U. Start looking there. Obviously the latest 11.10 kernel is giving you probs. ;)

---

### Post by jerm1027 on 2012-01-17
> **Bucky Ball said:**
> Try the previous kernel. It should be in the selection in the grub list at startup.

Incidentally, Xubuntu *is* Ubuntu, just with a different desktop environment and apps. The base install is same. Prob why you're having the same problem. More about 11.10 than X K or U.  ;)

Already tried that too. As of right now, the current option is:
Ubuntu, with Linux 3.0.0-14-generic

I went into Previous Linux Versions, which was
Ubuntu, with Linux 3.0.0-12-generic

That also freezes. Just a purple screen, no logo, warnings, or errors.

---

### Post by dnh500 on 2012-01-19
Having the same problem with a aspire 5542. Guessing it's something to do with backlight on the fglrx :confused:

---

### Post by jerm1027 on 2012-01-19
> **dnh500 said:**
> Having the same problem with a aspire 5542. Guessing it's something to do with backlight on the fglrx :confused:

Could be, especially since it doesn't support the APU's. I tried from the extra drivers, which I get that hardware not supported watermark, and then I just installed the one from AMD's site, but that just supports the C-50, and I have the C-60. Since I was using Unity2D, I might try to update using the open0-source driver, and see if I get the same problem. But I would like to see if there are other solutions before I nuke the OS and reinstall.

Any other suggestions?

---

### Post by jerm1027 on 2012-01-25
So, because of the lack of responses, I ended up nuking Ubuntu and re-installing. However, this time I did NOT install the proprietary fglrx driver and I disabled all but the most important updates. I just installed the important updates (still >100MB) and I have booted successfully. This means that it's either fglrx causing instability after updating, or a recommended update. I'm leaning more towards fglrx because it doesn't officially support the C-60, and when I first installed it via additional drivers, I had the unsupported hardware watermark. I don't want to confirm it though...

---

### Post by theopulus on 2012-01-25
I've had the same problem on my Dell Latitude E5510.

Tried installing both x86 and AMD64 versions. Everything goes ok until I update packages. From that point, system won't boot anymore.

Kernel 3.0.12 -> Installation default kernel. Boots ok
Kernel 3.0.15 -> No boot anymore. If I try former kernel it doesn't  boot...

---

### Post by jerm1027 on 2012-01-25
> **theopulus said:**
> I've had the same problem on my Dell Latitude E5510.

Tried installing both x86 and AMD64 versions. Everything goes ok until I update packages. From that point, system won't boot anymore.

Kernel 3.0.12 -> Installation default kernel. Boots ok
Kernel 3.0.15 -> No boot anymore. If I try former kernel it doesn't  boot...

Really? :confused: I thought that was just an issue with Acer, because the AO722 has a few hardware bugs. If that's the case, then that rules out the fglrx, and since I already installed the important ones with successful boots, that means it has to be a "recommended" update that's breaking Ubuntu. In all honesty, I'd either keep the updates on Important/security patches as those are tested, and skip the recommended. Or use a different distro entirely. I've been meaning to try out Arch. :D

---

