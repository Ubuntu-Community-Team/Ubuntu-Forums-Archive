---
title: "Need Newbie level Instructions for a Massive Server"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by soulreaper76 on 2008-02-24
I want to setup a Ubuntu 64 bit Server 7.10 with the following options

[LIST=1]
[*]LAMP Server
[*]NTP server for internal network
[*]Firewall for itself & the rest of my network
[*]AV & Anti-Spyware for web surfing & e-mail
[*]Content filtering
[*]Block P2P
[*]IM interception and logging in clear text (to keep an eye on my kids)
[*]Would like to be able to intercept files like photos and zip files sent via IM
[*]Logging Myspace messaged would be nice
[*]Anti Spam for 2 domains (or more)
[*]DNS for internal network
[*]Backuppc for windows, Ubuntu workstations, & the server itself to a single ext USB HD
[*]3 Websites, 1 internal (backuppc and such) and 2 for external use
[*]I'm guessing LDAP but some kind of Active Directory like domain structure, so all my users can go from one computer to another with the same login and possible the same desktop
[*]I would like the gnome desktop on the server as well
[/LIST]
Yes I want this thing to do everything for me, if I could get it to mow the lawn too I would :lolflag:

I Have the following hardware

[LIST=1]
[*]Dell Server SC440 with...
Intel Pentium D 3.20GHZ (Duel core 64 Bit)
2-250GB SATA HD's in a Hardware mirror
1GB Ram (willing to get another gig if needed)
[*]500GB Ext Hard Drive for backup
[*]DSL Line with Static IP (can have more IPs for free if its better to have multi IP or Multi NIC Config)
[*]Wireless for the laptops
[*]1 Windows XP Pro laptop (Kids)
[*]1 Ubuntu workstation 7.10 laptop
[*]1 Windows XP Pro Desktop (Wife's)
[*]2 Ubuntu Workstation 7.10 Desktops (my gaming systems)
[*]currently working off a 100 network but will be upgrading to 1000 soon
[/LIST]

I'm a PC Tech with extensive Microsoft background wanting to get away from viruses and Spyware with a bonus of learning more Linux.
I know a lot of this is configured all over the web already and have been trying to get it all working and most of it I do have working, but would rather have it all in 1 place as I do not know what apps work well with others and what ones are better then others.
Most important part to me is protecting my kids, so the IM trap and content filtering are very high on my list, only thing I have seen so far that does the IM trap is Smoothwall, and the best content filter I have seen is Astaro. but i want them all in 1 package.

If you have entry level links to the info I need that would be fine as well, ill just print them all out, and I'm sure the LAMP and Firewall parts are easy but it must have the IM portion or ill just end up sticking with Smoothwall.

PS please don't let this turn into a privacy issue with the snooping, we all parent are own ways. Thank You.

I am Loving My Ubuntu more and more every day, just want to work on moving ALL of my computers to Ubuntu Distributions!

I'm going to go ahead with the LAMP part myself as that seams easy enough.


Thank You All For Your Time and Effort
Stephen S.

---

### Post by m@ra on 2008-02-24
Whee... That is kind of a setup... First of all. Just putting in a Ubuntu server CD and clicking next next you would find yourself most of these installed with default settings. (LAMP etc.) What comes then to proxy settings is more challenging. 

One option for proxy which would do content filtering is this one. [http://dansguardian.org/?page=whatisdg](http://dansguardian.org/?page=whatisdg).

With proxy you can block some protocols / network ports if you set it also to network gateway. Such as torrents.

-DNS & DHCP is basic components,
-NTP is default stuff, just search ubuntuforums for configs.
-OpenLDAP will do same as Active Directory (at least at home).
-Backups are quite easy with cron & SCP scripts 

If you just start with installing these components first =)

I would say either block or allow => don't log.

---

### Post by soulreaper76 on 2008-02-24
m@ra Thank ou for you response

Do you know if I will be able to see Instant messages in some kind of log?
I need to allow MSN messenger or ill get hell from everyone, But feel that with all the un-nice ppl out there I need to monitor the chat 

Also is it safe to use the firewall as the main server (storage & backup, etc) or am I just asking to get hacked?

Thank You for Your Time
Stephen S.

---

