---
title: "eee 901 networking broken"
date: 2009-03-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by nurbl on 2009-03-01
Hi,

after a big update a few days ago, networking (both ethernet and wlan) seems completely broken on my jaunty 901 eee. The network manager just disconnects after a little while with no error, and running dhclient manually doesn't work.

...
execve (/sbin/dhclient-script, ...): Permission denied
bound to 192.168.1.133 -- renewal in 94004 seconds

The IP address seems right, but it does not actually get bound to eth0.  My router is seeing it, so it does get a connection. I'm guessing the "permission denied" above has something to do with it not working.

I tried upgrading dhcp3-client again, but that did not help.

Any pointers?

---

### Post by cyclone5uk on 2009-03-06
Did you upgrade from Intrepid or is this a fresh install?

---

### Post by nyarnon on 2009-03-06
I'm running a 1000h if i'm not mistaking the same wireless. Updates didn't break anything here.

---

### Post by Father Marc on 2009-03-06
I have a 904ha and my networking is broken after an update a few days ago.

$ iwlist wlan0 scan... gives me results, but they only show one or two networks available at very low quality, while dual-booting into my 8.10 partition finds every network fine.

My home network, which should be very high quality in 9.04, doesn't ever show up.

I'm at a loss as to what the problem might be, since the card shows up, but doesn't function properly after the update... before the update it worked normally.

---

### Post by cszikszoy on 2009-03-06
> **nyarnon said:**
> I'm running a 1000h if i'm not mistaking the same wireless. Updates didn't break anything here.

The eeepcs generally come with 2 different wierless cards.  I have a 901 with the railink card,, but my friend has a 1000 with an atheros card.

---

### Post by lamalex on 2009-03-06
I have a 900A with an atheros chip, working flawlessly. What chipset is your 901?

---

### Post by cszikszoy on 2009-03-06
> **Iamalex said:**
> I have a 900A with an atheros chip, working flawlessly. What chipset is your 901?

Something sounds funky, because my 901 with the railink card works perfectly too (wep, WPA, WPA2, LEAP, etc).

---

