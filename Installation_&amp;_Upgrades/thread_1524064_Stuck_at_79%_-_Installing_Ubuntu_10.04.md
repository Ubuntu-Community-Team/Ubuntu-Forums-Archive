---
title: "Stuck at 79% - Installing Ubuntu 10.04"
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by haran_hockey on 2010-07-04
I ran the installation - shrunk my xp partition during installation and during the progress, it just hangs at 79%. I looked it up on google quickly and it seems like other people get the same problem. But I wanna make sure my hardrive won't get messed up because of the new partition.

I also have an old ubuntu cd (8.04) so can I restart my laptop, run the 8.04 installation, and then update to 10.04 from there?

I just wanna make sure my partitions aren't messed up if I manually turn off my laptop while it's installing.

---

### Post by Souptik on 2010-07-04
Please check whether the internet connection was on at that time or not. If it is, please switch off the modem. I myself faced the same problem at installation and came out of it by turning off the modem. Hope this helps....

---

### Post by haran_hockey on 2010-07-04
I'm on wireless, so the wifi stick is plugged in... so should I just take it out?

There's also a button in the lower left corner that says skip, but when I click it, nothing happens.

---

### Post by Theft42 on 2010-07-04
Go ahead and try unplugging the wireless.. I have seen it work a few times and others not.. But I wish it luck and hope it works.

---

### Post by haran_hockey on 2010-07-04
Ok so it's still stuck at 79%. So should I manually turn off my laptop... like is it safe :|

---

### Post by Marlonsm on 2010-07-04
Around 80% is when the installer downloads the language packs, so it usually freezes there for a while if you have a working internet connection. I'd advise either try again without connecting, as you can download those packs later, or just wait...

---

### Post by haran_hockey on 2010-07-04
Ok, so I started up the installation again, no internet. When I got to the partitioning part, I left my xp partition untouched.

I deleted the ext4 and swap partition. The in the empty space, I clicked add:

They have a few things there, logical, beginning of partition, ext4, but where it says Mount point, I'm not sure what to put.

Also, after I do that ^, do I need to make a swap partition? Or can I make the swap partition after install using GParted or something?

---

### Post by darkod on 2010-07-04
For the main system partition the mount point is /. Whether you select primary or logical depends on your plan and your current hdd layout but usually it's better to create them as logical.
Yes, you need to create also swap partition during the install so it gets included in the install. Later it's more complicated.

PS. Stopping the install might also mean bad cd. That can be from bad burning or maybe the ISO downloaded is corrupted. To try with a new cd, burn another one not faster than 4x. For a new image, download with torrent because it checks for corruption during download.

---

### Post by haran_hockey on 2010-07-06
I burned a new cd just incase, and during installation, I chose to format everything and just make Ubuntu take up everything. But the installation is taking forever... How long should the installation take?

---

### Post by Marlonsm on 2010-07-06
> **haran_hockey said:**
> I burned a new cd just incase, and during installation, I chose to format everything and just make Ubuntu take up everything. But the installation is taking forever... How long should the installation take?

The install time really depends on the computer, I say it shouldn't exceed one hour, but I've already seen it finishing in 15 mins.

---

### Post by haran_hockey on 2010-07-07
Something is wrong with my laptop first of all - I think it's too hot so it took a couple (that's being generious) hours just to get to 79%. I left it overnight, and still at 79%. I believe this is the downloading language fiels part but I can't skip it. When I press the skip button, nothing happens, and wifi won't work because I have to put in the password. So anyone know a way so I can put in the wifi password or somehow skip this stupid laguage files thing?

EDIT: SOLVED

I ran another clean installation with internet, and flipped my laptop over so it wouldn't heat :P

---

### Post by srijit92 on 2010-10-15
[SIZE=4]**This problem is not solved even after switching off all network..... The Ubuntu Installation stuck at 79% and does not progress after that. Please Help!!**[/SIZE]

:confused::confused::confused::confused::confused:

---

