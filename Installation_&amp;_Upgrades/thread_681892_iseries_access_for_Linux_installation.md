---
title: "iseries access for Linux installation"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by abhver on 2008-01-29
I have installed iseries access for Linux on my Ubuntu 7.04. I converted the .rpg package to .deb using alien. And installed .deb by just double clicking it. I got the it installed successfully. But then I created a launcher on desktop with /opt/ibm/iSeriesAccess/bin/setup5250 in command. 

When I click it "nothing" happens. Can anyone help?

---

### Post by LanceM on 2008-02-12
You most likely need to give the launcher parameters. Here is my setup:

/opt/ibm/iSeriesAccess/bin/ibm5250 10.1.1.5 -geometry 9999x9999+0+0 -title DPLANCE1 -DISPLAY_NAME "DPLANCE1 DPLANCE2" -LANGID en_US

My parameters are server_ip window_size title display(this is session id) and language.

---

