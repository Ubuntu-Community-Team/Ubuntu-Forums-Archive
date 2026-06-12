---
title: "No Internet"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jigglypuff on 2009-10-18
Today I restarted my computer running Ubuntu 9.10 Beta and when I rebooted I had no Internet Connection. I checked all the wires and everything. BTW I have DSL
and a Compaq Presario Desktop

---

### Post by shafin on 2009-10-18
care to post more details? On your internet connection and stuff.

---

### Post by jigglypuff on 2009-10-18
More Details Posted

---

### Post by Vanishing on 2009-10-18
> **jigglypuff said:**
> More Details Posted

detail as in:
what do you mean by no internet, any error messages?

---

### Post by jigglypuff on 2009-10-18
When I click on the Network Manager Applet Its says 
[SIZE="4"]Wired Network[/SIZE]
[SIZE="3"]*Device not Managed*[/SIZE]

---

### Post by Marat89 on 2009-10-18
try "sudo pppoeconf" in the terminal.
afaik the nm-applet is broken for dsl connections.

pppoeconf should work just fine

---

### Post by jigglypuff on 2009-10-18
pppoeconf did not work :(

---

### Post by ubu-for on 2009-10-18
Had the same problem with Jaunty.

Try [this solution]("http://ubuntuforums.org/showpost.php?p=6855351&postcount=15")!

P.S. [Duplicate bug]("http://ubuntuforums.org/showthread.php?t=1283146").

---

### Post by jigglypuff on 2009-10-18
ubu-for Thanks for that. I rebooted and everything started working! Thanks!! :)

---

