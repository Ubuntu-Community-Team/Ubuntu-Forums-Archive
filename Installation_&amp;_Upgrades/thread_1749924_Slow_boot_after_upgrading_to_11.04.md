---
title: "Slow boot after upgrading to 11.04"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by fulopattila122 on 2011-05-05
Hi, my laptop's boot speed has been tremendously dropped (approximately from 30 secs to 3-4 minutes) after I've upgraded from 10.10 to 11.04.

What do you recommend me to check in order to get back my lost time? :)

---

### Post by ivanovnegro on 2011-05-05
I think the boot time of Ubuntu 11.04 is a little bit longer as with the older releases, at least it was in my case.
The only thing I could think of would to install 11.04 from scratch but that would be something you maybe dont want to do.

---

### Post by fulopattila122 on 2011-05-05
Yes, I don't want to reinstall. I could then switch back to windows and reinstall it in every 6 months to keep it in a good shape :)

---

### Post by mikehenry001 on 2011-05-05
I installed 11.04 into a new VM and it takes much more time than 10.10.

---

### Post by ivanovnegro on 2011-05-05
Im sorry for that but I think at the moment this is this way, 11.04 is really a bit slower in booting as it was 10.10 at least with Ubuntu Unity.

---

### Post by fulopattila122 on 2011-05-06
As far as I see it doesn't make too much sense whether Unity or Gnome is being used. I switched back to Gnome from Unity right in the beginning, and I didn't recognize difference in the boot time.

Unity would worth another `praising` thread.

It seems to me that Canonical has started to cut out Ubuntu's balls with the release of version 11. It remembers me to Microsoft's Vista.

---

### Post by Foxcow on 2011-05-08
Even with my hardware (1090T, SSD, etc), 11.04 takes almost two minutes to boot.  10.10 booted in about 10 seconds...

---

### Post by fulopattila122 on 2011-05-09
In your case it's 12x slower then. It's not a minor change.

---

### Post by fulopattila122 on 2011-05-09
I used [bootchart to profile the startup]("http://linux.aldeby.org/speed-up-your-ubuntu-linux-boot.html"). What at first sight is interesting is that even if I'm using Ubuntu in Classic mode (aka Gnome) I have a `unity-window-de` (I guess it's unity-window-decorator) process running during the startup.

Is that normal?

---

### Post by epictetus on 2011-05-09
Much slower boot time here, too. Staring at the purple screen of death for about 5 minutes. With 10.10, 10.04, and 9.10 boot time was approx 30-45 seconds. Very irritating as the time my monitor can be turned on is limited, and Ubuntu will often screw up the resolution (and not let me fix it without restarting) if I don't have my monitor plugged in and turned on during boot-up. Also very irritating since 11.04 is not recognizing USB devices that were not plugged in at boot-up (so if I need to plug something new in, I have to reboot).

Didn't expect this from Canonical.

---

### Post by Foxcow on 2011-05-09
Bootchart showed some interesting things.  I'll have to mess with it when I get home.

Bootchart:

[IMG]http://i.imgur.com/ZXeJx.png[/IMG]

---

### Post by fulopattila122 on 2011-05-09
Btw, did anyone of you try to _use_ banshee? That program must be a joke (buggier then Win95 was).

Ubuntu 10 was such a good piece of cake that Canonical seems gained an over-confidence, beliveing they're kind of a messiah who's gonna revolutionize the PC industry. However most of their new stuff seems to be sole sophistry, so at the end of the day they just wanted to poop bigger than their hole is.

I'm sorry to say that, but I'm so disappointed about 11.04.

---

### Post by Foxcow on 2011-05-09
I think I found a solution:

> 
in /lib/udev/rules.d/60-persistent-storage.rules

comment out rule:

# ATA/ATAPI devices (SPC-3 or later) using the "scsi" subsystem
KERNEL=="sd*[!0-9]|sr*", ENV{ID_SERIAL}!="?*", \ SUBSYSTEMS=="scsi", ATTRS{type}=="5", ATTRS{scsi_level}"[6-9]*", \ IMPORT{program}="ata_id --export $tempnode"


then run as root
```

update-initramfs -u

```reboot, and check your booting time

Here is my new bootchart:

[IMG]http://i.imgur.com/pALxz.png[/IMG]

---

### Post by CoaxVex on 2011-05-09
I just tried using bootchart myself, and it looks like rebooting or booting from a shutdown state give quite different results.

Have you tried cold-booting as well after making that udev change?

