---
title: "Hardy Heron upgrade problems"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by shouden on 2008-04-24
Hello all, I have been having some major problems after my upgrade to 8.4 from 7.10. The upgrade appeared to be successful, and after a reboot I was able to log into Gnome using my user account. Right afterwards Gnome completely locked up, I was unable to move the mouse and the OS was unresponsive when trying to switch to a console so I did a ctrl + alt + backspace to restart X. This caused X to close and show me that there was a kernel panic, the system was also unresponsive from the CLI.

I rebooted the PC and I was again able to log in, this time it did not lock up, but every program I attempted to open would fail, except for a terminal window, and nautilus. I also tried to open things via the terminal but they would just hand for several minutes and close without an error message. I browsed to my home directory and all the folders permissions had been changed so that I did not have permissions to view or modify the files. I also checked other directories and most had revoked my permissions to read the directory contents.

I rebooted the PC again and I was able to login, my permissions were fine, but my NIC card no longer functions (Not certain of the model, but it is onboard, and this is a desktop PC with a LAN connection.) The PC cannot get a DHCP address, and when I manually assign an IP address to it and attempt to ping my default gateway I get the message 'destination network unreachable'. I have tried  using ifconfig to bounce the port but it has had no effect, subsequent reboots have not fixed the problem either, although no other problems have showed up since this one occurred.

If anyone has any ideas they would be greatly appreciated.

---

### Post by shouden on 2008-04-24
Well I left the PC on while I was at work, and came back to it sitting on the CLI again, this time being unable to read a section of the hard drive. I rebooted it and it seems to be fine now, the LAN adapter is working perfectly. I am going to give it 24 hours and see what happens.

---

### Post by shouden on 2008-04-25
Well it hasn't yet been 24 hours, but the Ethernet link is down again. I have tried swapping out the cable for another one but I still get the error "destination unreachable" I have tried other hosts on the switchport the PC is connected to and they have worked fine. During the troubleshooting process I noticed that rebooting the PC fixes the issue, and the issue does not occur again until I open the Azureus bit torrent client. Other clients do not cause this problem. This is a program that was uninstalled during the upgrade process, and I reinstalled afterwards. Is it possible that some of the older unsupported application remains? If so, is there a way I could find out?

---

