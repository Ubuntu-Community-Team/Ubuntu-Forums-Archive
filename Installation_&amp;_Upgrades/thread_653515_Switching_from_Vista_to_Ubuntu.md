---
title: "Switching from Vista to Ubuntu"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by tgrav on 2007-12-30
In the past week I have made the change from Vista to Ubuntu 7.10. I had some issue installing Ubuntu on my laptop which is a presario f500 and it has a broadcom chipset and  I thought I would write what I did to correct this issue. Please, first let me say thanks to all the great help I got here to help with my problems. 

First when I was installing Ubuntu for the 1st time I ran in to an issue where it would not show the installation screen and my screen would stay blank. I found out that I had to do the following. When I ran the live cd I would have to select f6 instead of selecting start.This will allow you toubuntu online tutorials add boot parameters that will corrected my blank screen issue. Here's what you need to type. At the end of the code "quiet splash" you will need to add noapic irqpoll noirqdebug.

To get my wireless working I found a post ([http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)) in the tutorials, which worked to a tee. Even though I don't have a Dell machine I did use the drive and I worked and I am able to get my wireless to turn on. 

After I was able to turn on my wifi I was able to see all network connections, but I was not able to connect to them no matter what I did. So I used the following post [http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154), which once again worked like a charm. It did not work right away because I had my routers encryption on and this caused issues. So I disabled all encryption on my router and tried to connect to it. After rebooting my router, modem and computer I was able to see and connect to my ssid. Then I turned on my encryption and I have not had an issue with it yet.

I hope this helps anyone trying to install ubuntu. Once again I want to thank everyone for the support.

---

