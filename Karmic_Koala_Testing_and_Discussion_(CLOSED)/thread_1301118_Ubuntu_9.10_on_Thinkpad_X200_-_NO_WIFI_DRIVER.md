---
title: "Ubuntu 9.10 on Thinkpad X200 - NO WIFI DRIVER?"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by LebSoLjah on 2009-10-25
Hi, I'm making the switch but the problem I'm experiencing is making me regret installing Ubuntu.

WIFI does not work. It seems that there isn't any compatible drivers. 

In Windows, the card is recognized as:

**ThinkPad 11b/g/n Wireless LAN Mini-PCI Express Adapter II**


I've searched everywhere and there isn't any clear solution for this.

Any help would be greatly appreciated.

Thanks

---

### Post by earthpigg on 2009-10-25
hi,

[this guy]("http://justinsomnia.org/2008/09/getting-wireless-to-work-in-ubuntu-on-a-lenovo-thinkpad-x200/") said wifi was problematic for him in 8.10, but [worked out of the box in 9.04]("http://justinsomnia.org/2009/04/ubuntu-904-first-impressions/") on that hardware -- have you tried a 9.04 LiveCD? [software regressions]("http://en.wikipedia.org/wiki/Software_regression") in ubuntu are not unheard of.

---

### Post by LebSoLjah on 2009-10-25
Thanks for the reply

It's the same issue with 9.04 (installed) and the solution proposed on the site doesn't work, after reboot... (with the newest version of the driver)

---

### Post by LebSoLjah on 2009-10-25
lspci

03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

is it possible that this is my wifi card?



Edit: I just found threads discussing this and apparently there is no driver for it......

---

### Post by LebSoLjah on 2009-10-26
Found a possible solution.

[https://bugs.launchpad.net/ubuntu/+bug/401126](https://bugs.launchpad.net/ubuntu/+bug/401126)

It can now recognize the wireless card but can't find any APs. I spent 8 hours on this and I give up (typical linux scenario). I will switch back to Windows once again.

---

### Post by earthpigg on 2009-10-26
hi,

unfortunate that ubuntu did not work out for you on that computer.

since you clearly may end up switching later on the line, consult this list before purchasing a computer in the future -- even if you intend to run windows on it, you may as well leave your options open, right? :D

the list:
[https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)

---

### Post by thecow on 2009-10-26
Thats interesting to note though, I thought Lenovo just used the standard Intel wifi chipsets

---

### Post by Kokopelli on 2009-10-26
Bad luck, the thinkpad card is the only one (of 4) offered on the X200 that does not work out of the box.  Thinkwiki.org points to the same thread about using the NDIS wrapper.

You could buy and install one that works ($40 on amazon).

I am on an X200 tablet right now and everything (including wireless) works beautifully for me.  So perhaps wireless will be your last hurdle,

---

### Post by autocrosser on 2009-10-26
I install the Philips (atheros) or Intel 2200 a/b/g cards in the ThinkPads I refurb--I'm using a Philips card in my T42 & after un-blacklisting my ath5 driver it works very well...You can get the cards on eBay for $10 to $20US.....

---

### Post by LebSoLjah on 2009-10-28
This is the exception because I know that Ubuntu works with most hardware. 

Thanks for the help and Good Luck with the release. Flash works perfectly now.

---

### Post by P4man on 2009-10-28
Doesnt it work with the windows drivers using ndiswrapper?
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

