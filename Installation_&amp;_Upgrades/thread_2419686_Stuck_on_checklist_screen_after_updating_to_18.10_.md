---
title: "Stuck on checklist screen after updating to 18.10 from 18.04 LTS"
date: 2019-05-24
forum: Installation &amp; Upgrades
---

### Post by jarebare457 on 2019-05-24
AMD Ryzen 5 2600 and GTX 1060
Dual-Booting Ubuntu and Windows 10

I tried updating to 18.10 from 18.04 LTS earlier today. I followed the instructions, everything got ready to install. I hit the prompt asking to reboot to finish the update. When I booted in, I was greeted by this screen [ATTACH=CONFIG]283313[/ATTACH]  and waited for about 30 minutes and nothing happened. I eventually restarted the pc and booted into recovery mode. It got me a bit farther into the checklist, but still didn't bring me to the desktop. I got my live USB and booted off of that, went through the boot fix tool, here's the pastebin [http://paste.ubuntu.com/p/mCt986xj7]("http://paste.ubuntu.com/p/mCt986xj7h")h. It didn't solve anything. I don't know what to do, if I should install a fresh version of Ubuntu or what?

---

### Post by again? on 2019-05-24
Did you remove the nvidia driver before install?
Do you get to the grub menu?

---

### Post by jarebare457 on 2019-05-24
I get to the grub menu, and am able to select what OS I want to use, but once I select Ubuntu the problems listed start. I didn't remove the nvidia drivers before updating.

---

### Post by again? on 2019-05-24
At the grub menu, use ctrl+alt+F1 to access a tty. (May be F2 -F7)
Login and run...
```
sudo apt purge nvidia*
```

When finished ...
```
reboot
```

---

### Post by jarebare457 on 2019-05-24
Will try. Thanks in advance!

---

### Post by jarebare457 on 2019-05-24
Thanks from Cosmic Cuttlefish. Time to upgrade to Disco Dingo _***Without Nvidia Drivers***_

---

### Post by again? on 2019-05-24
I tend to stick to LTS releases these days unless there are dramatic changes.

_End of Life (days)_
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] distro-info --all -rf --days=eol**
Ubuntu 4.10 "Warty Warthog" -4773
Ubuntu 5.04 "Hoary Hedgehog" -4589
Ubuntu 5.10 "Breezy Badger" -4425
Ubuntu 6.06 LTS "Dapper Drake" -3602
Ubuntu 6.10 "Edgy Eft" -4047
Ubuntu 7.04 "Feisty Fawn" -3870
Ubuntu 7.10 "Gutsy Gibbon" -3689
Ubuntu 8.04 LTS "Hardy Heron" -2935
Ubuntu 8.10 "Intrepid Ibex" -3312
Ubuntu 9.04 "Jaunty Jackalope" -3136
Ubuntu 9.10 "Karmic Koala" -2948
Ubuntu 10.04 LTS "Lucid Lynx" -2207
Ubuntu 10.10 "Maverick Meerkat" -2601
Ubuntu 11.04 "Natty Narwhal" -2400
Ubuntu 11.10 "Oneiric Ocelot" -2207
Ubuntu 12.04 LTS "Precise Pangolin" -759
Ubuntu 12.10 "Quantal Quetzal" -1835
Ubuntu 13.04 "Raring Ringtail" -1944
Ubuntu 13.10 "Saucy Salamander" -1773
Ubuntu 14.04 LTS "Trusty Tahr" -30
Ubuntu 14.10 "Utopic Unicorn" -1402
Ubuntu 15.04 "Vivid Vervet" -1218
Ubuntu 15.10 "Wily Werewolf" -1037
Ubuntu 16.04 LTS "Xenial Xerus" 697
Ubuntu 16.10 "Yakkety Yak" -674
Ubuntu 17.04 "Zesty Zapus" -497
Ubuntu 17.10 "Artful Aardvark" -310
Ubuntu 18.04 LTS "Bionic Beaver" 1432
Ubuntu 18.10 "Cosmic Cuttlefish" 54
Ubuntu 19.04 "Disco Dingo" 238
Ubuntu 19.10 "Eoan Ermine" 419
```

---

