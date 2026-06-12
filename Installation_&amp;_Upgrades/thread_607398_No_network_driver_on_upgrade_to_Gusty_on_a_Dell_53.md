---
title: "No network driver on upgrade to Gusty on a Dell 530N with preinstalled Feisty"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by ejb11235 on 2007-11-08
I just tried upgrading my Dell 530N that had Feisty preinstalled on it. The upgrade itself went fine, but on the reboot I got a message saying that there were no open source network drivers. I opened up the restricted drivers manager expecting to find a network driver to enable, but there isn't one. 

Now I don't know what to do:confused:

------------

UPDATE - Problem "solved" :)

I ended up doing a full system restore back to Feisty as delivered by Dell. When I ran "lspci" the NIC showed as "unknown" even though it was working.

I then paved the  hard drive and did a full install of Gutsy and it detected the NIC card fine. Now when I do an lspci, the full name of the NIC is properly displayed:

00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)

So I'm thinking that the real problem wasn't with Gutsy but with the Feisty configuration.

---

