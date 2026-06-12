---
title: "Improved mobile broadband and PAN support for Karmic?"
date: 2009-07-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-07-19
Any chance of this getting in?

[http://blogs.gnome.org/dcbw/2009/07/10/unwire-with-networkmanager/](http://blogs.gnome.org/dcbw/2009/07/10/unwire-with-networkmanager/)

---

### Post by taavikko on 2009-07-19
that would really be something sweet to use bluetooth and mobile phone in conjuction, to gain access to network.

isn't networkmanager0.8 supposed to bring this goodness?

---

### Post by plun on 2009-07-19
I dont think that ver 0.8 will be in but "asac" has a test ppa running with the trunk

[https://launchpad.net/~network-manager/+archive/trunk](https://launchpad.net/~network-manager/+archive/trunk)

I needed it for a USB mobile connection which failed with ver 7.1.

Going to test blutooth....:D

---

### Post by Starks on 2009-07-19
I recall that the basic functionality for one-click CDMA/GSM DUN over BT (provided the device was paired) was present in Jaunty (and perhaps even Intrepid?).

---

### Post by plun on 2009-07-19
> **Starks said:**
> I recall that the basic functionality for one-click CDMA/GSM DUN over BT (provided the device was paired) was present in Jaunty (and perhaps even Intrepid?).

Not with standard gnome as I recalls it.

We needs a newer trunk-build for bluetooth support, no option for mobile support is available, just tested it.

---

### Post by Starks on 2009-07-19
plun, that doesn't sound right.

I remember in Jaunty that I could pair my phone (automagically or manually) and then have drop-down BT DUN access. Am I mistaken or am I thinking of USB DUN?

---

### Post by dudude on 2009-07-19
I don't know about DUN, since the phone I have been using does not have the capability, but I know to get bluetooth PAN support in Jaunty (and presumably Karmic) I could use Blueman.

I would also have to install the 'bluez-compat' package to get 'pand' to do the connections with.

I don't know what the proper way of connecting to a PAN is now since the 'bluez-compat' description says that the 'pand' binary is not supported any more.

---

### Post by xens on 2009-08-10
I read somewhere that karmic will ship blueman as bluetooth manager, is it true?

---

