---
title: "Thinking of upgrading to Lucid? How old is your hardware?"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by ub-pir on 2010-08-30
I've recently tried to upgrade from Karmic to Lucid and it went disastrously wrong - I am now happliy back with Karmic. Thinking about this, I tried to upgrade a laptop some while back and that too went very wrong - back to Karmic. On the positive side, I have upgraded on my work PC without problem and fresh-installed Lucid on the laptops of my two kids, again no probs.

The linking factor seems to be the age of the hardware: My bad experiences were both with older machines, although the desktop was only 5-6 years old. I also have a work colleague who tried to install Lucid on an "old PC" and that went wrong. As for the positives, my work PC is pretty new and my kids' laptops both less than 1 year old. Now I know this is anecdotal evidence but I am wondering if the changes to Lucid (to make it boot faster?) have removed support for older hardware (as a side-effect)? Quite a few of the posts on this site reporting weird install problems seem to be concerned with older h/w.

If so, this is a shame since the Linux community always boasted that, unlike resource-hungry versions of Windows, Linux would install quite happily on a four-slot toaster...

Summary:

1) Based on my (jaundiced) experience, I would suggest thinking very hard before trying to install/upgrade to Lucid on older h/w. (How old - I don't know.)

2) It would be interesting if people posting weird install problems on this site could state how old their h/w is. Maybe the community could get to know what will work and what will cause grief.

---

### Post by lechien73 on 2010-08-30
I think it probably depends on the manufacturer/model/popularity of the individual components, rather than the age of the hardware itself. 

For example, my 2 year old Dell Studio laptop had no installation problems at all but my wife's 1 year old netbook had (surmountable) WiFi issues with Lucid. I had to revert to Karmic on a 3 year old Compaq Presario laptop, but when the hardware on one of my VMWare host servers crashed on Thursday last week, the only replacement machine I had was a 7 year old Dell Celeron PC. Ubuntu 10.04 Server installed flawlessly and the I was quickly back up and running.

I have also found that Ubuntu usually addresses the hardware "properly", as opposed to Windows. A case in point is the 3Com 3C905 network card. Windows overrides the settings in the card's firmware itself. 3Com knows this, and so the firmware settings are often set to nonsense values. Because Ubuntu addresses the card properly - and sets its values according to the firmware, rather than the other way round - you often have issues getting 3C905 cards to work properly under newer versions of Ubuntu. (unless you set the firmware first with the DOS utility).

What this taught me is that, we often blame the operating system if there seems to be a hardware conflict, but manufacturers are so used to Microsoft arbitrarily deciding how Windows will address a particular piece of hardware, that they often just leave Windows to it. In which case, although the Linux driver is correctly written, *it* (rather than Windows) appears to have problems.

Just my 2-cents :)

---

### Post by Mark Phelps on 2010-08-31
No one is going to be able to say for certain how well any distro is going to work on any specific machine.  All  we can do is point out the required hardware minimums.

One of the primary purposes of having a LiveCD mode is to try out just what you want -- to run the latest version on a specific set of hardware to see how well it works.

---

### Post by ub-pir on 2010-09-01
> **Mark Phelps said:**
> One of the primary purposes of having a LiveCD mode is to try out just what you want -- to run the latest version on a specific set of hardware to see how well it works.

Except I can state absolutely unequivocally that the LiveCD version worked perfectly on my desktop but Lucid failed during install - it could not see the HDD which seems a common fault with Lucid installs, judging from this mailing list. The LiveCD does not touch the HDD...

Since my original post, I have noticed an ubuntuforurms list for Hardware (above this list) where people can post details of h/w that gave problems. It would be nice to have a database of motherboards which for which users have reported problems. I can add Asus P4/PE to that list.

---

