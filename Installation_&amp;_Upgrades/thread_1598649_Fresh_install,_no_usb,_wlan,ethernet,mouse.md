---
title: "Fresh install, no usb, wlan,ethernet,mouse"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by sirkeith on 2010-10-16
I have put 10.04.1 386, 32bit, on a Toshiba C650 laptop. Took Win 7 off. Install seemed good. The only cd daily I could find was from August 16.

I have a cdrom/dvd showing up but not much else. The mousesort of works, acts like it has an irq problem, jumps around and is slow. The touchpad works ok. USB sticks don't show up, nor ethernet card nor wireless card. An lspci shows everything there. Machine won't shutdown and is slow starting but does start.

Any thoughts are appreciated.

keith

---

### Post by TBABill on 2010-10-16
Those symptoms actually sound like a defective install disk that finished installing, but with problems. I had a bad burn (due to a bad download that I forgot to do a md5sum check of) that had similar types of system issues. Everything looked ok but a lot of operations just didn't work or were improperly working. Fresh download and new (slow) burn with a reinstall worked fine.

---

### Post by sirkeith on 2010-10-18
TBABILL, thanks for the reply. I had deleted off the drive the download so I redownloaded, md5sum was good and I reinstalled with the same results. So I got Maverick and installed it with some better results, I now have ethernet working and the wireless works. No USB response from mouse or sticks but I have found from more searching that these Toshiba's seem to have some problems. I would like to load my home onto the new mahine but that ain't gonna happen until I have USB. I will keep searching the forums.

I appreciate your help.

keith

---

### Post by amjjawad on 2010-10-18
I don't think there was anything wrong with the first installation, it's just 10.10 probably has more "drivers" than 10.04.

I know it's a bit late because you already installed but next time, make sure to try Ubuntu from the LiveCD before installing it :)
At that time, you could find what will work and what will not.

You need to find the missing drivers, download and install them.

---

