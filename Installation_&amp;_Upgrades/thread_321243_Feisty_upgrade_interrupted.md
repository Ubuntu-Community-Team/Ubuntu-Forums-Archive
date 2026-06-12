---
title: "Feisty upgrade interrupted"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by MegaHz on 2006-12-18
Hi guys
I tried to gksu "update-manager -d"

but during the installation of the new packages, my computer restarted (due to an electricity failure) it shows a new version of the kernel in grub but it does not boot if I choose that. It shows the ubuntu splash screen but it does not move.

If i choose my old kernel it boot.

Today I sudo apt-get update and sudo apt-get dist-upgrade, it found another kernel, it installed it but again it does not boot if I choose the new one.

anybody can help? is there any solution or I should re-install 6.10?

thanks

---

### Post by ciscosurfer on 2006-12-18
> **MegaHz said:**
> Hi guys
I tried to gksu "update-manager -d"

but during the installation of the new packages, my computer restarted (due to an electricity failure) it shows a new version of the kernel in grub but it does not boot if I choose that. It shows the ubuntu splash screen but it does not move.

If i choose my old kernel it boot.

Today I sudo apt-get update and sudo apt-get dist-upgrade, it found another kernel, it installed it but again it does not boot if I choose the new one.

anybody can help? is there any solution or I should re-install 6.10?

thanksI am going to suggest that [you first read this post]("http://ubuntuforums.org/showthread.php?t=306424").  And then I suggest you reinstall 6.10 unless you are a developer or tester or willing to deal with these sorts of issues on a daily basis.  Feisty is not ready for public consumption quite yet. :D

---

### Post by wpshooter on 2006-12-18
I wholeheartedly agree.

I have not even been able to get Feisty to boot correctly to the desktop with a functional mouse cursor.

I think this has a ways to go before anyone can even begin thinking about doing any testing on it.

---

### Post by d3v1ant_0n3 on 2006-12-18
> **wpshooter said:**
> I wholeheartedly agree.

I have not even been able to get Feisty to boot correctly to the desktop with a functional mouse cursor.

I think this has a ways to go before anyone can even begin thinking about doing any testing on it.

I've been using it for a couple of weeks now with no major failures I haven't been able to slog through. And the slogging is half of the fun. 

However, at this point I would say that Feisty is far from stable, and just running it for the sake of it isn't to be taken too lightly. Breakage WILL occur with frequency.

---

