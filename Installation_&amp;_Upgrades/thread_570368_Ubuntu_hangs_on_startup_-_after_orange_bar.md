---
title: "Ubuntu hangs on startup - after orange bar"
date: 2007-10-08
forum: Installation &amp; Upgrades
---

### Post by Isterklister on 2007-10-08
Hello,
I have a problem on starting my maschine. I did install ubuntu-7.04-alternate-amd64.iso and that went ok, but now I have to use _ubuntu-7.04-alternate-i386.iso_ (printer driver from Brother only works in i386 version). (I have a new Fujitsu Siemens ScaleoL so I can't start the LiveCD.)

Now my problem: The installation went OK but when Ubuntu are going to start it hangs (black screen) after orange bare are completed.

I can start in "recover mode" and there I can startx and everything are working. What could be my problem?

I have tried the ordinary things like noapic nolapic that solved others problems.

/Pelle

---

### Post by pay on 2007-10-08
I had the same problem on amd64 but not on i386. I got it to boot by removing the splash and quiet options from /boot/grub/menu.lst

BTW Welcome to Ubuntu Forums:)

---

### Post by Isterklister on 2007-10-08
Thank you, but it did not solve my problem. Any other good idea?

---

