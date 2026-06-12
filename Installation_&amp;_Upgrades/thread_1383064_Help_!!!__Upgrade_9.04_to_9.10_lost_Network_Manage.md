---
title: "Help !!!  Upgrade 9.04 to 9.10: lost Network Manager"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by jfl on 2010-01-16
Hi,

This is my fourth on-line upgrade from Gutsy (started with Dapper ...) all the previous one went without a hitch !

So I was pretty confident this afternoon upgrading my Lenovo laptop from 9.04 to 9.10.

At one point during the install, I got error messages and was offer to do a "Partial Install".  I accepted, different things happened, rebooted. Update manager came on with again the partial update pop-up. Accepted it again, it downloaded more files, rebooted, partial upgrade window again but it failed immediately.

The network connection was gone, clicking on the network icon I got a message that the network manager is not running.
I cannot check or uncheck the "network unabled" choice.

However, 9.10 is running, slow and weird, but no network connection so I cannot try to finish the "partial upgrade"

Every time I reboot the Update manager pops up.

Trying to boot any previous version in "grub" fails right away saying it is unable to mount the drives ...
[B]

Any suggestions ?

Is there a way to start the Network Manager from a terminal ???[/B]

Help !!!!!!!!!!!

Thanks.

---

### Post by jfl on 2010-01-17
Well, looks like other things are not working either; it was really a partial install :rolleyes:

It is trying to finish the upgrade, fires up the "Update Manager" every few minutes, but the networking cannot start.
Is it possible to "rescue" the system ?
I created a "Live CD" that works well, but I don't see how to use it to repair the system.

Thanks in advance for any suggestions, I am trying to avoid a "clean install", I'd loose too many things.

---

### Post by n0dix on 2010-01-17
> 

Is there a way to start the Network Manager from a terminal ???[/B]



```
nm-applet
```

---

### Post by lidex on 2010-01-17
Are you dual-booting? If so, download the 9.10 LiveCD. If you have separate /home partition, you can install over that mess and save your data. Worst case - back up your data and re-install.

---

### Post by jfl on 2010-01-18
My "home" directory is in a separate partition, good thing !!!
I tried to install with the live CD had errors even though the disk shows good.
Tried with the alternate CD, workrd like a charm; had to re-install a few apps, no big deal.

However, I am a bit disappointed; the previous on-line upgrades went easy.

All the people I know would not have gone through all this; I hate to say it but Ubuntu is definitely not ready for "mainstream" ...

---

### Post by lidex on 2010-01-18
> **jfl said:**
> My "home" directory is in a separate partition, good thing !!!
I tried to install with the live CD had errors even though the disk shows good.
Tried with the alternate CD, workrd like a charm; had to re-install a few apps, no big deal.

However, I am a bit disappointed; the previous on-line upgrades went easy.

All the people I know would not have gone through all this; I hate to say it but Ubuntu is definitely not ready for "mainstream" ...

Always seems worse when it happens to you:rolleyes:
The main reason people forget about windows upgrade nightmares - and there are plenty - is the time lag between releases. ;)

---

