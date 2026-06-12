---
title: "Trouble installing Ubuntu (GTX960M?)"
date: 2016-01-19
forum: Installation &amp; Upgrades
---

### Post by rutiolma on 2016-01-19
I'm having some problems installing ubuntu on a W230SD Clevo computer.

I boot using a USB stick and sometimes it goes to the live install and freezes after a couple of minutes, sometimes it starts loading ubuntu and just restart (it's all random). When on live CD, the only way to prevent the computer to freeze after a while is doing a CTRL + ALT + F1 and use the terminal only. Going back to GUI instantly freeze the computer (I already waited hours and it doesn't unfreeze).

I already did some few installs in the past but now I'm having the same problem on this laptop with a nvidia GTX 960M and I guess that's the problem.
I tried 2 different Ubuntu 15.10 ISO's (to make sure it wasn't a corrupted ISO), Ubuntu 14.03 and some Ubuntu Flavours.

Someone know a solution? I googled with no luck.
Maybe another distro more up to date or with better drivers for the GTX960M by default?

---

### Post by rutiolma on 2016-01-20
Ok, so I just booted with the "nomodeset" option and it worked!
After install, I just added the option on GRUB and all looks fine.

---

### Post by mörgæs on 2016-01-20
Good, please mark the thread 'solved'.

---

