---
title: "Kubuntu 8.04 KDE-4 Bootup Problem"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by truffsekka on 2008-04-09
I have installed Kubuntu 8.04 KDE-4 Beta and I am having a problem booting into it.  I am dual booting Vista and Kubuntu on a Raid-0 drive.  I have setup Grub correctly(I think) but I can boot into windows and start booting into Kubuntu without problems.  The problems comes after the boot starts, it hangs after this line...

```
ide: Assuming 33mhz system bus speed for PIO modes override with idebus=xx
```

System Specs
-----------------
CPU - Intel x3350 45nm quad core 2.66ghz
Motherboard - MSI P7N Platinum 750i
Ram - 2 x 2gb Gskill 1000mhz 
Video Card - 2 x Evga 9600gt Superclocked
Hard Drives - 2 x 500gb Seagate WD5000AAKS - Nvidia onboard Raid0(fakeraid)

Can anyone help me please... :(

Edit: After looking around the internet some more I found a way to make my resolution bigger while booting. This gave me some additional lines of information and I seen that the boot was spamming

```
Attempt to access beyond end of device.
```

So I am pretty sure it has something to do with dmraid and my setup.

---

### Post by dabl on 2008-04-09
Linux doesn't (in general) support hardware RAID setups, which is probably what you have, mainly because the RAID chip OEMs do not write Linux drivers.  In all likelihood you installed Kubuntu onto only one of your hard drives, and that's not gonna work with the IDE controller.

To learn more about RAID and Linux, useful search terms would be:

dmraid

mdadmin

Here's an older post on the topic: [http://www.nvnews.net/vbulletin/showthread.php?t=66344](http://www.nvnews.net/vbulletin/showthread.php?t=66344)

---

### Post by truffsekka on 2008-04-09
> **dabl said:**
> Linux doesn't (in general) support hardware RAID setups, which is probably what you have, mainly because the RAID chip OEMs do not write Linux drivers.  In all likelihood you installed Kubuntu onto only one of your hard drives, and that's not gonna work with the IDE controller.

To learn more about RAID and Linux, useful search terms would be:

dmraid

mdadmin

Here's an older post on the topic: [http://www.nvnews.net/vbulletin/showthread.php?t=66344](http://www.nvnews.net/vbulletin/showthread.php?t=66344)

I am pretty sure others have setup exactly what I am trying to do.  I actually found the guide on this forum.  This is the link: [http://ubuntuforums.org/showthread.php?t=464758](http://ubuntuforums.org/showthread.php?t=464758)

I did everything in the guide, so I don't know what could cause the error.

---

### Post by Neo0351 on 2008-04-09
this is kinda a stab in the dark, but are you running in sli?  if so, you will need to install with only one card, then install the drivers, and then you should be able to run in sli.

---

### Post by truffsekka on 2008-04-09
> **Neo0351 said:**
> this is kinda a stab in the dark, but are you running in sli?  if so, you will need to install with only one card, then install the drivers, and then you should be able to run in sli.

Okay, I'll try taking one card out. Do I need to reintall or just take it out and reboot?

---

### Post by Neo0351 on 2008-04-10
to tell you the truth i really dont know.  i dont have sli, all i know is you probably wont be able to boot as ubuntu doesnt support sli out of the box.  also, the faster card must be in the primary slot.  so if you are having problems with sli, you might try switching your cards.  sorry im not more help

---

