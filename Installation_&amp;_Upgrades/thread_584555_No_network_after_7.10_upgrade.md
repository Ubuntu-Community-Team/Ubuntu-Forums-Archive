---
title: "No network after 7.10 upgrade"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by empiremonkey on 2007-10-21
Since i upgraded to 7.10, all my networking no longer works.

I have a Dell C600 laptop and a 3Com PCMCIA wifi card.

The Wifi worked fine becuase it was used to download the upgrade. The IP details are the same but no network/internet.

I have tried the wired NIC, but again no joy.

any ideas out there ?

cheers

---

### Post by bluedragon436 on 2007-10-21
This may seem like a dumb question, and I am sure you have already checked but will ask anyways...did you already check to make sure that the computer sees these pieces of hardware and that it has installed the proper drivers for them???  I had an issue with my internal WiFi car originally when I first installed 7.10, but have since been able to get it working again due to still being able to run the Wired NIC.

---

### Post by empiremonkey on 2007-10-21
Network Settings shows both the wifi and internal nics.

the wifi properties will even pick up the various wifi networks near my house. 

I choose mine and enter the wep code etc, but still not joy with network or internet

---

### Post by empiremonkey on 2007-10-21
sorted it

i removed amd re installed network manager and it's now working !

work that one out :)

---

### Post by bluedragon436 on 2007-10-21
I was actually thinking about recommending to do that too....I have seen that a few times on here that people just uninstalled and reinstalled the software for the item in question and it fixed it...I guess it just sort of gets hung up...but glad to hear that you were able to fix your issue.  Hope all the rest of the things that may come up are that easy to fix....

---

### Post by nasrott on 2007-10-21
has anyone got a link to this file for reintalling the network and maybe some instructions also. One more thing I am getting a failed to initialize HAL error also not sure if this is connected with the missing network?

---

