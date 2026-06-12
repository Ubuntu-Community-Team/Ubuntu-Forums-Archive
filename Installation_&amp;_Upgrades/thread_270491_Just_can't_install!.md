---
title: "Just can't install!"
date: 2006-10-03
forum: Installation &amp; Upgrades
---

### Post by Gondorle on 2006-10-03
Hi there,

I'm getting really desperate here, maybe it's cause I'm st00pid or I just plain suck *** but erm, I can't even install ubuntu. I tried different dists of linux on vmware just to know which one to go for permantely and I figured ubuntu was the right one for me...I'm going to try and be as quick as possible with my problem description:

I downloaded .iso
Burned it in a cd
Reboot
Ubunt boot menu
Start or Install ubuntu...
Booting kernel...and thats it, it just "crashes" here, no error messages, no nothing..HD stops, no reading from drive, nothing...Waited a bit to see if it was normal but erm, after 10 min I allways quit. 

Thought it could be a burning problem, tried different burners, different .iso versions but it just won't work.

What could be the problem?

---

### Post by taurus on 2006-10-03
Before you burn it to a CD, did you remember to check the integrity of your iso file with md5?  Then, try to burn it at 4x instead of the max (auto) that you burner can handle...

---

### Post by Gondorle on 2006-10-03
.iso should be fine since I already installed it using vmware.

---

### Post by Old Pink on 2006-10-03
Try burning again, at 4x. 

Or use a different CD manufactuer/CD writer.

---

### Post by wpshooter on 2006-10-03
Make sure you are checking the integrity of the Ubuntu CD by running the verification check on the initial Ubuntu boot screen menu ?

If that does not work, have you tried downloading and burning the **ALTERNATE** CD version of Ubuntu ?

Have you ran checkdisk and degrag on your Windows O/S several times prior to attempting to install Ubuntu ?

---

### Post by Gondorle on 2006-10-03
> **wpshooter said:**
> Make sure you are checking the integrity of the Ubuntu CD by running the verification check on the initial Ubuntu boot screen menu ?

If that does not work, have you tried downloading and burning the **ALTERNATE** CD version of Ubuntu ?

Have you ran checkdisk and degrag on your Windows O/S several times prior to attempting to install Ubuntu ?

When I run the verification check on the initial ubuntu boot screen menu, same happens again, it "crashes" when loading kernel. Havent tried to download the alternate cd version but is that really what I want? I don't know anymore :S

Ran checkdisk and defrag, same thing happens. I'm burning the cd at 4x at the moment, see how it goes.

Thanks.

---

### Post by doobit on 2006-10-03
Maybe your system is below the minimum requirements for the standard live CD install. You need at least 198 MB How much RAM do you have and what processor?

---

### Post by Gondorle on 2006-10-03
2gb ram. Intel Core 2 Duo Processor 6300, 186mhz

---

### Post by wpshooter on 2006-10-03
> **Gondorle said:**
> 2gb ram. Intel Core 2 Duo Processor 6300, 186mhz

Well, not too old, maybe to NEW.

I think your next move should be to download, burn and try the ALTERNATE CD version.

---

### Post by Gondorle on 2006-10-03
Burning at 4x didnt solve the problem too unfortunately :(...Explain to me what is the difference between the desktop version and the alternate version please.

edit: Btw, Im not sure if you read it, I managed to install unbut using vmware the first time.

---

### Post by doobit on 2006-10-03
There are some issues with the Live CD install and certain CDROM/DVD drives, and also installing to SATA drives. 
Also could be an ACPI problem. One thing to try is to put one of these boot command options in the boot command line ```
ide=noapm
``` or ```
apci=force
```

I had to install from a regular ATAPI CDROM drive because it wouldn't install from my DVD drive.

These issues do not seem to exist with the Alternate install CD.

Take a look at this thread:
[http://www.ubuntuforums.org/showthread.php?t=186115](http://www.ubuntuforums.org/showthread.php?t=186115)

---

