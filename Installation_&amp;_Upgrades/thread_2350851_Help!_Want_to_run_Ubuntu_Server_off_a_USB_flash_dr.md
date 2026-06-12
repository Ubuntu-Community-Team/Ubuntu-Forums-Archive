---
title: "Help! Want to run Ubuntu Server off a USB flash drive in old laptop"
date: 2017-01-28
forum: Installation &amp; Upgrades
---

### Post by drewus on 2017-01-28
I have an old laptop (Core Solo CPU, 1GB Ram) that I have been running Ubuntu Server on, booting off a USB flash drive. It worked fine for about two years but now the USB flash drive died. I would like to get it running again in a way that will work better with a USB flash drive.
I have a fresh install of Server 16.04.1 installed with LVM support on an 8GB flash drive. I used UNetbootin to set up the flash drive with the ISO, then booted it up and installed Server.

What should I do to make it most compatible with the flash media?

I don't mind starting from scratch if it will make a better system but I don't want to buy more hardware.

Thanks

---

### Post by ian-weisser on 2017-01-28
Flash drives wear out with too many writes. Lengthen their life by minimizing the number of write cycles.
- LVM won't help a flash drive - that's a layer of unnecessary complexity.
- Don't use swap
- Mount /tmp and /var as tmpfs in RAM
- Don't host databases (including CMS websites) on a flash drive.
- Don't run a torrent server on a flash drive.

---

### Post by C.S.Cameron on 2017-01-29
Make and model of the flash drive is important.
I have several Kingston Data Travelers that have been running Linux for over ten years with no sign of wear.
Have a newer Kingston that died after a few months.
Have a Sandisk that died after a year but an identical one that has been working over three years.
Most trouble has been with Transcend drives, some have died within weeks.
Not sure the problem is too many writes, yanking a drive before it is ready does not seem to be a good idea, same with formatting a multi-partition drive in Windows.
Not sure what are currently the sturdiest drives for running Linux, there are a lot of choices out there.
If you Google, there are also lots of best flash drive reviews.

Most flash drives with wear leveling are good for 10000 writes, which can be a long time.

---

### Post by sudodus on 2017-01-30
I agree with the previous posts. I can add the following links,

[Installation/UEFI-and-BIOS#Final_system_tweaks](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#Final_system_tweaks)

[Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

-o-

Why are you using a USB drive instead of an internal HDD? Is the connection to the internal drive damaged, or is it because USB drives are cheaper?

---