---

### Post by Foxcow on 2011-05-09
> **CoaxVex said:**
> I just tried using bootchart myself, and it looks like rebooting or booting from a shutdown state give quite different results.

Have you tried cold-booting as well after making that udev change?

Not as of yet.  Will try when I get home tonight.

---

### Post by fulopattila122 on 2011-05-09
Wow, what does this rule exactly do? I googled but don't really understand what's being changed.

---

### Post by Foxcow on 2011-05-09
> **fulopattila122 said:**
> Wow, what does this rule exactly do? I googled but don't really understand what's being changed.



I'm not sure either.  I'm guessing it has something to do with the way the OS interacts with the drive during boot.  There really isn't any info available.

---

### Post by intheflesh on 2011-07-19
> **Foxcow said:**
> I think I found a solution:
...


Thank you, this helped speed up my boot time from 70+s to about 37s (29s from GRUB to login window, 8s from presssing enter to full desktop; used to be 30+40+).

Now I just have to figure out how to reduce those initial 30 seconds.

---

### Post by thom_raindog on 2011-09-28
> **intheflesh said:**
> Thank you, this helped speed up my boot time from 70+s to about 37s (29s from GRUB to login window, 8s from presssing enter to full desktop; used to be 30+40+).

Now I just have to figure out how to reduce those initial 30 seconds.

I was struck by the same problem AFTER I had my broken mainboard switched to another model. This solution here fixed it for me too, but I am left a bit curious as to what I just commented out. Would rather not find out weeks later that it was something rather important ;)

---

### Post by drbono on 2011-11-03
Running Linux Mint Katya.  Haven't done the bootchart yet, however with the old stop watch I was having 1:48 second boot.  After performing what this post said, my boot is down to 42 seconds. :D

I would also like to know just what this does, but much happier even not knowing...thanks for the post!

---

### Post by fulopattila122 on 2011-11-04
> **drbono said:**
> but much happier even not knowing...

Kinda like this sentence! :D

---

### Post by th3_survivor on 2011-11-23
Sorry for the stupid question but... how to "comment out rule", because nothing happened when I tried this solution - so I think I haven't done it right. :(

---

### Post by fulopattila122 on 2011-11-23
> **th3_survivor said:**
> Sorry for the stupid question but... how to "comment out rule", because nothing happened when I tried this solution - so I think I haven't done it right. :(

How did the line look before and how does it look after you've changed it?

---

### Post by th3_survivor on 2011-11-23
Now I'm not at home, so I can't copy the exact line but I think it was something like this:

# ATA/ATAPI devices (SPC-3 or later) using the "scsi" subsystem
KERNEL=="sd*[!0-9]|sr*", ENV{ID_SERIAL}!="?*", \ SUBSYSTEMS=="scsi",  ATTRS{type}=="5", ATTRS{scsi_level}"[6-9]*", \ IMPORT{program}="ata_id  --export $tempnode"

and I've just deleted the #

---

### Post by fulopattila122 on 2011-11-23
> **th3_survivor said:**
> 
# ATA/ATAPI devices (SPC-3 or later) using the "scsi" subsystem
KERNEL=="sd*[!0-9]|sr*", ENV{ID_SERIAL}!="?*", \ SUBSYSTEMS=="scsi",  ATTRS{type}=="5", ATTRS{scsi_level}"[6-9]*", \ IMPORT{program}="ata_id  --export $tempnode"

and I've just deleted the #

It should be:

# ATA/ATAPI ...
# KERNEL=="sd* ...

The phrase `to comment out` is also often ambiguous for me.

---

### Post by th3_survivor on 2011-11-23
> **fulopattila122 said:**
> It should be:

# ATA/ATAPI ...
# KERNEL=="sd* ...

The phrase `to comment out` is also often ambiguous for me.

Thank you very much. I'll do it tonight :)

---

### Post by th3_survivor on 2011-11-27
Hi again. My bootchart image shows time: 00:17.61 so I think my problem is something with Grub because when I choose Ubuntu from grub menu it actually needs about 18 seconds to show up password window. But it needs more than 1 minute to show up the grub menu. I've a dual boot system with Windows 7. First I see the purple screen then after 30 sec I can see the menu entries showing up one by one. If I want to choose anything else instead of default entry it reacts very slow. When I press Enter I have to wait again.
I wonder if this is because in earlier versions Grub menu resolution was lower and now it takes my 21.5" monitor resolution?

---

