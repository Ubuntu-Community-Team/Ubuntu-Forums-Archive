---
title: "Multip GPU - ATI HD 3600 - Mouse and keyboard freeze"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by ask@refcapgroup.com on 2010-04-30
**Help Multi GPU - Mouse and Keyboard Freeze once enabled**             
                                                                Previously on  Ubuntu Karmic I had multi GPU setup without a problem.
System consists of three ATI radeon HD 3600 series (multi head) running 6  monitors.

Setting it up was was easy as on Microsoft windows. All I did was download the ati  catalyst and issue the following command: [B]
aticonfig --initial=dual-head --adapter=all[/B]

That created the perfect xorg.conf. With the amdcccle desktop, I then  rearranged the monitors around to my setup and enabled xinerama. I thus  had a total of six monitors working without a problem. (Naturally with  compiz turned off).

**- UPGRADING TO LUCID BIGGEST MISTAKE -**

Yesterday the update manager popped up Lucid  Ubuntu 10.04 Release available. I upgraded. I got the same issue of  fglrx.. Reading through Forum I deleted the /usr/share/ati folder.  uninstalled the catalyst. Rebooted in safe mode and then re-installed  via synatic fglrx and amdcccle. All went well.

I then issued the basic command.

**aticonfig --initial -f  **

This created the standard xorg.conf. On rebooting machine. My first two  screens (off the first Radeon HD 3600) worked fine, without a problem. (See attached file)

I then issued
**aticonfig --initial=dual-head --adapter=all.**
This created the long xorg.conf file for all the cards on the system to work.

**BUMPER !! **Machine reboots and right before the X login screen appears all of a  sudden my monitor screen goes into "Digital Power saving mode" and the monitor goes to  sleep. Keyboard and Mouse are not responsive (All freeze). No alternative but to cold boot the machine and restart.

I have tried everything, each time mouse and keyboard just freeze. 

ANY HELP, ANY ONE, ANY IDEA.

---

### Post by jamesbrown on 2010-05-01
I'm experiencing the same problem as well, just installed fresh 10.04 64 bit.
Attempting to activate second Radeon 4670 results in no display whatsoever and requires a replacement of xorg.conf to get working again.

Rebooting with the dualhead xorg.conf simply freezes on the Ubuntu startup progress window, there is no indication of errors in /var/log/Xorg.log

---

### Post by quadproc on 2010-05-01
> **ask@refcapgroup.com said:**
> **Help Multi GPU**...
I then issued
**aticonfig --initial=dual-head --adapter=all.**
This created the long xorg.conf file for all the cards on the system to work.

**BUMPER !! **Machine reboots and right before the X login screen appears all of a  sudden my monitor screen goes into "Digital Power saving mode" and the monitor goes to  sleep. Keyboard and Mouse are not responsive (All freeze). No alternative but to cold boot the machine and restart.

Please take this for what it is worth (perhaps nothing in your case): there was a problem in X windows version 1.5 where the X server, upon finding more than one graphics device, could not determine which one to use as a primary device.  The X server would then simply quit executing without even creating a log file entry.  My workaround for that was to furnish a BusId for my primary graphics device; this disambiguated the configuration and allowed X server to function.

The new problem may or may not be related.  In any event, good luck and please let us know how to work around the new problem once you find a solution.

quadproc

---

### Post by jamesbrown on 2010-05-01
I did not encounter this problem until upgrading to 10.04, 9.10 worked as intended.

---

### Post by ask@refcapgroup.com on 2010-05-01
After trying everything, realised I had run out of options. To get system back operational before Monday deleted Ubuntu 10.04 completey and made a fresh install of Ubuntu 9.10. Went to ati website and downloaded latest catalyst 10.4. It worked out of the box. Again all I had to do was
aticonfig --initial=dual-head --adapter=all. And all my Six monitors are back working perfectly. This puts the problem squarely on Lucid 10.04 (talk about an upgrade shooting you in the foot).  How true the expression of old. "If it is not broken, don't fix it !"  learnt the lesson the hard way. No more upgrading for a LONG WHILE.

---

### Post by jamesbrown on 2010-05-01
I believe I will need to do the same I can't appear to get two ati 4870 gpus working with 10.04 no matter what I try.

---

