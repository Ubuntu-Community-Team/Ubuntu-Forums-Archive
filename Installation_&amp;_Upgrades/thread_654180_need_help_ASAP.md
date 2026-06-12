---
title: "need help ASAP"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by c0nka16 on 2007-12-30
hello i installed ubuntu with alternate installer becouse live cd didnt work it installed successfully. but everytime i boot up ubuntu it come up a black screen with ubuntu words in the middle and a progress bar which is normal but when it has loaded it goes on to a black screen ... could someone help
i have a compaq presario sr1619uk computer with ATI RADEON XPRESS 200 series
thanks in advanced

---

### Post by calicat on 2007-12-30
That is exactly what is happening to me so I hope you get the info you need!  Good luck to ya :-)

---

### Post by c0nka16 on 2007-12-30
cheers mate

---

### Post by c0nka16 on 2007-12-30
anyone please

---

### Post by Partyboi2 on 2007-12-30
I would try booting without splash and see what happens. You can do this by pressing Esc to enter grub menu when your puter is booting and highlighting the ubuntu kernel you normally boot into and press "e" then highlight the one starting with "kernel" and press "e" again then at the end of the line you will see "splash" replace "splash" with nosplash. then press "enter" then "b" to boot.
If that works you will need to add that to grub menu.list so it happens all the time.
When you get the blank screen are you able to get to a terminal? (Ctrl+Alt+F1-F6)

---

### Post by c0nka16 on 2007-12-30
and it should be done

---

### Post by alitanveer on 2007-12-31
I had the same problem with a HP laptop. I assume that the livecd would blank out after loading. The best way to fix this is to insert the live disc and when you get to the main menu, hit F6 then type in "noapic irqpoll noirqdebug" without the quotes. Then press Enter. You should boot into the livecd fine with that and then install ubuntu from there. Hope it works out.

---

