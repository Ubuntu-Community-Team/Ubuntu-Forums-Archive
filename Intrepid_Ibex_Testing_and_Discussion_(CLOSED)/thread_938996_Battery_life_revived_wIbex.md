---
title: "Battery life revived w/Ibex"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by darco on 2008-10-05
I have a 2yr old Toshiba Satellite laptop running HH. The last maybe 8 mos. I noticed that my battery will drain when its unplugged. I normally run my laptop 90% plugged in. I assumed the battery was at the ends of its life. 
I just upgraded to Ibex and now after booting up I have 90% battery life? Awesome!....So I take it that the new kernel is responsible for this?
Keep up the good work!

darco

---

### Post by Delvien on 2008-10-05
> **darco said:**
> I have a 2yr old Toshiba Satellite laptop running HH. The last maybe 8 mos. I noticed that my battery will drain when its unplugged. I normally run my laptop 90% plugged in. I assumed the battery was at the ends of its life. 
I just upgraded to Ibex and now after booting up I have 90% battery life? Awesome!....So I take it that the new kernel is responsible for this?
Keep up the good work!

darco

I don't think an OS will just revive a battery, its probably reporting the wrong %.

---

### Post by darco on 2008-10-05
> **Delvien said:**
> I don't think an OS will just revive a battery, its probably reporting the wrong %.

must be my imagination then :)

darco

---

### Post by shuttleworthwannabe on 2008-10-05
install [COLOR=Red]**powertop**[/COLOR] from repos and run in terminal as root; check the processes causing high power usage in AC unplugged mode. You can check battery health in this way as well. Follow the suggestions in the output and check if battery stamina improves.

---

### Post by eldragon on 2008-10-05
there are some improvements in the newer kernel related to power savings..

i dont know if they are enabled by default, but i managed to get a kick of my battery with those patches applied to the hardy kernel and enabled during battery usage.

---

