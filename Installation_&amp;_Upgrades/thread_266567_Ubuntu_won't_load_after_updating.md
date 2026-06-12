---
title: "Ubuntu won't load after updating"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by dnguyen411 on 2006-09-27
Computer: Dell Lattitue C640
Memory: 512 MB
CPU: 1.2 GHz
WIFI Card: Netgear WG511v2
Ubuntu Version: 6.06

I just recently installed Ubuntu 6.06 onto my laptop. After going through the procedure for loading ndiswrapper from the Live-CD and using the WINXP drivers for my WiFi card, my computer still worked fine.

The problem started as soon as I ran the "sudo apt-get update" command and downloaded all available updates. After restarting the computer, the computer freezes at the point where it loads Network Devices.

Is there a way other than reinstalling Ubuntu from the CD to revert back to before I updated the computer? )i.e., kind of like System Restore for WinXP)

---

### Post by jd65pl on 2006-09-27
Try this..

Boot in safe mode

**Add**
```
alias wlan0 ndiswrapper
```

To:
/etc/modules.d/ndiswrapper

then reboot see if that works

Message back if it works just for info

---

### Post by dnguyen411 on 2006-09-27
I don't have a folder in /etc called "modules.d." I have a "modprobe.d" and a "ndiswrapper" folder.

I'm not familar with the "alias" command.

Could you please eloborate.

Thanks


*****Follow Up Message********

Never mind, I restarted the device back into normal mode and the computer was able to boot all the way through. I'll keep you up to date if this problem occurs again, but for now, everything is working again.

---

### Post by jd65pl on 2006-09-28
Oh sorry it is in the location

/etc/modprobe.d

Create a new file called "ndiswrapper" and insert the line

```
alias wlan0 ndiswrapper
```

This will load the correct wireless module on boot, I think it takes a long time to load because of some sort of driver conflict. This method has worked for me and a few others.

When the computer is booting and hangs on the network setup press [ctrl + C] it should stop the computer from trying to do what it is currently trying to load and continue with the next step

J

---

