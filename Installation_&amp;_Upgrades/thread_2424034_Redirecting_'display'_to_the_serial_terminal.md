---
title: "Redirecting 'display' to the serial terminal"
date: 2019-08-02
forum: Installation &amp; Upgrades
---

### Post by carolog on 2019-08-02
I recently bought the [APU2]("https://www.pcengines.ch/apu2.htm") from PCEngines on which I intend to install Ubuntu Server 18.10. This hardware does not support any kind of display and instead uses its serial terminal to act as the display. Are there any files that I can modify in the official 18.10 server iso to ensure that the VGA stream is off and specify serial terminal parameters?

---

### Post by rsteinmetz70112 on 2019-08-02
What kind of storage do you intend to use?
 
You could install Ubuntu on the storage then move the storage to the board. Then access the board using ssh and modify that install to use a tty on the serial port. That would require having an amd64 computer to do the initial install.

---

