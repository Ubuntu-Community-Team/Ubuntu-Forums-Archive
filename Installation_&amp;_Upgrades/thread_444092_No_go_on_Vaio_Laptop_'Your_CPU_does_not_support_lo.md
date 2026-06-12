---
title: "No go on Vaio Laptop: 'Your CPU does not support long mode. Use a 32bit distribution."
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by jordanm on 2007-05-15
I just got a new Sony Vaio VGN-SZ240P laptop with 1.83ghz Core Duo. I am trying to install Ubuntu 7.04 using the AMD64-desktop cd, but get the error "[SIZE=-1]Your CPU does not support long mode. Use a 32bit distribution." From searching it seems that I may need to disable acpi, but anyone else encounter this bug or have any suggestions?

Thanks,
Jordan
[/SIZE]

---

### Post by jordanm on 2007-05-15
Trying to start with acpi=off did nothing. Does anyone have any ideas? When I searched, it seems that all of these problems were related to trying 64-bit OS on a 32-bit processor, but my processor should be 64-bit.

---

### Post by heimo on 2007-05-15
Not a solution - but a suggestion to try latest BIOS:[B]
[http://209.85.129.104/search?q=cache:1COilEdMQ8cJ:episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/567006164831+sony+vaio+%22Your+CPU+does+not+support+long+mode.+Use+a+32bit+distribution.%22&hl=fi&ct=clnk&cd=1&gl=fi]("http://209.85.129.104/search?q=cache:1COilEdMQ8cJ:episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/567006164831+sony+vaio+%22Your+CPU+does+not+support+long+mode.+Use+a+32bit+distribution.%22&hl=fi&ct=clnk&cd=1&gl=fi")

[/B]

---

### Post by jordanm on 2007-05-15
I was looking around and it seems that the Core Duo is 32-bit, whereas the Core 2 Duo is 64-bit. Oh well, guess I am stuck with 32-bit then.

---

### Post by heimo on 2007-05-15
> **jordanm said:**
> I was looking around and it seems that the Core Duo is 32-bit, whereas the Core 2 Duo is 64-bit. Oh well, guess I am stuck with 32-bit then.

Yeah, seems like that's the reason:
[http://en.wikipedia.org/wiki/Intel_Core](http://en.wikipedia.org/wiki/Intel_Core)

---

### Post by jordanm on 2007-05-15
I saw that wikipedia page too. Oh well, I paid $799 for my brand new Sony VGN-SZ240P, so I supposed I can't really complain...

---

