---
title: "No network access after upgrade"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by Fiddlestx on 2008-05-15
Hello,

I recently upgraded from 7.10 to 8.04 using the update manager and everything went fine untill the installation finished. I am using a Dell inspiron 8100 and my integrated ethernet card is not being detected. It is not showing up in the network manager and eth0 is not being detected in ifconfig however the activity light is working on the port. This is particularly frustrating because I can't even connect to the internet to download the broadcom drivers for my wireless card in the drivers manager. Does anyone have any suggestions on what i might try to get it to detect the integrated card?

---

### Post by Indroth on 2008-05-25
I had a similar problem (or at least similar symptoms). I had to bring up eth0 manually:

ifconfig eth0 up

Then

dhclient

Worked fine after that.

If this doesn't work and you don't have eth0 listed in ifconfig -a, then you have some other problem. You could start by making sure your controller is listed in lspci.

---

### Post by ScottyP on 2008-05-31
I like when others have my problem. Same laptop. Same problem. If I use ifconfig -a it doesn't even list my adapter. My 'puter doesn't even know it exists.

How much does it not know it exists? When I run lspci there is nothing listed for ethernet adapters.

---

### Post by Indroth on 2008-05-31
I don't have the same computer, so my problem could have been totally different. However, if there is nothing listed in lspci, I think that usually means that the hardware is not present or not working. Not sure about that though, so don't take my word for it.

---

### Post by ScottyP on 2008-05-31
Indroth-

Do you there any way to force Ubuntu's hand and say "Yes you do have a network card" like there is with Windows?

---

