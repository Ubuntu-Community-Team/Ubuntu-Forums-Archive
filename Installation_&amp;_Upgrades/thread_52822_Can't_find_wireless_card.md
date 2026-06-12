---
title: "Can't find wireless card"
date: 2005-07-29
forum: Installation &amp; Upgrades
---

### Post by rmorgan1016 on 2005-07-29
Hello, and thanks in advance for reading this.

I'm completely new to Linux, and am installing it dual-boot mode on a PC otherwise running WinXP Home.  I downloaded the ISO image, burned it to CD, and went through the partitioning and installation process.  Very smooth it was, too, at least for the most part.  Everything seemed to install just fine....except for my wireless network card.

Ubuntu found my Ethernet card and configured it, which is great except it's not plugged in to anything.  I have a Linksys 802.11g wireless card that the PC uses for Internet connectivity.

From the desktop, I went to System -> Administration -> Networking, and entered my password when prompted.

Two connections are shown in the Connections tab.  They are my modem and my Ethernet card.  The Help section says that to add a connection, you use Add in the Connections windows, but there is no Add, only Properties, Activate, and Deactivate.

In searching the forums I found some threads on wireless cards that use Broadcom chips, but I don't think my card has those.

So, how do I find the Add button and find my wireless card?  I'm on a home networking using DHCP through a Linksys wireless router, so I don't think it's a DNS problem, although at this point I have to admit I don't know what it is.

Thanks to any who can offer a suggestion.

Randy

---

### Post by rmorgan1016 on 2005-07-29
And one more thing....I don't seem to be able to boot into Windows.  When I shutdown and restart the system I get the HP splash screen, and then LILO starts loading Linux....shouldn't I be asked which o/s I want to boot?  I mean, I'm excited about learning Linux and all, but I really do need to get Windows to boot.

Thanks again.

---

### Post by strikeforce on 2005-07-29
Push your arrow key down and it should give you more options?

Thats re. getting back into windows.

---

### Post by rmorgan1016 on 2005-07-29
I tried holding down the down arrow key during boot, but it just beeped at me and then continued to load Linux after I released the key.

I thought there was something called Grub that should run before LILO, but I never see it.

I'm wondering if I should just re-burn the install CD again and start over, or at least boot from the install CD again and re-install the whole thing?  I don't have anything on the Linux partition yet that would can't be lost during a re-install.

---

### Post by rmorgan1016 on 2005-07-29
I did a fresh install and seem to have gotten Grub to install properly, because I can now boot to either Linux or Windows.  But, still no luck with the wireless card.

The solutions I've been able to find so far all seem to involve getting something and installing it, and the getting part is a little difficult since there's no internet connectivity.  The only errors during my last install all revolved around DHCP configuration, which I do use on my home network but ubuntu can't set up, presumably because it thinks I only have a wired enet card.

So, I'm wondering if the only way around this is to hook up my enet card to my wireless router, install again and hope ubuntu can get some internet connectivity so I can download whatever I need to download to make the wireless card work.

I'd be grateful for any other suggestion.

Thanks.

---

### Post by rmorgan1016 on 2005-07-29
AARGH.

My wireless card *does* have a Broadcom chipset, and I remember seeing how they don't support Linux, but that there's some tricky way to set things up.

Into the abyss I go...

---

