---
title: "Fresh install gone crazy"
date: 2021-05-06
forum: Installation &amp; Upgrades
---

### Post by davidpcoleman on 2021-05-06
I am trying to install Ubuntu 20 on a Emachines computer that has Windows 7 on it. I booted up and clicked on install and delete Windows 7. After it installed, it said to reboot, so I did and thats when it went crazy. Now the screen flickers and it gives a line like this;

Checking  ./pool/main/g/gcc-9/libgcc-9=dev_9,3,0-17ubuntu

and a few others that are similar. And it just repeats it over and over again. I have had it running for about 15 minutes and no change.

Intel eleron 900
Intel GMA 4500M
2 Gigs DDR3 Memory
250gig Hard drive


It appears that the lines do indeed move up with a new line written on the bottom. Last line right now is
.pool/main/n/nvidia-prime_0.8.15.3~0.20.04.1.all.deb: ok

Any thoughts or should I just re-install and consider it a corrupted install?

---

### Post by ubfan1 on 2021-05-07
Did you remove the install media before rebooting?  Looks like the checking being done is of the install media.

---

### Post by davidpcoleman on 2021-05-07
Yes I removed it. I did a complete shutdown on the computer and restarted it. Same thing. Just a bunch of the same code repeating over and over. But Ubuntu will finally load and seems to run fine. Just something weird in the bootup. thinking about going in thru the usb and re-formatting the hard drive to where it is fully blank and starting over. BTW, this was the first time I installed Linux off USB. My other computer has Mint on it off a DVD and runs fine.

---

### Post by ubfan1 on 2021-05-07
Are you using the zfs filesystem, or raid -- something that might have a .../pool to check?  I always use ext4, so don't know anything about those.

---

### Post by tea for one on 2021-05-07
How old is the PC?

2GB RAM for Ubuntu with Gnome is probably not quite enough - hence the slow boot time.

You may want to try another version of the Ubuntu family such as Xubuntu or Lubuntu.

Here's some info [https://ubuntuforums.org/showthread.php?t=2415676](https://ubuntuforums.org/showthread.php?t=2415676)

---

### Post by davidpcoleman on 2021-05-07
Ubfan1 - I don't know anything about the [COLOR=#000000]zfs filesystem, or raid. I switched to Linux as I was very frustrated with the whole WIndows Microsoft family. I have used Linux Mint for years wilh almost no problems.

tea for one - the pc is a little old and you may be correct. That laptop has always seemed slow even with Windows 7 on it. It is running fine, it updated and installed some software for me. It's just the bootup that is crazy. If I have to reboot, I walk away from it for about 15 minutes and it is sitting there waiting for me. But I think you may be on to something. Probably my best bet would be to do what I had said before and used a boot disk and reformat the whole hard drive and just settle for Mint. Ubuntu had more features, but I think the age and, more so, the ram may be the problem. It is a backup laptop and I should have probably put Ubuntu on this laptop as it has 8 megs or ram. Maybe at a later date.    Think I will just mark this thread as solved. I think if I put together what you 2 said, I think I have the problem figured out.

Thanks for the help..[/COLOR]

---

