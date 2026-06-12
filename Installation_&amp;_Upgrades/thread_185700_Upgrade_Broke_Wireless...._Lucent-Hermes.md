---
title: "Upgrade Broke Wireless.... Lucent-Hermes"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by conro on 2006-06-01
I have a Lucent HERMES 802.11b integrated wireless on my acer travel book c100 tablet PC that i just finished upgrading to dapper from breezy.  

After the install my wireless card stopped working. 

iwconfig:
```

lo                 no wireless extensions
sit0              no wireless extentions

```

and lspci doesn't show my wireless card. it is an internal card, not pcmcia. 

the way that my network cards work is kind of dumb. you can choose to use either the wired or wireless card by pressing a button, but you can't have both running at the same time. the problem is that in order to switch interfaces in linux you need to reboot the computer and hit the button before it gets to the grub screen. 

(every thing that i have read about my particular laptop running any distribution/kernel version has said that the interface can only be switched at boot)

if i boot up with my wired network card everything works ok..

---

### Post by conro on 2006-06-01
hmmm... if i reboot and select the breezy kernel (2.6.12) from the grub menu my wireless works, but the sound is borked.. 

so it would appears to be a problem with the new kernel... ?

---

### Post by nkbj on 2006-06-01
Which driver do you use for wireless in breezy?

Regards,
Niels Kristian

---

### Post by conro on 2006-06-01
ok, so i fixed it...

first of all, turns out my wifi card is a pcmcia card even though it is built into the computer. 

the problem was that breezy's pcmcia manager is not compatable the dapper kernel, and for some reason it was not updated when i did apt-get dist-upgrade. 

a simple ```

$ sudo apt-get install pcmciautils

```
got my card recognized, then i just added eth1 to my /etc/networking/interfaces file

and now everything works.

---

