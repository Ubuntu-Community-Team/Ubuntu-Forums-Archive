---
title: "Problem with WUBI"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by kvalenza on 2010-11-29
I posted this to the Dell thread, but I got not responses at all. I hope you don't mind my reposting it here, but I am afraid this situation might happen again, and I want to know if anyone has an answer:

I have installed Unbuntu 10.10 on my Vostro 1720 three times in the last three weeks. I also downloaded kde so that I could use kde instead of Gnome. Each time Ubuntu was installed, everything worked fine for a while, but then something happened that required delete, then reinstall Ubuntu.

The first time I installed Ubuntu 10.10, after a few days my Windows 7 got corrupted . No matter what I did, including a system restore, nothing I did would allow Windows to boot normally I got numerous error messages when it would attempt to load.. So I reinstalled Windows 7 and deleted Ubuntu.

The second time, after getting everything to work (including sound) on Gnome and KDE, after a few days I was completely unable to boot Ubuntu. What followed was an endless loop when I turned on the computer. When I turned the computer on, the selection screen came up as always, but when I selected Ubuntu, the screen went blank, then the Dell boot screen came up as if I was rebooting, then the selection screen appeared again. Each time I chose Ubuntu, the same thing happened, over and over. Yet I was able to select Windows and boot it with no problem. So I completely deleted Ubuntu, and reinstalled it again yesterday using WUBI.

As of today, everything works fine, but who knows about tomorrow? It seems like I read somewhere that an Adobe program caused this. Should I completely stay away from all Adobe downloads? Does this mean I should not install Adobe flash drive for Youtube as well?

Is there any way I can prevent this from happening again? I thought Linux was supposed to be more stable than this.

---

### Post by Frogs Hair on 2010-11-29
Wubi installs Ubuntu inside Windows , so it's stability is partially dependent on Windows . The file system is not a real file system and therefore less stable . I encountered no problem with Adobe flash player when using Wubi. A Wubi installation is not intended for regular use , it is a means for Windows users to try Ubuntu/Linux.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by bcbc on 2010-11-30
> **kvalenza said:**
> I posted this to the Dell thread, but I got not responses at all. I hope you don't mind my reposting it here, but I am afraid this situation might happen again, and I want to know if anyone has an answer:

I have installed Unbuntu 10.10 on my Vostro 1720 three times in the last three weeks. I also downloaded kde so that I could use kde instead of Gnome. Each time Ubuntu was installed, everything worked fine for a while, but then something happened that required delete, then reinstall Ubuntu.

The first time I installed Ubuntu 10.10, after a few days my Windows 7 got corrupted . No matter what I did, including a system restore, nothing I did would allow Windows to boot normally I got numerous error messages when it would attempt to load.. So I reinstalled Windows 7 and deleted Ubuntu.

The second time, after getting everything to work (including sound) on Gnome and KDE, after a few days I was completely unable to boot Ubuntu. What followed was an endless loop when I turned on the computer. When I turned the computer on, the selection screen came up as always, but when I selected Ubuntu, the screen went blank, then the Dell boot screen came up as if I was rebooting, then the selection screen appeared again. Each time I chose Ubuntu, the same thing happened, over and over. Yet I was able to select Windows and boot it with no problem. So I completely deleted Ubuntu, and reinstalled it again yesterday using WUBI.

As of today, everything works fine, but who knows about tomorrow? It seems like I read somewhere that an Adobe program caused this. Should I completely stay away from all Adobe downloads? Does this mean I should not install Adobe flash drive for Youtube as well?

Is there any way I can prevent this from happening again? I thought Linux was supposed to be more stable than this.
don't upgrade packages grub-pc and grub-common. they break wubi installs.

---

