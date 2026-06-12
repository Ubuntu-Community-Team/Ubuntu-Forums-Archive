---
title: "lost my windows partition after replacing power supply???"
date: 2013-06-13
forum: Installation &amp; Upgrades
---

### Post by Radamand on 2013-06-13
system setup to dual-boot Win7 & Ubuntu 12.04:

My PC's power supply crapped out so i replaced it, when booting I get the grub menu, select Windows, and get "Invalid Signature".

Googling around I come across a thread suggesting I run boot-repair from an ubuntu terminal, I do and now my Win7 partition doesn't even show up in the grub boot menu......

It's late, i've had a very long day, and don't have the energy to deal with this tonight, please someone tell me what diagnostics you need me to run to troubleshoot this....

---

### Post by Radamand on 2013-06-13
sigh......  now i've completely buggered it up.....

reinstalled ubuntu, updated grub, now on boot i get "No operating system found. Press any key to blah blah blah......"

---

### Post by ahallubuntu on 2013-06-13
~

---

### Post by Radamand on 2013-06-13
It could have been a power surge, all i know is it was dead.  and yes, it was an el cheapo (Lenovo PC) power supply, I replaced it with a decent one.
My BIOS no longer even shows the HD that windows is installed on.

Booting with Windows CD and going to 'Repair my Windows Install" says "This version of windows repair options is not compatible with the version of windows you are trying to repair", which is odd because this is the exact disk windows was installed from.....


I will try the SMART utility, other than that what can I do to troubleshoot/repair the HD that doesn't show up in BIOS?

---

### Post by Radamand on 2013-06-13
okay, finally got gsmartcontrol setup;
The windows drive does not show up when i start gsmartcontrol, when i tried to 'add device -> /dev/sdb' the execution log says "NO MEDIUM present on device".  I'm betting this is not a good thing....

fdisk -l does not even show the windows HD.....  any way to restore it?

---

### Post by steeldriver on 2013-06-13
... are you sure you got the power supply connection to the HDD seated correctly when you replaced the PSU? and didn't dislodge the data connector? sometimes it's the simplest things...

---

### Post by Thee on 2013-06-13
If all fails, try connecting the HDD to another PC to see if it works there.

---

### Post by Mark Phelps on 2013-06-13
> **Radamand said:**
> ... other than that what can I do to troubleshoot/repair the HD that doesn't show up in BIOS?

Sorry ... basically, nothing.  If the BIOS doesn't see it, no OS or utility is going to see it, either.

If the BIOS does see it, there are MS Windows utilities that do a good job of searching for and finding directories and files, even when the partition table itself is corrupted or missing -- but you would need to be able to connect the drive to an MS Windows PC, and then, that BIOS will have to be able to see it.

---

### Post by QIII on 2013-06-13
Hello!

Forgive me for asking the obvious, but did you check the cable connections on the drive?

---

### Post by grahammechanical on 2013-06-13
I also have a question, that also may be obvious. Would replacing the power supply constitute trying to run Microsoft Windows on another machine? Does Windows need to be reactivated? I am not using Windows, so I know nothing about this except rumours about Microsoft stopping users from running the OS on more than one set of hardware components.

Regards.

---

### Post by ahallubuntu on 2013-06-13
~

---

