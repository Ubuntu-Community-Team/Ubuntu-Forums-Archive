---
title: "[SOLVED] Suddently my touchpad stopped working (not after any updates)"
date: 2008-10-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by olavjunior on 2008-10-29
When I started my laptop this morning, the touchpad was broken. I had put it into hibernation yesterday, and neither mouse nor touchpad would respond. Rebooted, and bluetooth mouse worked fine again, but NOT the touchpad!

I rebooted the machine many times yesterday after the last updates, so it's not due to them. 

I've added the xinput list

---

### Post by wgrant on 2008-10-29
It doesn't even work after you power it down and up again? What happens if you run 'xinput list-props' on the touchpad device?

---

### Post by olavjunior on 2008-10-29
Solved! Thanks for your tip, because there everything was fine!

I started thinking that it was very odd, and thought it might be a hardware switch. And it was! 

I was playing with short cut keys yesterday to create a trigger for toggling between displays, and then I must have had pushed the <fn>F9 key, witch apparently is a switch for toggling touchpad on/off. 

Nice :)

---

