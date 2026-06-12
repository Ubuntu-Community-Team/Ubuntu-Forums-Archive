---
title: "Jaunty and wireless broadband USB720 modem"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by electricroo on 2009-03-29
I haven't got my wireless broadband (verizon) using a USB720 modem working in any of the Alpha's or the Beta version of Jaunty Netbook Remix on my Aspire One. Dialing is initiated through network manager, modem light blinks as usual, then network manager gives me a disconnect message. It works in Intrepid. Maybe I missed something, but is this going to be fixed in the final release? Network setting are configured the same as usual.
Any info would be appreciated!

---

### Post by rperkins on 2009-03-29
i have one of these and it worked with jaunty devel.
however i get a more stable connection configuring the modem through pppconfig, and configuring as a standard modem.  when using the network manager interface, i would get lcp terminated by peer disconnects.  had this same issue with intrepid.  i feel the lib used by network manager for cellular modems does not honor the lcp settings in /etc/ppp.

I'm wondering if you also have another network connection active, such as wifi.  have you checked your route and your dns settings while the usb720 is active ?

---

### Post by electricroo on 2009-03-30
Settings are what they should be. The USB720 is my only active network conection. Believe me, I wish I had another option for internet. No cable, no DSL or anything else available here! I am typing this now on my desktop pc running Intrepid with the USB720. It works on the Aspire One with Intrepid also. So it may be a simple change, or something that will not be implemented until the final release, so I will just wait for that.

---

