---
title: "Failure to finish an install"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by Sor-app on 2007-10-22
I have a homebrew box, it has an MSI K8N Neo2 motherboard an AMD Athlon 64 3500+ processor and 1572864K memory, Bios is Phoenix Award Bios V6.00 PG The hard drive is a seagate 200 GB Barracuda 7200

I have tried several times to complete the installation of Kubuntu 7.10, the process will always freeze but never at the same place. Of the several times through the process here are my observations:
1.  When I tried to just use the Start kubuntu selection after the marker passed along the progress bar a few times the process stops.
2.  When I tried installing with a text interface, I noticed that there was an error message like, 53.764325 PCI: Cannot allocate resource region 0 of device 0000:00:00.0 
[The number 53.764325 would change regularly to larger and smaller numbers and seemed to be in the range of 10 to 100.]
The installation would then blythly progress as if nothing had happened. If  a previous install had died. Then, when the partition stage arrives I would be notified that there had been a file system error on IDE1 and IDE2 which had been improperly unmounted and I should run a program to check and repair the problem. If I reformated the drive then it would freeze again at places like:
1.  Install Base System libpam-modules (6%)
2.  Install base system Retrieving Libcrypt II (6%)
3.  Load additional components Retrieve ubuntu keyring-udeb (90%)
4.  Load additional components retrieving partmanBase (71%)
5.  Select and install software (6%) please wait......

Oh, I could tell the install had failed because the Caps Lock and Scroll Lock lights on the keyboard would flash in unison, and no response would come from any keys not Ctrl+Fn or Ctrl+Alt+Del.
I have gone through the help files at the beginning and tried no apic no lapic and several other choices  but nothing seems to change the final outcome.
Going though the archinve last night and today does not seem to yield threads with similar problems from which I may learn.
Anybody have any wisdom on this problem?

Thanks
Sor-app



While looking over other posts I realized that the Virus protection in BIOS had not been turned off.
I've been modifying this box for 12 years, I've installed new motherboards at least 5 times, and reinstalled windows at least 6 times. I've even encountered this very problem the first time I tried to load an operating system, I guess I got thrown because the process seemed so capricious. Fortunately my name is not in the post.

Sor-app

---

