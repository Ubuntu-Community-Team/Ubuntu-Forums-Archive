---
title: "DHCP updating MS dns server (NOT!)"
date: 2005-09-16
forum: Installation &amp; Upgrades
---

### Post by Thomas Mockridge on 2005-09-16
Hi

I have installed Ubuntu 5.04. I use an MS XP PC as my internet gateway using internet  connection sharing. (No political flames please - reasons beyond my control!) The issue is the MS DHCP supplies ubuntu with an IP address and all the DHCP details I need. I can connect out and browse the internet etc. (This is posted from ubuntu). What ubuntu does not do is update the MS dns server. I cannot ping the ubuntu machine from any MS platform and if I remove the /etc/hosts entry I cannot see this machine.  A local nslookup of my ubunto host fails on all machines. My other PC's all work fine (XP, 2000 and an old Knoppix 'live' CD)

I added:[FONT=Courier New]
############## Thomas Added #####################
send fqdn.fqdn "mythtv.mshome.net.";
send fqdn.encoded.on;
send fqdn.server-update on;[/FONT]

to the /etc/dhcp3/dhclient.conf file

Also set ubuntu hostname and domainname to the above, rebooted, cursed etc..  but still the MS dns doesn't know me. This has caused my MythTV to fail as "gethostby name" uses the MS server ... 

Help! ](*,) 

Thomas

---

