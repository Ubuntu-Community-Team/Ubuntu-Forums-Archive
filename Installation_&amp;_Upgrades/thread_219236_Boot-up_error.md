---
title: "Boot-up error"
date: 2006-07-19
forum: Installation &amp; Upgrades
---

### Post by SpongeBob SquarePants on 2006-07-19
After installing my modem software, now when I boot up, it drops away from the ubuntu splash and comes up with an error. Problem is, it comes up and scrolls away so fast I can't read what it says. Is there any way I can slow things down in order to read what's going wrong...or does it log this information anywhere so I can take a look once I'm booted?

Thanks :-)

---

### Post by fadumpt on 2006-07-19
type dmesg in the terminal after you boot up and you can see all the messages generated at boot up.  

I'm going to venture a guess and say that the error is your modem trying to start up a connection and can't, much like your network card trying to get an IP address at boot up would cause it to say failed.  

I can't recall how (for some reason I frequent ubuntuforums when I'm at work and lack a ubuntu computer :-/) but you probably need to remove the modem from the boot up.

---

