---
title: "How can I upgrade form Ubuntu 10.10 to Ubuntu 11.04"
date: 2011-04-15
forum: Installation &amp; Upgrades
---

### Post by Uewd on 2011-04-15
I want to perform an upgrade from Ubuntu 10.10 to Ubuntu 11.04 without reinstalling Ubuntu. How can I do this?

---

### Post by oldos2er on 2011-04-15
11.04 is still beta, and should be run for testing purposes only.

Run ```
update-manager -d
``` in a terminal.

---

### Post by Uewd on 2011-04-15
Will this apply to 11.04 Final (I want to do this when it is released)?

---

### Post by Rubi1200 on 2011-04-15
The same procedure can be applied when the final version is released. 

But as oldos2er pointed out, Natty is in beta and that means bugs. 

It should only be used for testing at this time.

---

### Post by Dutch70 on 2011-04-15
> **oldos2er said:**
> 11.04 is still beta, and should be run for testing purposes only.

+1

If you have trouble with it, and you probably will. It's difficult at best to get help with. Very few people have it installed & most of the ones that do, use a stable version as their main OS.

---

### Post by wrldwzrd89 on 2011-04-15
I just attempted to install Ubuntu 11.04 beta2 64-bit on a PowerSpec B707, upgraded to 8GB RAM, twice. Both times, the installer process failed midway through, without reporting an error or even generating a log file I can look at - my computer just spontaneously rebooted, instead. Such a shame that the installer is crashing on my HW - I really wanted to test the next Ubuntu.

---

### Post by Dutch70 on 2011-04-15
> **wrldwzrd89 said:**
> I just attempted to install Ubuntu 11.04 beta2 64-bit on a PowerSpec B707, upgraded to 8GB RAM, twice. Both times, the installer process failed midway through, without reporting an error or even generating a log file I can look at - my computer just spontaneously rebooted, instead. Such a shame that the installer is crashing on my HW - I really wanted to test the next Ubuntu.

Try it from the live cd/usb. Report any bugs you find, and maybe they'll have it resolved before 11.04 is officially released.

---

### Post by wrldwzrd89 on 2011-04-15
> **Dutch70 said:**
> Try it from the live cd/usb. Report any bugs you find, and maybe they'll have it resolved before 11.04 is officially released.
I am trying it from the live CD. It works for a while, then... KABOOM, my computer reboots on its own.

---

### Post by Dutch70 on 2011-04-15
Sorry I should have mentioned this earlier. It's best if you start your own thread in the Natty Testing & Discussion section of the forum. 

To get there, go to Development & Programming and then, Natty Narwhal Testing and Discussion.

---

### Post by KegHead on 2011-04-15
Hi!

I used the kansasnoob way;

sudo apt-get update && sudo apt-get dist-upgrade

Worked perfectly.

KegHead

---

### Post by Uewd on 2011-04-16
Thank you all for replying. I got the answer.

---

### Post by oldos2er on 2011-04-16
> **KegHead said:**
> sudo apt-get update && sudo apt-get dist-upgrade


Are you sure? apt-get dist-upgrade doesn't upgrade to a newer Ubuntu version, despite its name.

---

