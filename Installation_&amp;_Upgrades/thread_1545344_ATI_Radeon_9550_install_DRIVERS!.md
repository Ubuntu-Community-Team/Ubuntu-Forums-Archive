---
title: "ATI Radeon 9550 install DRIVERS!"
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by alberto2172 on 2010-08-03
hello i have recently installed ubuntu 10.04 on  my Windows PC but i am trying to install ati driver 9550 on it. i want to install them because i want to use Compiz Fusion. Can anyone help me out with this problem.. Thanks alot

---

### Post by Cavsfan on 2010-08-03
I have an Nvidia card, but this might help [[COLOR=blue]_here._[/COLOR]]("http://www.google.com/webhp?as_q=#hl=en&source=hp&q=ubuntu+ati+radeon+9550&aq=f&aqi=&aql=&oq=&gs_rfai=CPmLaSZxYTPHmOpi8zgTHmdCxCgAAAKoEBU_QiKSE&fp=24975515c8815dd")

---

### Post by spydeyrch on 2010-08-03
> **alberto2172 said:**
> hello i have recently installed ubuntu 10.04 on  my Windows PC but i am trying to install ati driver 9550 on it. i want to install them because i want to use Compiz Fusion. Can anyone help me out with this problem.. Thanks alot


How are you trying to install the driver?  I would recommend that you try going to the system menu -> admin -> hardware.

It should scan your hardware and give you a list of any relevant drivers that are appropriate for your hardware.  Select the correct driver (usually only one available in the list) and activate it. You may have to restart it for it to start taking affect.

The other thing is that some of the older GPUs are no longer supported by the newer versions of the proprietary drivers by the manufacturer.

I don't know if yours is or isn't at this moment.

-Spydey :KS

---

### Post by sepius on 2010-08-07
Just had a power outage kill my system and now have reverted back to my old system from '06 with an ATI 9550 (Gigabyte I think).  When I goto "Hardware Drivers" it does not get detected, I suspect it is obsolete.
Stand by, if I find a fix I'll post back, but might have to move over to the open source drivers.

---

### Post by Mark Phelps on 2010-08-07
You will have no choice other than to use the open-source drivers -- which are installed by default.  If you're seeing a graphical desktop, not a text screen, the drivers are already installed.

Do NOT try to force the installation of any other drivers.  ATI dropped proprietary driver support for your card over a year ago and NONE of the current ATI drivers will work with your card.  Plus, the only OLD drivers that will work with your card will not work with current versions of Ubuntu.

---

