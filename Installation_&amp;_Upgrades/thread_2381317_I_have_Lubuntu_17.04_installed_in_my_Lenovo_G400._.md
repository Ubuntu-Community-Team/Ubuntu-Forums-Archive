---
title: "I have Lubuntu 17.04 installed in my Lenovo G400. Is it safe to update to 17.10 yet?"
date: 2017-12-29
forum: Installation &amp; Upgrades
---

### Post by data4pass on 2017-12-29
There is a known bug affecting Lenovo laptops that upgrading to Ubuntu 17.10 may result in a bricked laptop, [link]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147"). The issue appears to have been fixed with the next Kernel update (4.13.0-21). Seeing as Lubuntu 17.10 [now ships with Linux Kernel 4.13]("https://lubuntu.net/lubuntu-1710-artful-aardvark-released/"), does this mean that it is now safe to upgrade?

  For the record, I intend to upgrade via Software Updater, which has notified me that an update is available.

  Thank you!

---

### Post by #&amp;thj^% on 2017-12-29
This is just "my" experience with that bug listed. I am Always upgrading to the newer release's (In testing) I have never had any issues. Lenovo T430
That said i did have a friend that brought me her laptop with the corrupt bios (From a fresh clean install) that I was able to fix by installing kernel 4.14, and after a couple of reboots the Bios were back and functional. NOTE: (Your Mileage may vary)
But upgrading to 17.10 was reported to be safe as it pulled in the fixed kernel.

---

### Post by uRock on 2017-12-29
[s]I wouldn't go through with it until the download is made available again on ubuntu.com.[/s]
1fallen seems to have good information.

---

### Post by deadflowr on 2017-12-29
> Seeing as Lubuntu 17.04 now ships with Linux Kernel 4.13, 
When did that happen?

---

### Post by data4pass on 2017-12-29
> **deadflowr said:**
> When did that happen?

Ah, I meant 17.10, corrected.

---

### Post by deadflowr on 2017-12-29
> **data4pass said:**
> Ah, I meant 17.10, corrected.

:lolflag:

I thought I missed something important happening.

---

### Post by #&amp;thj^% on 2017-12-29
**NOTE: This is just one case test here.** **_Your Mileage may VARY_**
Just wanted to add that I just now 12/29/2017 Downloaded the iso Dated 2017-10-18 18:53>> From here: [http://releases.ubuntu.com/17.10/](http://releases.ubuntu.com/17.10/)
Installed a fresh clean install from that .iso.
All is Good! For me.
System:
```
inxi -M S && uname -a
Machine:   Device: laptop System: LENOVO product: 2349M88 v: ThinkPad T430 serial: N/A
           Mobo: LENOVO model: 2349M88 serial: N/A
           UEFI [Legacy]: LENOVO v: G1ETB2WW (2.72 ) date: 01/31/2017
Linux me-ThinkPad-T430 4.13.0-21-generic #24-Ubuntu SMP Mon Dec 18 17:29:16 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

And From here: [https://www.theregister.co.uk/2017/12/21/ubuntu_lenovo_bios/](https://www.theregister.co.uk/2017/12/21/ubuntu_lenovo_bios/)
> A spokesperson for Intel has been in touch to say the chipmaker is aware of the BIOS cockup triggered by installing Ubuntu Linux 17.10. "We&#8217;re actively working with Ubuntu to ensure the issue is corrected," she said. "This is a unique issue based on non-Intel recommended changes made to the BIOS configurations by Ubuntu."

These machines are not really permanently borked. It is possible to reflash them, which restores normal BIOS functionality. The difficulty is that Lenovo only supplies reflashing tools which work under Windows, and in order for these to work you need to boot Windows. Which is tricky, if your only OS available on disk is Linux, and you cannot boot anything else from USB.

Some affected users managed to attach CDROM via USB and proceed from there. Ideally Lenovo should provide BIOS reflashing tool which works under Linux :(

Hope this is useful.

---

### Post by data4pass on 2017-12-30
Thank you, 1fallen, deadflowr and uRock. Your information have been very useful.

I think I will just wait until the fixed iso is released. For some reason I'm still hesitant to upgrade via Software Updater despite the reports that the updates provided from it includes a fixed kernel. :)

---

### Post by mörgæs on 2017-12-31
Good idea. I always prefer a fresh install to an upgrade.

Support for 17.04 runs out in january which usually means end of the month so you have plenty of time.

---

