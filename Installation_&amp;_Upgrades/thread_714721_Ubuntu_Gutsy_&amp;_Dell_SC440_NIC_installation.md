---
title: "Ubuntu Gutsy &amp; Dell SC440 NIC installation"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by frtora on 2008-03-04
Hello guys,
I made a fresh installation of Ubuntu Gutsy on a Dell Poweredge SC440 server. After installation finished I realized that I had no network.:(
I googled, and I found the information I needed in the following link:

[http://ubuntuforums.org/showthread.php?p=1920008#post1920008]("http://ubuntuforums.org/showthread.php?p=1920008#post1920008")    

When I finished with the above procedure the network was working just fine. I made also a few reboots just to see if it was stable, and everything was ok.:)
Then after a few days, since I have fixed the problem, the update manager informed me that new updates were available and of course, as you can imagine, I just installed these updates. A side effect of these update was to lose my network connection once again. Trying to revise the new situation I followed again some steps of the procedure described in the link above i.e.: 
•	modprobe –r tg3 and 
•	insmode tg3.ko 
and the network was reactivated, but until the next reboot. Since then every time I need to reboot the server I have to unload and reload the driver so the NIC to be operational.
Does anyone has a clue how to fix permanently this problem? :confused:

---

