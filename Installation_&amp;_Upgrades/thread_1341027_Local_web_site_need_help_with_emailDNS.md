---
title: "Local web site need help with email/DNS"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by rockym on 2009-11-29
I configured a lamp server on a home network (cable modem), for the purpose of hosting a [Joomla software] web site. 
My hostname is bookworm and i gave the server a static IP address. 
I still very new to this and have the following questions.
 
How can I set up an configure DNS to resolve my server's IP address locally, but still use the cable modem or router's DNS settings to reach the outside when I need to.
 
Secondly, How do I set up email to work locally and if possible to be able to send over internet?
 
Thanks in advanced,
Rocky

---

### Post by darkod on 2009-11-29
Do all the other computers have static IPs too? If they do, then one option might be for DNS1 to enter the local server IP (if that is resolving your local names), and for DNS2 to put public dns server (your isp server or any else).
If your computers are receiving IPs with DHCP just adjust in your DHCP server to assign them DNS1 and DNS2 as above.

For email to work locally you will have to have local email server. If I'm not wrong, when it detects that the recipient is one of you local users it will just keep the email and put it in the mailbox. If the recipient is outside, it should send it over the internet.

---

### Post by rockym on 2009-11-29
No all of the clients get a DHCP address from the router. I'm not sure what you mean by dns1 dns2 etc.
 
Thanks for the reply
Rocky

---

### Post by darkod on 2009-11-29
OK, open the router web config, and in DHCP Server settings it will offer some king of static setting for DNS1 and DNS2 (basically first and second choice dns server to be used). Since first your local network has to find out if the computer is local, DNS1 should be your DNS server, probably your server if you have added that option too.
For DNS2 you need the IP of a public dns server.
If you haven't added dns server option to your LAMP it can't resolve your local IPs. You need one dns server inside your local network to connect the names of the computers with their IPs.
Actually what are you trying to achieve more specifically?

---

### Post by rockym on 2009-11-29
I do not have bind running on the LAMP server. Basically I want my clients to be able to resolve my server by name (without having to edit the client's host file)
Secondly I want to be able to send email locally between the clients and if necessary to send email out to the internet.

---

### Post by darkod on 2009-11-29
I have never used Joomla but I have basic knowledge of public and local dns.
1. In order to resolve it by name, there has to be something converting that name to IP. In other words, local dns server (because the public ones have no idea about your home network). Usually you would add that to the LAMP server. And for the clients to check the local dns server first, it has to be first choice dns server for them, in short DNS1 either in static settings or assigned by the router DHCP server.
2. To be able to send and receive email locally you need local email server. It will have to have the accounts (mailboxes) created and put the message in the corresponding mailbox. If the message is for outside recipient, the email server also will have to have internet access to send it to the recipient mail server.

Maybe Joomla allows some of this functions, but I have no idea about that as I said. Unless Joomla is helping you with that, you need to expand your LAMP to be also dns server and mail server. Or add another server to your network.

Try googling "ubuntu dns server", "ubuntu mail server" etc. I'm sure there will be some great tutorials.

---

### Post by rockym on 2009-11-29
Okay. I can install BIND for DNS. Joomla does not help with name resolution so It needs to be handled with DNS.
 
What about email. Is there a quick way to see if I have it configured correctly from the server. I should have mentioned that all my client PCs are running windows XP.

---

### Post by darkod on 2009-11-29
As far as I know LAMP is not automatically a mail server. Correct me if I'm wrong (haven't worked with LAMP either :) ). So unless you set up mail server additionally to LAMP I can't see how it would be set up.
Sending a test email is probably best way to try but unless you did the above said, no chance it would work.

---

### Post by rockym on 2009-11-29
I did set up mail, but no real way of knowing if i did it right. I'll work on bind and I'll update this post as soon as I have more information. Thanks for all the info.
 
Rocky

---

### Post by darkod on 2009-11-29
Well if you did setup mail server, you could test but not until DNS is working usually.
Create two accounts in the mail and try sending test email from one to the other. But for the clients to be able to "see" the mail server you have to get the DNS up and running.
Also for the DNS, there are two options. Your DNS server can connect over internet with public servers, and in that situation it's enough your clients to have only your local DNS server in the settings, It will help them resolve also the public names.
If the local DNS is not relaying the public names too, then the clients need to have DNS2 as second choice in the settings which can be your router for example (usually your router would relay DNS to clients anyway). But now you need to make the router second choice, better to look for local names first on your local dns.
Hope you get it going. Cheers.

---

