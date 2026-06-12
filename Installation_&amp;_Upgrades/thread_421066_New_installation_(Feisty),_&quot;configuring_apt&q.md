---
title: "New installation (Feisty), &quot;configuring apt&quot; problem, oddities with network"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by klimbermann on 2007-04-24
I am trying to get Ubuntu Feisty running on a desktop machine. Every time I tried, the installation process hanged at "configuring apt" (some 82%, if I remember correctly). So, I finally switched with Ctrl-Alt-F2, killed the processes trying to access the internet and switched back. Did it again soon after, while downloading language packs. Installation completed, I reboot and Ubuntu starts up flawlessly.

Sidenote - I am not behind a proxy, just a router (assigns addresses via DHCP and both Ubuntu liveCD and alternate install CD say that autoconfiguration has succeeded. I tend to believe them).

Now, on to the problem - I can successfully ping everything, but surfing the web succeeds only on servers outside my home country (Estonia; I find it *very* strange). Apt doesn't work at all - I try to configure software sources, order to select the best servers and it always fails. I can access all the servers with my browser, but apt can't download the index file.

Any ideas?

---

### Post by dcstar on 2007-04-24
> **klimbermann said:**
> I am trying to get Ubuntu Feisty running on a desktop machine. Every time I tried, the installation process hanged at "configuring apt" (some 82%, if I remember correctly). So, I finally switched with Ctrl-Alt-F2, killed the processes trying to access the internet and switched back. Did it again soon after, while downloading language packs. Installation completed, I reboot and Ubuntu starts up flawlessly.

Sidenote - I am not behind a proxy, just a router (assigns addresses via DHCP and both Ubuntu liveCD and alternate install CD say that autoconfiguration has succeeded. I tend to believe them).

Now, on to the problem - I can successfully ping everything, but surfing the web succeeds only on servers outside my home country (Estonia; I find it *very* strange). Apt doesn't work at all - I try to configure software sources, order to select the best servers and it always fails. I can access all the servers with my browser, but apt can't download the index file.

Any ideas?

If you killed the apt configuration task then there is a very good chance that it isn't configured correctly.

If you can reinstall the apt package then things may get fixed (assuming that it can be done via the CD).

---

### Post by klimbermann on 2007-04-24
but what about the inability to browse network sites?

the computer gets an IP correctly via DHCP, has correct DNS servers and everything. I can, for example, open [www.google.com](www.google.com) in my browser, or almost any of the ubuntu http mirrors, yet I cannot even open my router's configuration panel (which is a http site in the local network) or most of the sites in Estonia.

---

