---
title: "Need help - GRUB is broken since Dapper, still broken now!"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by 51m0n on 2007-04-26
Right, can someone please explain how (K)Ubuntu/Debian can be so broken and no one seems to have any idea why or how to fix it for sure yet?? No one even seems to want to acknowledge there is an issue!

Dapper's GRUB is busted. I can install an Mdk 10.1 system in minutes and it all works and boots fine - I just did. SUSE 9.x the same etc etc. As soon as I try Dapper I get as far as GRUB Stage 1.5 and then it hangs - no errors.

Booting the system with the Grub Super Disk exposes that grub cant even see, is utterly unaware of at least one possibly two of my three hard drives (find cant find files on the system that are clearly there as I can navigate to them in Konqueror and the CLI). 

There have been posts about this butI cant find a procedure anywhere to get beyond Stage 1.5 Can anybody suggest anything that they know worked?

Worse still is Feisty. I can install Feisty and everything seems to work, and Grub reports complete success with an install into MBR. On a reboot however I get nothing at all. No sign of GRUB, the system just restarts over anover again.

What gives? All references to this issue and Feisty are that it's fixed. Well it isn't at all!

I'm trying to get this working on an ABIT KG7-RAID mobo with 3 drives plugged into the Highpoint Controller (clearly ther are no issues booting from this controler, I've been doing so for 5 years).

Sorry if I sound a bit stressed but I've lost a weeks sleep over this and had a resoundingly lacklustre response to pleas for help. Those who have tried/offered anything - thanks alot, really! Anybody with some more info, please let me know, anyone putting this stuff together, any ideas when there may be a fix (dont care how long I just need to know if its even in the pipeline)?

The real killer is I'rn using Kubuntu on a supposedly much harder to get going machine (HP nx6125) and have no end of help and support getting i all running - which it now does superbly,and I really really like the distro. Just a shame it wont boot on old kit.

Si

---

### Post by zvacet on 2007-04-26
Maybe this can help you

[http://ubuntuforums.org/showthread.php?t=424166]("http://ubuntuforums.org/showthread.php?t=424166")

---

### Post by 51m0n on 2007-04-26
Thanks,

I've tried this precise set of steps already I'm afraid. The is weirder than that.

Grub's device.map has:-

(hd0) /dev/hde
(hd1) /dev/hdf
(hd2) /dev/hdg

But in the grub shell find doesn't find anything on any partition mounted on hde. Naturally hde is where windows is, and /boot (second partion on the drive).

One thing to note is I prefer reiserfs, and have had no issues with it in the past  but I did see someone say grub doesn't play nice with reiserfs, anyone have any more to offer??

---

