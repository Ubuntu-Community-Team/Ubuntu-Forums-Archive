---
title: "Installation on a Dell 9200"
date: 2005-03-12
forum: Installation &amp; Upgrades
---

### Post by jodde on 2005-03-12
It's a known problem that the installer for dell computers in general. It freezes when after HAL starts at libsys i think.

* Restarting system message bus ...
* Stopping Hardware abastarcation layer... [ok]
* Starting hardware abstaraction layer ... [ok]

Then I restart and it freezes at "starting PCMCIA".

I tried to rmmod b44, adding acpi_irq_isa=7, but nothing works.

I'm very new to linux/unix so can anyone please give me some detailed steps on how to cope with this?

thanks.

---

### Post by jodde on 2005-03-12
I finally figured it out. I installed linux -custom, to get a plain text based installation and then I used aptitude to install the packages but I excluded HAL and its dependencies.

Now I'm in Ubuntu and it's working great.

---

