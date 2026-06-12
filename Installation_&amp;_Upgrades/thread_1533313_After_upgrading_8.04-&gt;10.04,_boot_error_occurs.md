---
title: "After upgrading 8.04-&gt;10.04, boot error occurs"
date: 2010-07-17
forum: Installation &amp; Upgrades
---

### Post by Jetro on 2010-07-17
During upgrading from 8.04 to 10.04, I was asked several times what I wanted to do with *menu.lst*. I gave the same reply each time: "keep the local version currently installed". I wanted it the way I had when using 8.04; that is, not having the un-customizable grub menu I've experienced before with 10.04.

When I was done installing 10.04 and was going to reboot, the GRUB menu appears as it has before, and the Ubuntu entry says "Ubuntu 8.04", even though it's now 10.04.

But when I choose "Ubuntu 8.04", the following error message occurs:

```
error sending message: Connection refused
udevadm[900] error sending message: Connection refused
udevadm[901] error sending message: Connection refused
udevadm[902] error sending message: Connection refused
error: unexpectedly disconnected from boot status daemon

libdev: undev_monitor_mew_from_netlink: error getting socket: Invalid argument
Segmentation fault
Gave up waiting for root device. Common problems:
- Boot args (cat /proc /cmdline)
 - check root delay= (did the system wait long enough?)
 - check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; Is /dev)

ALERT! /dev/disk/by-uuid/23aec7cf-e7dc-4401-bd14-34237f32b5c6 does not exist. Dr
opping to a shell!

BusyBox v.1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)

Enter "help" for a list of built-in commands.

(initrams)_
```

If keeping the local menu.lst version installed was going to make Ubuntu unbootable, I never would have chosen it.

Can anybody please help here, if you know what's going on? :|

[COLOR="Gray"](I feel certain that I did thorough searches for this beforehand, and I found nothing that complied with my issue.)[/COLOR]

Edit: I clumsily forgot to add the rest of the error message, it is now added.

---

### Post by Rubi1200 on 2010-07-18
> If keeping the local menu.lst version installed was going to make Ubuntu unbootable, I never would have chosen it.

Newer versions of Ubuntu use GRUB2. I understand that you wanted to stick with something familiar, but GRUB2 is the way of the future and not as complicated to customize as you might think.

Here is the link to read about it:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

As far as your current situation is concerned, I would wait until one of the more experienced forum members comes along with suggestions/solutions.

But I do advise that you get hold of a LiveCD and use it to save any important files just in case.

---

### Post by Jetro on 2010-07-18
Thank you. The last time I checked I think GRUB2 was entirely "beta" and highly unstable. But I see how that becomes a problem for me now. :P

I added the rest of the error message, which I had forgotten about.

---

### Post by Jetro on 2010-07-19
I just removed 8.04/10.04 entirely, and installed it again. So I guess this topic is not needed anymore. :)

Now I get the GRUB 2 menu and all works. What still occurs, though, is that after every update (had one so far) where you have to reboot, Ubuntu doubles it's boot entries for no apparent reason. If GRUB2 is the "future", it's dazzling that they haven't changed such a cluttering and obvious bug like this. :)

---

### Post by Rubi1200 on 2010-07-20
> **Jetro said:**
> I just removed 8.04/10.04 entirely, and installed it again. So I guess this topic is not needed anymore. :)

Now I get the GRUB 2 menu and all works. What still occurs, though, is that after every update (had one so far) where you have to reboot, Ubuntu doubles it's boot entries for no apparent reason. If GRUB2 is the "future", it's dazzling that they haven't changed such a cluttering and obvious bug like this. :)

The extra entries are there for a reason; these are the old kernels. If, for some reason, an update breaks your system, you can always boot into the previous version.

You can also remove these entries if you wish, but many people like to keep at least one old entry as a precaution.

---

### Post by Mistiq Dragon on 2010-08-03
Need to delete this but don't see the option

---

### Post by Jetro on 2010-08-24
Okay... so you say all the Ubuntu entries are there for a reason, but none of them (except the newest one) actually works (for me), it is cluttering and takes up space. What is the point of updating, if not to remove those old entries?

Anyhow, I read the [Grub 2 Community Ubuntu Communication](https://help.ubuntu.com/community/Grub2), and it seemed to me that StartUp-Manager would be the best alternative for a complete rookie like me. However, this does not allow me to remove obsolote entries, as well as vapourising the Ubuntu boot logo. (At first it was two of them, half-wide with distorted colours, and now it is just a mess of pixels.) So I find it only make things worse, and I want to remove it.
**Is there a way to restore the settings done by StartUp-Manager till the way it was before?**

---

### Post by Jetro on 2010-08-28
According to [this guide](https://help.ubuntu.com/community/StartUpManager), I can just hit "Restore Original Settings." But there is no "Restore Original Settings" button in the manager. It looks like this: (See attachments.) and a thorough search on Google didn't help. Also, completely removing the StartUp-Manager from Synaptic didn't restore anything.

---

