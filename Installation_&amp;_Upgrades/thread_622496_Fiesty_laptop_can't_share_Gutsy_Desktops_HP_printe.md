---
title: "Fiesty laptop can't share Gutsy Desktops HP printer"
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by Buster95 on 2007-11-24
I'd like to share my old HP Laserjet 4L printer, connected to my Desktop (Gutsy) with my laptop (Feisty).
On the desktop, I have set System\Admin\Printing\policies to "Enable", "Accepting jobs" and "Shared".
Under "Settings", it showed the device URL as "parallel:/dev/lp0 which I assume is the local host URL. I then selected "Change" on the URL Change button in order to identify the actual URL and path of the printer. To my surprise, a remote printer appeared in the "Server settings" section on the left hand side of the configuration box. It showed "ipp://192.168.0.4:631/printers/LaserJet-4L" as the URL.

On the laptop, I have set System\Admin\Global to "Detect LAN printers" and "Share printers".
I copied the URL displayed on the Desktop into the Laptop and tried a test page. The laptop shows the printer icon and clicking on the icon shows 2 pages in the print queue. The printer does not receive anything.

Any suggestions?
Thanks

---

