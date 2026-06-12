---
title: "Can't get Broadcom STA installed"
date: 2010-03-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by COLiNx86 on 2010-03-09
I haven't used Ubuntu (or linux at all) since 9.04(maybe 8.10), but I saw the new theme and that it was a faster boot time, and then I had to try it.
First thing, boot times are ridiculous...there so fast!! takes mine 15sec.

Anyways, after I installed it I went to hardware drivers to install the broadcom sta driver, whenever I click on it to install it starts to install then says something about Jockey failing.  Anything I can do to get it to install?  oh I can't get internet without this, I don't have the cable to plug my computer directly into the router.

I figure I probably need to update.  Anyway I can maybe download the updates on my windows partition, and move them to the Ubuntu partition and manually install them?

Thanks,
Colin.

---

### Post by tekstr1der on 2010-03-09
```
sudo aptitude install bcmwl-kernel-source
```

This will build the proper kernel modules needed for Broadcom 802.11 STA Wireless drivers

---

### Post by Trespasser on 2010-03-09
Individually install dkms, fakeroot, patch, and the bcmwl-kernel-source package from the live-cd then reboot.

---

### Post by jynyl on 2010-04-03
The instructions over [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1368699") seem pretty good, except (using liveUSB Lucid netbook beta1 on HP mini 5102, 4322 wireless) I found I needed to install patch and fakeroot before running the bcmwl-kernel-source deb at step 2.2.4 of those instructions.

I hope this is fixed for the final version of Lucid.  There were about 9 dependencies required for the dkms and bcmwl packages.  These were all on the liveUSB, but still a mission to find and run them all.

---

### Post by teh603 on 2010-04-03
I've found that I often have to install updates before I can find bcmwl in synaptic. I think its got something to do with synaptic not having the driver in its package lists at that time, or something.

---

### Post by gjoellee on 2010-04-03
> **COLiNx86 said:**
> I haven't used Ubuntu (or linux at all) since 9.04(maybe 8.10), but I saw the new theme and that it was a faster boot time, and then I had to try it.
First thing, boot times are ridiculous...there so fast!! takes mine 15sec.

Anyways, after I installed it I went to hardware drivers to install the broadcom sta driver, whenever I click on it to install it starts to install then says something about Jockey failing.  Anything I can do to get it to install?  oh I can't get internet without this, I don't have the cable to plug my computer directly into the router.

I figure I probably need to update.  Anyway I can maybe download the updates on my windows partition, and move them to the Ubuntu partition and manually install them?

Thanks,
Colin.

Jockey is a package that had something to do with "Hardware Driver" to do. Have a look out for updates on the jockey packages for a fix.

These things happen when you run systems under development.

---

