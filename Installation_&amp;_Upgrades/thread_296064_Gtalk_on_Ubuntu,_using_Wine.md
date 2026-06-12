---
title: "Gtalk on Ubuntu, using Wine?"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by Z13 on 2006-11-09
I launched gtalk with wine but can't login; these are the processes shown in the terminal. I waited 20 min but still nothing.
Does anyone know if I can run gtalk on ubuntu using wine?

```
fixme:richedit:fnTextSrv_TxSendMessage 0x1280c20: STUB
fixme:richedit:fnTextSrv_TxSetText 0x1280c20: STUB
fixme:richedit:fnTextSrv_TxGetNaturalSize 0x1280c20: STUB
fixme:richedit:fnTextSrv_TxSendMessage 0x1280c20: STUB
fixme:richedit:fnTextSrv_TxSetText 0x1280c20: STUB
fixme:richedit:fnTextSrv_TxSendMessage 0x1280c20: STUB
fixme:richedit:fnTextSrv_TxSetText 0x1280c20: STUB
fixme:richedit:fnTextSrv_TxGetNaturalSize 0x1280c20: STUB
fixme:richedit:fnTextSrv_TxSendMessage 0x1280c20: STUB
fixme:richedit:fnTextSrv_TxSetText 0x1280c20: STUB
fixme:richedit:fnTextSrv_TxSendMessage 0x1280c20: STUB
fixme:richedit:fnTextSrv_TxSetText 0x1280c20: STUB
fixme:richedit:fnTextSrv_TxDraw 0x1280c20: STUB
fixme:richedit:fnTextSrv_TxSendMessage 0x1280c20: STUB
fixme:richedit:fnTextSrv_TxSetText 0x1280c20: STUB
fixme:richedit:fnTextSrv_TxSendMessage 0x1280c20: STUB
fixme:richedit:fnTextSrv_TxSetText 0x1280c20: STUB
fixme:richedit:fnTextSrv_TxDraw 0x1280c20: STUB
fixme:richedit:fnTextSrv_TxSendMessage 0x1280c20: STUB
fixme:richedit:fnTextSrv_TxSetText 0x1280c20: STUB
fixme:richedit:fnTextSrv_TxSendMessage 0x1280c20: STUB
fixme:richedit:fnTextSrv_TxSetText 0x1280c20: STUB
fixme:richedit:fnTextSrv_TxDraw 0x1280c20: STUB

```

---

### Post by angkor on 2006-11-09
Did you try to use gaim to connect to gtalk? Since gtalk uses the jabber protocol it should work great on linux natively.

[http://www.google.com/support/talk/bin/answer.py?answer=24073](http://www.google.com/support/talk/bin/answer.py?answer=24073)

---

### Post by Z13 on 2006-11-09
Gaim doesn't have voice capabilities. I tried Tapioca VoIP but now I'm using Edgy x64 and they haven't released yet the packages for my system.

---

### Post by revertex on 2006-12-14
jabbin works flawlesly, dead easy to install.
i can talk with windowze users without they notice that i'm using linux.

[http://www.jabbin.com/int/](http://www.jabbin.com/int/)

---

### Post by loell on 2006-12-14
thanks, who needs tapioca, when there's jabbin :)

---

### Post by Z13 on 2006-12-14
> **revertex said:**
> jabbin works flawlesly, dead easy to install.
i can talk with windowze users without they notice that i'm using linux.

[http://www.jabbin.com/int/](http://www.jabbin.com/int/)

Is there any way I can use jabbin on my amd64 machine?? (I found only a package for ubuntu/i386)

---

### Post by bizaarem1ke on 2006-12-17
I cant get jabber to actually use the voice over ip.. i can send msg's like gaim.. but when i try to connect to use the voip  function it doesnt seem to want to send what i say.. now.. is there a kmixer, or alsamizer setting i need to use..  and also i cant here them talk.

---

### Post by GV1pJTHl on 2007-07-13
> **revertex said:**
> jabbin works flawlesly, dead easy to install.
i can talk with windowze users without they notice that i'm using linux.
[http://www.jabbin.com/int/](http://www.jabbin.com/int/)
It would be nice to know what hardware you're using. I've got a Dell D800 laptop and can't get the voice calls to work. We can get calls to connect but the bars aren't lighting up and there isn't any traffic back and forth (both sides get zero bars from receiving party.

From looking at quite a few other posts here and elsewhere it seems many people suffer from the issue. Have tried aoss and reconfiguring sound, etc and still no joy.

---

### Post by ashfaq.nsu on 2007-09-15
> **revertex said:**
> jabbin works flawlesly, dead easy to install.
i can talk with windowze users without they notice that i'm using linux.

[http://www.jabbin.com/int/](http://www.jabbin.com/int/)

thanx for the help:guitar:

---

### Post by orengolan on 2008-04-30
I want to use gtalk because of the voice message feature-
sending an audio message to an offline friend.
right now I use XP on VirtualBox but I would like 
to do it from my hardy instead.

wine googletalk-setup.exe actually installs it but 
it fails to connect to the server with my credentials.

---

### Post by vigyani on 2008-06-05
Hi
I am using Empathy on Ubuntu 8.04 for voice chat with Google talk users; for details check the following:

[http://ubuntuforums.org/showpost.php?p=5118375&postcount=1]("http://ubuntuforums.org/showpost.php?p=5118375&postcount=1")

---

### Post by orengolan on 2008-06-05
I am using pidgin but I would like to find a way to send **voice message**, just like the gtalk in windows.

---

