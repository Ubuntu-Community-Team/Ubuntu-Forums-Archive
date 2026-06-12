---
title: "Linksys EPSX3 print server"
date: 2007-10-09
forum: Installation &amp; Upgrades
---

### Post by BSayer on 2007-10-09
ubuntu 6.06 on a dedicated SATA drive.

The installation has gone basically ok, except that I can't access any printers yet.  I have a Linksys EPSX3 print server with an HP 4050 laser printer and an HP 950 ink jet, both connected to the print server via parallel cables.

The print server is attached to a Linksys switch, as is the computer.  However, I use DHCP to get IP addresses, and I suspect the problem might be there.

What do I need to specify in cups to get ubuntu to see these printers?

---

### Post by rvickers on 2007-10-21
Wish someone would answer this, I have the same problem...
Thanks

---

### Post by rvickers on 2007-10-23
I resolved this by using an Ubuntu desktop as a print server ( very simple to do ). The EPSX3 is connected via parallel and print server via usb. This fixed my Ubuntu laptop printing but I still have my wife's XP laptop using the EPSX3. I'm going to play around with how I can print to the Ubuntu server printer via XP. As a side note, my Ubuntu laptop runs 6.06 and was printing fine to the EPSX3 until recently, not sure what changed, I have an IP assigned to the EPSX3 by the way. 
[http://ubuntuforums.org/showthread.php?t=302960&highlight=cups+howto](http://ubuntuforums.org/showthread.php?t=302960&highlight=cups+howto) has some good info in it...

---

