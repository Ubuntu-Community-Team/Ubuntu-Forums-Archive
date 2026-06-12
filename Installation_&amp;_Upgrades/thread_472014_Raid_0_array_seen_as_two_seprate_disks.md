---
title: "Raid 0 array seen as two seprate disks"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by Zenerek on 2007-06-12
Greetings all

I've searched the net with google and lurked about the #ubuntu channel for awhile now,trying to get help with this problem with no luck,so i have decided to come here for your aid(not that i did attempt my own fixes of course)

I have a promise fasttrak tx2000 raid controller card, two seagate ata 100...i believe 150 gig drives are attached to it and i have set them up on a raid 0 array

when i go into gparted during the ubuntu install i see two disks,not the array which was created, i did a mock install of win2k to load the promise driver disk to see if it was a harware prob,but no the raid was detected fine

Have also tried alternate install method but seems to only have support for software raid(i have the dvd that came with a book)

So any ideas?

---

### Post by Pumalite on 2007-06-12
> **Zenerek said:**
> Greetings all

I've searched the net with google and lurked about the #ubuntu channel for awhile now,trying to get help with this problem with no luck,so i have decided to come here for your aid(not that i did attempt my own fixes of course)

I have a promise fasttrak tx2000 raid controller card, two seagate ata 100...i believe 150 gig drives are attached to it and i have set them up on a raid 0 array

when i go into gparted during the ubuntu install i see two disks,not the array which was created, i did a mock install of win2k to load the promise driver disk to see if it was a harware prob,but no the raid was detected fine

Have also tried alternate install method but seems to only have support for software raid(i have the dvd that came with a book)

So any ideas?

In my case at least, Feisty 7.04 did not support SATA Array 0. I had to install in another box with IDE drives.

---

### Post by Zenerek on 2007-06-13
I'll keep waiting for some help for a bit but if don't get any,i may have to change os prospects on my target system,pitty too, i wanted to see how ubuntu did on a cpu with more than twice the power of my test system.

Surley though there must be someone who knows somthing about hardware raid cards and ubuntu who can help me out, i mean this cards at least 4 years old, i'd expect ubuntu to be able to handle it and if ubuntu is to run on buisness type servers then it must be able to handle hardware raid setups.

The version i want to install on the system is ubuntu 6.06 dapper, i tried using some tool called mdadm .... or something like that, it's supposed to create raid devices out of the the hardrives you specify that can then be mounted

---

