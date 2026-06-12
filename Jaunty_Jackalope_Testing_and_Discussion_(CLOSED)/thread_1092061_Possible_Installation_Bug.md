---
title: "Possible Installation Bug"
date: 2009-03-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by CarlAndrews on 2009-03-10
I have been fortunate to recently aquire an Acer Aspire One (8G SSD) and have installed both Jaunty and Intrepid many times and with the same results for both the production and development versions.

During the install if I select the option for guided use entire disk when the option to partition the installation drive appears the swap partition created is around 350M. This does not pose any operational issues but if I attempt to hibernate or suspend the computer seizes up. I have even performed installs with both Jaunty and Intrepid after erasing the partition table on the SSD (no partition table exists at the time of the install) with the same final results.

If I install and manually create the partitions, specifically creating a swap partition larger than RAM, then the suspend and hibernate functions work as expected. Now I suspect the installation process checks the installation drive and makes decisions on swap space depending on the installation target. Since my target drive is 8G and a 2G swap would be a quarter of the available space it is possible the logic is to create a smaller swap.

I realize SSDs are not bleeding edge technology but it took me 5 format/installs and many PM_DEBUG logs to finally conclude that this was a swap issue so maybe I can help to prevent someone else from having the same problem ... assuming this is not isolated to just me :->

Now my question is, does anyone else believe this to be a bug or other issue and if so is it one of the "installer" or "pm-utils"?  I have posted the same information on the pm-utils newsgroup and think pm-utils should gracefully handle insufficient swap but also see that this could be avoided at installation so is this a bug or a feature request and who should it go to?

Thanks,
Carl

---

### Post by superJoel on 2009-03-10
have you checked out this pretty informative community documentation for the aspire one yet?  I read about the suspend issues there associated with not having a swap partition.  check it out... hope it helps.

... [https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne")

---

### Post by nyarnon on 2009-03-10
> **CarlAndrews said:**
> I have been fortunate to recently aquire an Acer Aspire One (8G SSD) and have installed both Jaunty and Intrepid many times and with the same results for both the production and development versions.


As an eeepc user I strongly disagree :-) <-- smiley!!!

> **CarlAndrews said:**
> 

Now my question is, does anyone else believe this to be a bug or other issue and if so is it one of the "installer" or "pm-utils"?  I have posted the same information on the pm-utils newsgroup and think pm-utils should gracefully handle insufficient swap but also see that this could be avoided at installation so is this a bug or a feature request and who should it go to?

Thanks,
Carl

I think the whole automatic partition procces could do with an overhaul. I would very much propose automaticly giving /home it's own partition f.i.

As to your specific situation I would suggest rethinking swapspace on a sdd. As we all know sdd's don't like many writes and this is exactly what swap will do. This is one of the reasons that I never would go for a laptop with internal sdd.

IMHO the automatic installer should ask before placing a swap on an sdd.

---

