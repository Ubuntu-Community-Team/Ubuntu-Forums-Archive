---
title: "Boot from install cd not working. /bin/sh: can't access tty; job control turned off"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by marroon on 2007-03-28
I just downloaded ubuntu a couple hours ago from here [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

I burned it, booted it from cd, chose the Start or install ubuntu option, then it went to splash screen with the orange bar going back and forth, and then gave me the error message. 

BusyBox v1.1.3 (debian 1:1.1.3-2ubuntu3) built in shell (ash)

/bin/sh: can't access tty; job control turned off
(inittamfs)

I do ctr-alt-f1, and it has

cp: unable to open '/root/var/log/': no such file or directory
mount: Mounting: /root/dev on/dev/.static/dev failed : No such file or directory
mount: /sys on /root/sys failed: no such file or directory
mount: Mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have /sbin/init

The computer I'm installing on has 3 hard drives, so maybe that is part of the problem

what should I do?

---

### Post by dannyboy79 on 2007-03-28
this is becoming a more and more common issue! either the cd your using is bad or you need to try to add a boot option which acpi=off. burn the cd very very slow also!!! 4x or even 2x to ensure a good burn. check this thread ([http://www.ubuntuforums.org/showthread.php?t=386688](http://www.ubuntuforums.org/showthread.php?t=386688)) out for help in adding the boot option. Also, there is a search function at the top right of this forum, you could have found that many others are experiencing this and probably didn't even need to post this but since you have i'll help. just think about using the search function next time. good luck

---

### Post by marroon on 2007-03-28
thanks for your reply,

The cd looks good. I checked the md5sum, and did the Check CD for defects option on another computer. (Check CD gives the same error message on the computer I'm installing to)

I tried the options in that thread, and looked a bunch of others threads, but nothing worked. I'll try beta 7.04. If that doesn't work, I guess ubuntu is not meant for my computer

---

### Post by pradeepadapa on 2007-03-28
hello man, why dont u download the alternate cd nd then try to install frm the alternate cd instead of LIVE CD, just try that,

---

### Post by SteelShepherd on 2007-03-28
Same problem here...  I can't install Feisty - can't access tty; Job control turned off

I downloaded Feisty beta 2 (both kubuntu-7.04-beta-desktop-i386 AND Feisty 386) and can't hardly get past the boot choice before I get dumped to a command line with the error "can't access tty; Job control turned off"

I tried burning the Kubuntu disk a 2nd time using DAO at only 8x. Same error and running Test CD also fails with the same error. I googled quite a bit and found no solution yet. I don't have anything extra plugged into USB ports, etc.

What's the scoop with this error? It seems to be almost exclusive to Ubuntu.

My hardware is ASUS M2V-MX mobo
AMD 64 3000+
1 Gig DDR2 800
Biostar Nvidia 6300gt PCIe
via KM800 chipset

FYI, I have successfully installed Mepis 6.5 RC3 (based on Dapper) and Ubuntu Edgy on this same box, so the problem is specific to the Feisty.

---

### Post by dannyboy79 on 2007-03-28
didi you try the acpi=off or noapic within your boot options as others have done to get it work? there are many other boot options, check out thread #5 in this link: [http://www.ubuntuforums.org/showthread.php?t=386688](http://www.ubuntuforums.org/showthread.php?t=386688)

---

### Post by confused57 on 2007-03-28
> **dannyboy79 said:**
> didi you try the acpi=off or noapic within your boot options as others have done to get it work? there are many other boot options, check out thread #5 in this link: [http://www.ubuntuforums.org/showthread.php?t=386688](http://www.ubuntuforums.org/showthread.php?t=386688)
Nice writeup, it's definitely a seemingly common problem with no specific solution...just bookmarked your reply in that thread.

---

### Post by pgilmon on 2007-04-21
I had the same problem.

Finally I managed to boot from the live CD just by adding the folloing options to the boot command line (press F6 when the live CD bootup screen appears):

```
noapic nolapic
```

---

