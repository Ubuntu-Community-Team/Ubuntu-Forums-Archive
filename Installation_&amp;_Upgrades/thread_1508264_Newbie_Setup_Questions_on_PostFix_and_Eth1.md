---
title: "Newbie Setup Questions on PostFix and Eth1"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by ajfletcher on 2010-06-12
Hey all, I just made the leap to Ubuntu 10.04 Server Edition.  Previously I used a dedicated hosting plan with cPanel.  I decided setup my own box and only use the command line for this new dedicated server.  Its up and running now in my place of business and wow its a lot faster than my old CentOS with cPanel dedicated hosting plan that I paid $145 a month.

Well so far things have gone rather well.  I have Apache setup, with three Virtual Websites ported over and seem to be running fine (even faster than before) with mySQL, PHP etc.  There are however a couple of things that I can't get my head around.

1.  Okay I setup POSTFIX but I have no clue how to use it.   For example I have three sites running and I want each to have a "webmaster@site1.com"   "webmaster@site2.com" and "webmaster@site3.com"   These are all virtual sites created and running off my home directory.  How the heck do I setup email accounts for these sites?   Is there a nice HOWTO I can use?

2.  Lastly, my server has two Ethernet Ports and I have two dedicated IP addresses so I thought, hey I can setup both.  Well I did that and added eth1 to the /network/interfaces and then all of a sudden eth0 stopped sending webpages but you could still ping it.  Then I thought, Okay I know what I will edit sites-available and instead of using <VirtualHost *:80> I would use <VirtualHost XXX.XX.XXX.X:80> (XXX being the actual IP address) and all I got was a big error.

Right now I have removed eth1 for the moment and things are working again

Sorry if these are basic questions but I feel I have made progress setting up my First Ubuntu box from scratch and not using cPanel or other GUI.  It's actually pretty easy.

---

