---
title: "Unable to format to ext4"
date: 2010-08-06
forum: Installation &amp; Upgrades
---

### Post by nikoskoutr on 2010-08-06
Hello, i recently bought a new pair of rams, after i installed them (removed the old ones) ubuntu started lagging and all my applications started normaly, after half a minute they didn't respond for 2 minutes and then back to normal again. So i decided to delete the ubuntu partition and re-install ubuntu. I begin the installation normaly but it stucks at 5% where the partitioning takes place. I also tried gparted to create an ext3 and ext4 partitions but i had the same problem on both tries. I believe it is a ram problem, should i go and replace them, or there is a possible solution without replacing them? (Also run the memtest 86+ for 4 hours and there were no errors).

The ram i bought:   [http://www.newegg.com/Product/Product.aspx?Item=N82E16820231209]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820231209")

Thanks in advance.

---

### Post by oldfred on 2010-08-07
Does BIOS see RAM ok. Since it is dual channel did you install per your motherboards instructions. Some require dual channel in same color slots (or alternating slots), other wise it only sees part of memory. I would remove & reinstall, perhaps contacts are dirty, new memory should be ok but slot may have accumulated some dirt or oxidation if not used before.

---

### Post by nikoskoutr on 2010-08-07
Thanks for the reply,
I have tried putting my ram cards with both (same color) combinations. After that i tried to install ubuntu with just one ram and i still had the same problem. Now i tried installing ubuntu with my old ram and it went good. So i guess ill need to change the new ones, what troubles me though, is that my windows 7 partition runs fine without any problems. Do you think a bios upgrade could fix this problem ?

---

### Post by oldfred on 2010-08-07
Some say do not upgrade BIOS unless you have a problem they list that is fixed with the new version as you might create new problems.

I have always update just to be up to date and never had problems. I am surprised that memory works in windows and not in Ubuntu.

---

### Post by nikoskoutr on 2010-08-08
I updated my bios and i still have the same problem.
I guess i'll go change them at the shop (or ask if they have any idea how to fix this).
If you think i should try something else, let me now. :D

---

### Post by Ginsu543 on 2010-08-09
Have you changed the appropriate settings in your BIOS to make it compatible with your new ram? I noticed that the G.Skill takes 1.8V-1.9V. Is the ram voltage setting in your BIOS set to those values? How about the FSB speed? Is your motherboard FSB running at or below 400 MHz?

---

