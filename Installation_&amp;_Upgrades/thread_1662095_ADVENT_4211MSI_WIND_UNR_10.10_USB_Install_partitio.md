---
title: "ADVENT 4211/MSI WIND UNR 10.10 USB Install partition issur"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by LZ31380 on 2011-01-07
Hello all,

I'm not certain on this one, but from my search in the forum i don't think this issue has been addressed extensively yet. 

I have an ADVENT 4211B or C (depending on where you read the labels it has). it was bought from dixons in the uk. I have read that it is an MSI Wind u100 rebadge.  it originally came with 512 ram, win xp sp2 and 120 gb hdd. i upgraded to 1024 ram, and after a few years, having survived a win xp sp2 crash, malware etc.. decided it was time for a linux distro. the thing had a nasty malware on it that kept me from accessing registry and was quite persistent. 

I chose to install UNR 10.10 recently, since the thing has no cd, only a usb would do. i used a 4GB Kingston bought specially for this install. i tried to run live and install directly many ways but it keeps hanging once i click forward in the preparing to install phase, just before partitioning ( which i never reach ). it just stalls there and i see the waiting icon . the mouse still moves and i can still shut down.

i know that it is something to do with the gparted app not able to work while the usb is plugged in. i know because after using many apps to mount the live version on my usb, and after ensuring my hdd had nothing seemingly wrong with it through freedos and other apps, and after making sure the checksums were alright, etc.... 

i actually mounted a gparted live from usb and it only read my drive when i removed the usb (booting to ram). it seems that the issue is not Ubuntu as much as it is the partition app that won;t start.


so.. the question is.. how do you install UNR on a netbook with only a USB, no other OS ( i wiped out windows as it had malware i couldnt dodge as i said). can you find a way to copy the installation files to a partition from the USB, then install from the hdd itself. or should you partition beforehand?

i really do not want to have to run from a live usb. i just want a good OS for the netbook which i only use for light work. I have two other laptops for the heavy work.

coudl i for example find way to link two laptops together through a coaxial and install from one laptop to another? can i use my router? is there anyway to simply avoid buying an external cd? its simply not worth it and i am guessing from other posts that even cd roms are having this issue.

apologies for long post/.

L








the problem is that

---

### Post by Quackers on 2011-01-07
Which screen exactly do you click "forward" on and it stalls?

---

### Post by LZ31380 on 2011-01-08
as i mentioned in the text. its the preparing to install phase.

---

### Post by LZ31380 on 2011-01-09
bump. also to clarify... it just stays that way for more than 1 hour....

---

### Post by LZ31380 on 2011-01-11
i figured it out from other forums. its got something to do with partition tables of modern usb flash drives. mine started at 4 instead of 1. some said they managed to xero them using fdisk but did not mention exactly how to do on netbooks with no other means. i got another external hd that did not have this issue and it worked fine. 
I think unetbootin and other similar apps should factor this problem in. it seems to affect many, and since the issue was not reportable with apport, it's left to teh poor user and his patience levels to get through. 

all this for a secondary laptop. the one positive is that i learned a few things about fdisk, gparted, partition tables, a few other linux distros (slax is nice btw)...

so the easiest solution is changing booting medium , if you are stubborn like i am, but still a noob, like i am..it becomes a headache.

---

