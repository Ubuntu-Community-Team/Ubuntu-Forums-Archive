---
title: "GIMP installation"
date: 2012-12-09
forum: Installation &amp; Upgrades
---

### Post by npcnitc on 2012-12-09
I was trying to install GIMP from the Software center on 10.04. However it was showing the message ''The action would require the installation of packages from not authenticated sources.'' when I gave the install option. Then when I gave OK the installation didn't get through. I then tried using the Command prompt  which also didn't work
Please suggest a way out
NPC

---

### Post by alexandari on 2012-12-09
post the output of the command prompt here when you try to install it

---

### Post by ibjsb4 on 2012-12-09
Hi npcnitc, welcome to the forums  :)

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get update
```

And post any errors.

---

### Post by mcduck on 2012-12-09
The warning about "not authenticated sources" is usually a result from adding a new software repositor, but not adding the signing key for it. If you do that, you'll get a warnign every time you try to install or update something, regardless if it comes from that partivluar repository or some other one.

Synaptic, and apt-get from a terminal, allow you to continue regardless of the warning. But of course the proper way to slve the issue is to add the missing key so that the packages can be verified.

---

