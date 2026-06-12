---
title: "error no such device grub rescue common error lately---is there a fix?"
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by ellabee on 2010-08-02
after lots of searching last night i noticed that over the last couple of days there have been quite a few posts of people recieving the error: no such device lotsofnumbers grub rescue>
i have a dual boot vista/ubuntu setup with ubuntu on my d: drive and windows on my c: drive and it happened to me last night. so after my freaking out when i received the grub rescue> error after updating somethings in my ubuntu install and restarting. once the computer rebooted bam! error. after much freaking it **_only_** fixed itself by reinstalling the windows bootloader via the vista rescue disk i was wondering if there was a way to prevent this from happening again? will ubuntu attempt to "update" itself again?

---

### Post by Rubi1200 on 2010-08-02
Forum member bcbc has reported this as a bug.
 
You can follow its progress here:
 
[https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)
 
The solution you followed is the correct one, for the moment at least.

---

### Post by AshWatson on 2010-08-11
I have the exact same problem, i cant boot up in any os, windows or ubuntu i cant boot up, only thing is how did your windows bootloader fix itself, did it just do it automatically or did you do it manually, love to know so that hopefully i could then fix mine.

---

### Post by bcbc on 2010-08-11
> **AshWatson said:**
> I have the exact same problem, i cant boot up in any os, windows or ubuntu i cant boot up, only thing is how did your windows bootloader fix itself, did it just do it automatically or did you do it manually, love to know so that hopefully i could then fix mine.

It's not automatic. You will need to reinstall the windows bootloader. Instructions are [here]("http://ubuntuforums.org/showthread.php?t=1014708"). Scroll down to the appropriate section e.g. How to restore the windows XP bootloader, or Vista/7.

It's also possible to fix this from an ubuntu live cd if you don't have windows disks. Ask if you want to do it this way.

---

### Post by watari_l on 2010-08-11
I also have this problem. I try holding shift when i boot my computer to access grub but it won't. is there any solution for this

---

### Post by bcbc on 2010-08-11
> **watari_l said:**
> I also have this problem. I try holding shift when i boot my computer to access grub but it won't. is there any solution for this

I have to be a little careful. You can get this problem but the cause may be different. If you installed ubuntu in windows (using wubi), the fix is as I described above.

If you installed Ubuntu direct to partition, then the fix won't help you (although it will likely get windows booting).

So, if it's the same problem use the above fix. Otherwise create a new thread and post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and someone will help.

---

