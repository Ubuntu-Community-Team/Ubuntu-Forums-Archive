---
title: "no wired internet connection after upgrading to ubuntu 11.10"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by jsalz on 2011-10-26
Hello,

I have upgraded to ubuntu 11.10 and the wired connection does not work anymore (I can not connect to the internet). Suprisingly, the wireless works perfectly well...

I don't if it may be related, but during the installation I saw an error message on the terminal, saying:
E: /etc/*ca*-*certificates*/update.*d*/jks-keystore *exited* with code 1

Does anyone knows what to do ?

Many thanks in advance for your help,

Jsalz

---

### Post by jnorthr on 2011-10-26
Welcome aboard :KS

11.10 has not received the same amount of testing as 11.04 and may not have been tested for all combinations of hardware. Network access is typically one area where testing is lax as most testers do not have every combination of hardware in the world. They rely on people using ubuntu and reporting failed/slow/unworkable issues like this. If you still have internet access over wireless at least count your self lucky as you can still apply system upgrades that will eventually correct your issues. See Menu>Administration>Update manager which checks for new/revised logic and installs it where needed. 

At this point, i would just use the system as it is, unless you are prepared to roll up your sleeves and do some work isolating the conflicting issues. If you want to, you can start a terminal session Menu>Applications>Terminal then you can type commands to ubuntu. One command we use to see the audit log files that are written to for each event is the dmesg command. It will give a big list of messages but the messages at the bottom of the list are the newest and may offer clues as to why the conflict. Good luck.

---

