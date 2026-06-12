---
title: "IBM T20: video, wifi, shutdown problems"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by mattotoole on 2006-10-27
I just tried running 6.10 livd CD on my Thinkpad T20.  The same problems persist from 6.06, which is why I'm still running 5.10 every day.

First, the video only works in safe mode.  Otherwise I get a blank screen.  This problem existed in 6.06, but 5.10 works fine.

Second, there's no wifi.  I'm using a Linksys WPC-11, a common-as-dirt wireless card.  So there should be no hardware problems, and it works fine with 5.10.  With 6.06 and 6.10, the networking applet doesn't automatically find an open network and connect, as it does with 5.10.  It won't create and enable a location with the ESSID field left blank.  If I do put in a valid ESSID, the network card shows two solid lights as if it's connected, but I can't ping out.  I had this same problem in 6.06, which is why I haven't upgraded.  

Third, my system won't shut down properly.  I have to use the power button.  With 5.10 this happens sporadically, but 6.06 and 6.10 have never shut down properly at all.

Until I find solutions to these problems, I'll stay with 5.10.

---

### Post by qriopal on 2006-10-31
I could confirm one thing that 6.06 and 6.10 has problems on thinkpad T20. I tried to install both Xubuntu and Ubuntu Edgy Eft and Dapper Drake but they would not even run as liveCD. I could run 5.10 liveCD though without any problem. 

When I use Edgy Eft or Dapper Drake liveCDs, I get a message about the possibility of corrupting my serial EEPROM because of which it says it cannot load some module. I do not get any such message in Ubuntu 5.10. I wish the developers will take a note of this and do something to fix it in the next release. 

Thanks.

---

### Post by mattotoole on 2006-12-05
> **qriopal said:**
> I could confirm one thing that 6.06 and 6.10 has problems on thinkpad T20. I tried to install both Xubuntu and Ubuntu Edgy Eft and Dapper Drake but they would not even run as liveCD. I could run 5.10 liveCD though without any problem. 

When I use Edgy Eft or Dapper Drake liveCDs, I get a message about the possibility of corrupting my serial EEPROM because of which it says it cannot load some module. I do not get any such message in Ubuntu 5.10. I wish the developers will take a note of this and do something to fix it in the next release. 

Thanks.

First, ignore the message about corrupting the EEPROM.  I forget exactly what the issue is (old BIOS?), but apparently it isn't a problem.

Second, you should be able to run the Live CD in VGA/safe mode.  I can do this, but I can't get the wifi to work.  Without a functioning network, there's no way I'm going to do a hard drive install, so I'm sticking with 5.10.

---

### Post by darkphader on 2006-12-11
I find that the following option is needed in xorg.conf for proper video operation:

Section "Device"
        ...
        ...
        Option  "BusType"  "PCI"

---

### Post by Mark Stosberg on 2007-01-20
I have you so many problems, consider running Mandriva on the T20, which is what I'm doing now, with full hardware support.  Details are here:

[http://www.thinkwiki.org/wiki/Installing_Mandriva_Linux_on_a_ThinkPad_T20](http://www.thinkwiki.org/wiki/Installing_Mandriva_Linux_on_a_ThinkPad_T20)

About the wifi card, did you find this page?
[http://www.linuxvoodoo.com/resources/howtos/linksysv4/](http://www.linuxvoodoo.com/resources/howtos/linksysv4/)

It looks like it may need a little fussing to work, but may not be an issue of one distro vs another.  I have always had great line with  Orinico/2wire cards, so have stuck with them. 

  Mark

---

