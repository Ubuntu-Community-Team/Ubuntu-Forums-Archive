---
title: "Installed Swap Partitions"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by Gregory@Feanor on 2008-04-25
So I installed xubuntu (dual booted with Win XP) yesterday using uNetBootin (since I have no optical drive on my laptop) and really loved it. But later on that day I managed to totally goose it by trying to install a package ...long story. Anyway, I couldn't fix it so decided to reinstall xubuntu and thought deleting the xubuntu partition was the way to go.

Then I realised I had a swap partition. I have no idea if this was made for the deleted xubuntu or for Win XP (which can hibernate).

Now I'm trying to reinstall xubuntu using uNetBootin. I've got to the partitioning section and it appears that it is trying to create another swap partition.

I don't want a redundant partition on my hardrive but I really don't know how to fix it. Should I delete the first swap partition? Should I try to install xubuntu without allowing it to make another swap partition? Or should I install xubuntu with the extra swap partition and try to sort it all out using xubuntu?

---

### Post by Partyboi2 on 2008-04-25
You can choose the manually partition option and keep the old swap and tick on the ext3 partition (your old xubuntu installation) to format. This should reinstall xubuntu to the same  partition.

---

### Post by Gregory@Feanor on 2008-04-26
Ah yes, I have reusued the old swap partition by changing the "use as" to "swap" and not "do not use" while doing manual partitioning. I've also reformatted the free space as ext3 and used that for the xubuntu partition.

My question is though - can windows use the swap partition assigned to xubuntu when hibernating? Will there be any conflict sharing between the two OSs? Does windows automatically detect it or do I have to manually tell it where it is?

Thanks

---

