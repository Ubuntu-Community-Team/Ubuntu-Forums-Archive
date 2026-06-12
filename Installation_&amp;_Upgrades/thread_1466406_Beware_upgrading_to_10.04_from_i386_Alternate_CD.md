---
title: "Beware upgrading to 10.04 from i386 Alternate CD"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by RobertSwipe on 2010-04-30
Halfway through upgrading from 9.10 to 10.04 (i386 desktop) using the Alternate CD, you are prompted to insert "Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)".

Luckily, I'd already burnt a full installation CD so swapped this and the run continued for a moment. It then asked for the Alternate CD again (20100427.1).

If you haven't got a full install CD handy before you start, you may not be able to complete the upgrade.

---

### Post by ubun2warrior on 2010-04-30
Thanks for the warning !!

---

### Post by razeshkale on 2010-04-30
Same story... half way through and died, machine is not rebooting, trying to recover ubuntu 9.10 machine.

another hitch was not able to upgrade with disk... used gks cdrom upgrade but nothing comes up on screen after RUN..

hahah

waiting for recovery..

---

### Post by r-mo on 2010-04-30
Same with the 64-bit version

It asks for desktop
Please insert 'Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)' into the drive '/media/cdrom0/'

then for the alternate cd
Please insert 'Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427.1)' into the drive '/media/cdrom0/'

---

### Post by RobertSwipe on 2010-04-30
Altogether there were six changes back & forth - three in the "Getting new packages" phase and three in the "Intalling the upgrades" phase.

I'm just about to enter the "Cleaning up" phase, so hopefully that's the lot!

---

### Post by samuli64 on 2010-04-30
I got this as well, it was lucky that I had already downloaded the Desktop CD for a friend. I've only got it once so far, but it's still getting new packages so I'll see how it goes.

---

### Post by alfh on 2010-05-02
Same happened to me, the installation process stops promptly and there is no way to continue except for shut-down.

Surprised that these things still can happen, I´m downloading the desktop installer now from another computer. Hope this will solve my problem.

---

### Post by samuli64 on 2010-05-02
Well I ended up having to switch between the Alternate and Desktop CDs about half a dozen times as well, but I got there in the end. I was performing an 'Offline' upgrade, not sure if this will happen if you let the upgrade connect to the net.

---

### Post by Keith1212 on 2010-05-02
i just went into update manager and clicked update. took forever, but no disk swapping.

---

### Post by fschnittke on 2010-05-03
I had the same problem. Had to swap disks during the upgrade. I also had some error messages pertaining to likewise-open. I was a bit worried during the first reboot, but everything seemed to come up fine.

But I am noticing the same problem when trying to re-install rhythmbox from synaptic package manager:

[INDENT][FONT=Courier New]Please insert the disk labeled:[/FONT]
[FONT=Courier New]Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)[/FONT]
[FONT=Courier New]in drive /cdrom/[/FONT]
[/INDENT]After inserting the CDROM, it just keeps coming up with the same message....

I've installed other stuff from Synaptic this morning without any problem.

---

### Post by sagarhshah on 2010-05-25
I was wondering why it was asking me for the same as well.
Thank goodness someone else found out the problem before me and managed to figure it out.
Also glad I downloaded the desktop edition as well before I moved continents.
Internet in africa isn't as fast as in europe.

Thanks for going to the trouble of letting us know what to do.
I was contemplating on backing up and starting afresh but, I thought let me go over to the forums and see if anyone has had a similar problem.

Thanks alot guys.
Well I'm going to try this tonight and hopefully it will work.
Will report back on what happens.

Have a great day.
Sagar

---

### Post by Sunnz on 2010-05-27
Somehow I got the alternate CD to install and now up and running.

But sometimes when I install some software it sometimes ask me for the Desktop CD.

Now do I *have* to burn it to a CD? Is there a way to just mount the CD and just use that directly off the hard disk instead of having to waste another CD?

EDIT: just to answer my own question, it is quite easy to mount an ISO image:

```
# mount -o loop disk1.iso /mnt/disk
```

But I still get the problem where installing software prompts me for the CD, I ended up removing the CD as the repository in Software Manager and everything works from there.

---

### Post by Jerubaal on 2010-06-02
> **Sunnz said:**
> I ended up removing the CD as the repository in Software Manager and everything works from there.

This is exactly what I wanted to hear! I keep getting asked for the CD when installing stuff, but that is a right pain, especially as my download speed is usually good. 

My upgrade exerience wasn't too bad though (alternate CD).

---

