---
title: "install hardy on my acer aspire 5570"
date: 2008-09-16
forum: Installation &amp; Upgrades
---

### Post by antonferdinand on 2008-09-16
hi all,

today i try to install hardy-desktop on my acer aspire 5570
the instalation was succeed but why i cannot connect my ubuntu to my LAN on my office. i setup the IP from /etc/network/interfaces
but when i try to chek my ping to my gateway .. the result is "unknown host". so i hope someone can help me ?

---

### Post by manishtech on 2008-09-16
NIC model? Get it through

```
lspci | grep -i network
```

Can you provide us with more information about your office network?

---

### Post by antonferdinand on 2008-09-16
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


thx finally i can connect to LAN.

---

### Post by manishtech on 2008-09-17
You can connect to LAN now? If its so then its good.

And as far as your wi-fi is concerned, its Intel 3945 chipset which has iwl3945 open source driver provided by intel itself. So wi-fi would work flawlessly out of box on your system.

If you had heard that wi-fi is one of the most troublesome thing in Linux, since most of the wireless vendors dont provide linux drivers. So wifi is achieved by using ndiswrapper which emulates windows wireless drivers on windows. Quite complicated. You are free from all such hassles. Inte; has its open source driver division which makes excellent drivers for linux too. I am also having the same wireless chipset.

---

### Post by Jarethc on 2009-08-05
I have the same problem

I have:
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

any ideas how i could get it working?
worked.it worked with ubuntu 9.04 so i changed to 8.04 because other stuff didnt work but now wireless doesnt work.

---

