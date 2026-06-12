---
title: "Upgrade dual boot from WinXP to Win7 HP"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by RealGomer on 2010-12-20
Current set-up:
Athlon 64 2800
2 GB RAM
340 GB on two HDD
Ubuntu 10.04 LTS
Win XP Pro SP3

After getting the Silver Ghost all set up and purring like a kitten for my daughter, she now informs me she'd rather have Win7 HP instead of Win XP Pro SP3. Ubuntu and Win XP Pro are on separate HDD. Can I do a "clean install" of Win 7 HP on the Windows drive without screwing up GRUB? Or will I need to do the dance described at [http://ubuntuforums.org/showthread.php?t=1647103&highlight=install+windows](http://ubuntuforums.org/showthread.php?t=1647103&highlight=install+windows). I've had to modify Ubuntu because of conflicts between 10.04 and the Ralink 2780 (?) wireless-n drivers.
Thank you.

---

### Post by wilee-nilee on 2010-12-20
> **RealGomer said:**
> Current set-up:
Athlon 64 2800
2 GB RAM
340 GB on two HDD
Ubuntu 10.04 LTS
Win XP Pro SP3

After getting the Silver Ghost all set up and purring like a kitten for my daughter, she now informs me she'd rather have Win7 HP instead of Win XP Pro SP3. Ubuntu and Win XP Pro are on separate HDD. Can I do a "clean install" of Win 7 HP on the Windows drive without screwing up GRUB? Or will I need to do the dance described at [http://ubuntuforums.org/showthread.php?t=1647103&highlight=install+windows](http://ubuntuforums.org/showthread.php?t=1647103&highlight=install+windows). I've had to modify Ubuntu because of conflicts between 10.04 and the Ralink 2780 (?) wireless-n drivers.
Thank you.


Don't worry about grub or the windows bootloaders they can be put back into the MBR master boot record with ease.

Do this though if you want a complete look at your setup.
click on the bootscript in my link, for your own use it is quite handy. You can post the text from the generated file if you like. If you post the text open a reply and click on the # in the reply panel and paste the text between the code tags.

---

