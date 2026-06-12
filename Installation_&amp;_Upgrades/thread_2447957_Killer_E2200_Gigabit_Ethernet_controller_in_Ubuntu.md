---
title: "Killer E2200 Gigabit Ethernet controller in Ubuntu 20.04"
date: 2020-07-29
forum: Installation &amp; Upgrades
---

### Post by mikaslayton on 2020-07-29
Hi there,

I have an 'MSI GT70 2PC Dominator' laptop and was tired of the poor performance with Windows 10.  Installed Ubuntu 20.04 and it runs like a dream, but the network card doesn't seem configured.  Network card is a Killer E2200 Gigabit Ethernet controller.  I've searched through the forums and I saw some related threads, but haven't found specific instructions for what to do on Ubuntu 20.04.  Could anyone lend me a hand?  

Thank you so much for the consideration

-- mika

---

### Post by mikaslayton on 2020-07-29
I feel it (the Killer e2200) is not properly configured, but the option for 'Wired Network' appears sporadically and is super slow, despite it reporting as 1000mb/s in the wired settings. 

Could it be due to me using powerline adapters?  I have my modem in another room and am using PLP2000 (Netgear Powerline adapters) to bring the internet to the back room.  

UPDATE:

After switching between wired and wireless several times in Ubuntu settings, I finally got a decent speedtest result.  Just about 100mbps.  Something seems unreliable though.  I have a Gigabit internet connection from Comcast and earlier today I was getting 5mbps on the same wired/Powerline connection in Ubuntu.  All webpages (20 different webpages) were loading super slow, too.  Speed seems intermittent...

---

### Post by CatKiller on 2020-07-29
> **mikaslayton said:**
> Killer E2200 

That's a Qualcomm (who have, at best, spotty support for Linux) Atheros with Killer's own non-standard stuff slathered over the top, which they specifically disclaim from supporting on Linux.

The easiest approach would be to get another adaptor that uses an Intel chip, which all support Linux well.

---

### Post by mikaslayton on 2020-07-29
Thank you for the kind and clear response.  I will get an adapter.  :)

---

### Post by gividen on 2021-02-02
Just downloaded ubuntu today. NO IDEA WHAT IM DOING.  Please clarify what an adapter is?

---

### Post by QIII on 2021-02-02
RIP.

Closed.

---

