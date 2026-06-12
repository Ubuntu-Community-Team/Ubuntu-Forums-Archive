---
title: "Confugure ADSL Router...."
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by LORD_EC on 2007-04-12
I use a D-link 504 ADSL router to connect to my broadband..It needs no settings in Windows XP.
My ISP provides us with a dynamic IP everytime i connect with my broadband..
I tried hard to connect internet in Ubuntu 6.10 but failed..Can anyone explain how can i do that ??
I am able to ping sites like google (with the help of ping tool ) etc but i am not able to open it in a browser.
Can anyone help me ??please

---

### Post by pxwpxw on 2007-04-12
Hi,

I have a dlink 504g here now, using it as a routerr/modem for 4 computers.
Can you open the ADSL router config web page from your browser, using
the address 10.1.1.1

---

### Post by LORD_EC on 2007-04-12
ya i can do that..But wht shud i do after that ???

---

### Post by pxwpxw on 2007-04-12
Go to the Status tab, 

Look at the Device Info to see if you are connected
and have  IP Address
and DNS Server Enabled

Also look at the Log tab, last entry .

Thu Apr 12 19:20:12 2007 : STATUS ALARM: PPP Authorization Successful : Interface - ppp-0
Thu Apr 12 19:20:13 2007 : STATUS ALARM: PPP Event: NCP Got IP address:
Thu Apr 12 19:20:13 2007 : STATUS ALARM: PPP Event: NCP Got primary DNS address
Thu Apr 12 19:20:13 2007 : STATUS ALARM: PPP Event: NCP Got secondary DNS address
Thu Apr 12 19:20:13 2007 : STATUS ALARM : PPP Interface Up : Interface - ppp-0
		
(I deleted my ip address info)

Does that look ok?
(may be different format if your router is different version)

---

### Post by pxwpxw on 2007-04-13
Your problem may be that the ADSL modem is setup in Bridge Mode.

Check your ADSL router, Home - WAN Setting

If this is in Bridge Mode, the normal Ubuntu network configuration will not work,
and can be difficult.

[http://ubuntuforums.org/showthread.php?t=288645&highlight=bridged+modem](http://ubuntuforums.org/showthread.php?t=288645&highlight=bridged+modem)

The PPPoE/PPPoA Setting with username/password in the DSL504 suits the 
standard wired network configuration in Ubuntu.

If this is the case, your isp should be able to help you change the ADSl modem configuration.
and Windows.

---

