---
title: "Wireless lost on Aspire One ZG5 after suspend"
date: 2009-08-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kozimodo on 2009-08-14
Using a live usb of the current alpha, I thought I'd try out karmic on my Aspire One to see how support for my Aspire was shaping up.  Wireless seemed to work great with the LED blinking etc.  But when I tried suspend, my AAO eventually came back up but wireless was dead.  I had to 'sudo rmmod ath5k ath' and then 'sudo modprobe ath5k' to get wireless back up.

---

### Post by jbernardo on 2009-08-14
On my AA1 110L wireless works well, and even after suspend/resume. And now plasma-widget-networkmanagement has been fixed, wifi is working as expected.

---

### Post by taavikko on 2009-08-14
Running UNR on aao110 and the suspend works fine, ath5k driver gets automatically reloaded after it.

Check dmesg for starters for any clues.

---

### Post by kozimodo on 2009-08-14
Ok, tried it twice more and wireless came back fine after suspend.  Maybe I'll go ahead and upgrade...

---

