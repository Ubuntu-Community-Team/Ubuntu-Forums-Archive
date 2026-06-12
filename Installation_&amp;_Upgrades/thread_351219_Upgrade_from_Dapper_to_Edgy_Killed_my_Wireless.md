---
title: "Upgrade from Dapper to Edgy Killed my Wireless"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by akirksey on 2007-02-01
I can't say my sudden transition from windows to Ubuntu has been a nightmare. There has been tons of help, and several weeks ago (after two and a half weeks of troubleshooting) the helpful instructions in the forum provided a means to activate my broadcom 4318 Airforce One g801.11 wireless card and finally enjoyed an internet connection provided through ubuntu's efficient OS that I’ve only once before seen rivaled by Comcast's internet service which is as fast as whips. 

By no means do I consider the length of time it takes to set up a Linux system a downside to running Linux. It's fantastic, you know how to control and command your hardware better. I like this. I haven't had this before, and as I said my transition from the training wheels of computing with windows to the motorcycle of Linux was sudden. So with the windows file system still burned into the back of my mind, I began the endeavor to learn and understand how the Linux fs works. The system documentation is great for just the absolute basics, but the terminal commands, and their sub commands are a labyrinth of hell... at least for now.

So I'm posting this question with the hopes of better understanding the terminal, its commands, and the way Ubuntu communicates to my hardware rather then just blindly following some commands someone posted in a thread. I might have come over to Linux abruptly by accident (how this happened is a story for another time, label me n00b why not?) but I'm here to stay. 

Ok so here's the problem.

I got my wireless card active in dapper, for complicated reasons I decided after I got my system half way to where I wanted it, I'd wanted to enjoy Beryl to enhance my desktop. I needed to upgrade to Edgy Eft. So I went about searching the forums for how to do this. Following the reboot my network manager no longer had my wireless eth1 displayed. Ubuntu is under the impression that I don't have a wireless card. Deja Vu, this was what happened the first time, but then I was in the terminal making changes myself and keeping track of what I was doing (wisely) to undo it. Now I'm at a complete loss on how to even get the system to see that it’s there, and then to get ndisgtk to acknowledge that yes the hardware is there as well. Ndiswrapper says the driver for my wireless is installed. 

Last time, what solved the problem was a series of commands provided to trouble shoot the failure of ndiswrapper. I’m uncertain to which actually 'did the trick', but heres the list:

sudo rmmod ndiswrapper
sudo ifdown eth1
sudo ifup eth1
sudo dhclient

---

