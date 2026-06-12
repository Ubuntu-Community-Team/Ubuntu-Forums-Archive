---
title: "Speedtouch USB ADSL modem stopped after upgrade"
date: 2006-08-31
forum: Installation &amp; Upgrades
---

### Post by captain.kipper on 2006-08-31
I have just done a system update (the first for a few weeks) and now my internet has died. It has been a right palava getting it going ever since I switched to Linux. The Alcatel/Thompson USB modem is (still) badly supported, it seems. :x 

Some details: Running Dapper 686 on a P4 desktop. I think it upgraded from .25.to .26. I recall seeing that it updated PPP amongst other things, which I suspect broke it.    
I originally used this guide
[https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch)
to get it working after I first upgraded to Dapper. 

I have tried going through it agoin, but to no avail. (I also made sure I copied the firmware to the new .26 folder)

Can anyone help?:confused: 
Many thanks...

---

### Post by captain.kipper on 2006-09-01
EDIT:

After reboot internet etc is working again. If anyone has similar problems ensure you copy the 2 fimware files (speedtch-1.bin & 2.bin) to the latest kernal version folder in /lib/firmware/ (in this case /lib/firmware/2.6.15-26-686).

Hope this helps out anyone else out there having similar problems. :D 


PS
Note to developers / bugfixers - could you sort it so that these added firmware files are copied to any future new /lib/firmware directories in future updpate scripts?

---

