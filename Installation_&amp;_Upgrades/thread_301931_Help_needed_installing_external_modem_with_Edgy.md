---
title: "Help needed installing external modem with Edgy"
date: 2006-11-17
forum: Installation &amp; Upgrades
---

### Post by John Read on 2006-11-17
Hope someonre can point me in the right direction.
Have just installed Ubuntu Edgy (6.10) on an Intel box and set it up to dual boot with Windows XP.

The installation was the easiest I've ever done in the last 15 years for _any_ system (Windows and Linux):) 

The only hassle I have is I can't manage to set up my _external_ modem (connected to /dev/ttyS0) so it will work. It worked fine with Red Hat Linux 9 so I suspect I'm just overlooking something? Currently the modem just won't respond in any way at all. Have read all the documentation I can find.

Thanks in anticipation. John R.

---

### Post by gborzi on 2006-11-17
Have you tried pppconfig ? I mean to give the > sudo pppconfig from a terminal and follow the instructions. It should detect your modem, if not, give the port device.

---

### Post by John Read on 2006-11-19
Thanks for the advice. Was kind of hoping to be able to get it all sorted using the graphical Network front-end via the System menu of Ubuntu 6.10 (Edgy) but just coudn't get it to work that way.
Cheers, John

---

### Post by Bartender on 2006-11-19
What kind of modem is it (manufacturer, model #) and more importantly, have you had this modem working with your ISP previously, say with Dapper?

---

### Post by John Read on 2006-11-21
Finally read the ModemHowTo at xxx and tried the wvdial method. Worked like a charm. Apparently most external modems can be used bu Ubuntu quite successfully without having to track down special drivers. Will download the Kppp graphical dialer as it appently works well under Gnome too.
For anyone else having external modem problems with Edgy, go to [http://help.ubuntu.com/community/DialupModemHowto]("http://help.ubuntu.com/community/DialupModemHowto")

Cheers,  John

---

