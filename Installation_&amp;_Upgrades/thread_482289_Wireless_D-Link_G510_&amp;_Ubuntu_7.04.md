---
title: "Wireless D-Link G510 &amp; Ubuntu 7.04"
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by jimb1939 on 2007-06-23
Hi,
This is my first post and I am new to Linux and Ubuntu. I have used DOS and Windows from 3.1 to Media Center 2005.
Wanted to try Linux on my old computer as I watch Leo on Call for Help & The Lab with Leo and they think it is a good OS.
Downed loaded Ubuntu 7.04 and installed on second HD. I tried for two days to get connected to the internet with my D-Link G510 wireless card.Error unsupported driver (Atheros Hardware Access HAL)    Searched tis forum and read many posts but failed to find a solution. Also tried to use ndiswrapper to install windows driver but could not follow the instructions to install.
Then I removed 7.04 and downed loaded Ubuntu 6.06 (Dapper Drake). Installed to second HD and was connected to the internet on the first try. Works great!!

Why did my wireless card work with 6.06 and not with the newer 7.04?
What are the advantages or differences between the two?

Thanks

---

### Post by jpeddicord on 2007-06-25
I (used to) have that card, and the reasoning behind it working in 6.06 is that it used the "madwifi-old" interface, instead of the newer "madwifi-ng" one. The card has a lot of trouble working with the NG drivers, but always worked fine with the "old" ones. :?

Jacob

---

### Post by jimb1939 on 2007-06-26
Thanks. I will stay with 6.06 until I get a wireless card that works with 7.04.

---

### Post by AndyCinDallas on 2007-06-26
I have a D-Link DWL-G650 Airplus - it worked immediately in 7.04 but not in 6.06 ;)

---

### Post by mercerm on 2007-06-28
Is there a known fix for this? I just wiped out my computer and installed 7.04. i really don't want to have to go back to 6.10. My card is pretty new, it's a D-Link DWA-552.  It worked great in 6.10. 


Thanks

---

### Post by Stoffer on 2007-08-09
I have a DWL G510 and it worked "out of the box" with Ubuntu 7.04.  It only reports half the signal strength as it did under Windows, but it definitely works with what I suppose is the default Gnome wireless manager.

Don't let that card prevent you from switching to 7.04.  It works automatically.  The linux driver it's using is ath_pci.

Note:  More specifically, my card is Rev. B.  I've read that Rev. A&C use different chipsets.

---

