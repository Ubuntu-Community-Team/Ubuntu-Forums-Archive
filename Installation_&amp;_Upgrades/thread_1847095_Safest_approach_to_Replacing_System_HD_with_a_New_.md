---
title: "Safest approach to Replacing System HD with a New one"
date: 2011-09-20
forum: Installation &amp; Upgrades
---

### Post by paulbuk on 2011-09-20
Hi folks,
I'm upgrading my Ubuntu comp with newer replacement of MoBo/Pro/Mem with faster ones this week and hence upgrading my old 'tiny' 80Gb with a WD 500Gb to compliment my 500Gb 'home' on current 2nd internal drive (both will be Western Digital - WD).

Would like to copy my current 11.04 system partition to the future new 500Gb system HD as quickly as I can after backing up my SQL D/Bs today so it's 100% the same but on a BIGGER beast!

Anyone advise on quickest, safest route or point me to a tutorial?
Thanks in advance.

Paul B

---

### Post by dino99 on 2011-09-20
nothing better than a fresh install (30 min done :) via net-install)

---

### Post by YesWeCan on 2011-09-20
> **paulbuk said:**
> Hi folks,
I'm upgrading my Ubuntu comp with newer replacement of MoBo/Pro/Mem with faster ones this week and hence upgrading my old 'tiny' 80Gb with a WD 500Gb to compliment my 500Gb 'home' on current 2nd internal drive (both will be Western Digital - WD).

Would like to copy my current 11.04 system partition to the future new 500Gb system HD as quickly as I can after backing up my SQL D/Bs today so it's 100% the same but on a BIGGER beast!

Anyone advise on quickest, safest route or point me to a tutorial?
Thanks in advance.

Paul B
The quickest way is to clone the old to the new using dd. Boot from a live CD/USB and run:

```
sudo dd if=/dev/sdx of=/dev/sdy bs=64k conv=notrunc,noerror
```

Where x=letter of 80GB old drive and y=letter of 500GB new drive. [COLOR="Red"]Caution: do not get the drives mixed up or you'll lose your data.[/COLOR]  This will trash any existing data on sdy.
It will show no progress and will take quite some time, maybe an hour.

After it finishes, you will have two drives that look identical. So it is very important not to try to boot one when the other is still connected. This causes problems because the boot programs will be confused about which partitions on which disks to use.

After the cloning I would disconnect the 80GB and then check the 500GB boots ok and then shutdown, reconnect the 80GB and boot from live CD and reformat the 80GB drive.

---

### Post by paulbuk on 2011-09-20
> **YesWeCan said:**
> The quickest way is to clone the old to the new using dd. Boot from a live CD/USB and run:

```
sudo dd if=/dev/sdx of=/dev/sdy bs=64k conv=notrunc,noerror
```

Where x=letter of 80GB old drive and y=letter of 500GB new drive. [COLOR="Red"]Caution: do not get the drives mixed up or you'll lose your data.[/COLOR]  This will trash any existing data on sdy.
It will show no progress and will take quite some time, maybe an hour.

After it finishes, you will have two drives that look identical. So it is very important not to try to boot one when the other is still connected. This causes problems because the boot programs will be confused about which partitions on which disks to use.

After the cloning I would disconnect the 80GB and then check the 500GB boots ok and then shutdown, reconnect the 80GB and boot from live CD and reformat the 80GB drive.
Thanks guy, that's very helpful. Presume the new MoBo/CPU (Gigabyte M68MT-S2P/AMD X2 260) won't be tempermental about the new system drive (i.e the WD 500Gb), unlike M$ upgrades used to be?
The 80Gb is really an older IDE and I'll have 2 * WD 500Gb (along with the 4Gb Ram yippee!) so the 80Gb will go down to the charity shop as even my music comp will eat that in 5 on audio!!! tehe. 

Someone also did mention "[CloneZilla]("http://clonezilla.org/")" as a utility. Any comments on using that or is the live CD just as useful?
Cheers,

Paul B

---

### Post by Shazaam on 2011-09-20
Clonezilla has a live cd also.
Most of the diferent apps are basically frontends for the "dd" command (among other commands). Use whichever one you feel comfortable with. They ALL have a risk of data loss so read about/research each one.

---

### Post by paulbuk on 2011-09-23
Thanks Guys. I decided to take the plunge with [CloneZilla]("http://clonezilla.org/"), it worked flawlessly copying my old previous system drive of 9Gb used (80Gb capacity in total) to a new Western Digital 500Gb in about 10 minutes.
Then I turned off computer, unplugged the old IDE 80Gb drive and removed from machine; set the new 500Gb as the 'primary' boot in the BIOS settings, then switched back on and the computer was as the same as before but faster with the new MoBo/CPU. Real easy IMO.
The only issue I had was with my 'Home' which I had set on a 2nd 500Gb, but that had nothing to do with the cloning process and once both drives were connected worked so easy. And, I never lost any data.

For novices, CloneZilla is great. But AGAIN USER BEWARE! pay attention and WATCH which drives you clone, carelessness may cost you data if you don't focus on the job!!

Thanks,

Paul B

---

### Post by paulbuk on 2011-09-24
Hi people,
Just a follow up and keen on your own opinions for next move.

After successfully cloning the old IDE 80Gb drive to a new SATA 500Gb (and then removal of the old 80Gb), I noticed with GParted that I currently have some circa 389Gb 'unallocated', (I can quite easily sort this kind of thing out having done it many times with M$) but don't really want to trash my MBR or GRUB.

My new system partition has 89Gb which I'm sure is well sufficient for the system/swap file etc, and could quite easily just make a new partition with the 389Gb but me thinks I'd rather have a one 'large' partition.
(FYI, my 'home' is already set on the second 500Gb (both SATA drives are the same model, so I'm not really bothered).
I am currently upskilling in LAMP/Drupal WebDev and work a lot on localhost for playing on WebDev etc and I'm sure 89Gb is well enough for many many SQL D/B's.

If GParted is not the best approach, can someone advise on the safest, quickest route to 'merge' the 89Gb with the unallocated 389Gb into one partition without destroying my MBR or Grub on the current 89Gb.

I'm keen to hear your advice on partition layout or best practice.

I've attached a GParted png for you to view and I'm sure the opinions will help others in future make positive decisions.

Thanks again.
(:

Paul B, Lancs.

---

