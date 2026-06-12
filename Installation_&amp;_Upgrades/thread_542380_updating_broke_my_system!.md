---
title: "updating broke my system!"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by stooge4ever on 2007-09-03
I was out of town for two weeks on vacation. My computer was off in the interim, as well as the power strip, so no power flowed to it.

i returned, turned on my computer, and saw a heckuva lot of updates from those two weeks i was gone. i updated my system, thinking maybe something might be better. nope! everything's broken!

compiz-fusion won't work - compiz isn't even running (i can't move windows using alt+left click).
sound is very distorted after going into standby.
the worst one is, i can't print on my epson stylus c84! something's wrong here, and i don't know what to do...

help!

---

### Post by merlinus on 2007-09-03
If possible, you can boot from the previous kernel listed in grub and see if these things work again.

-merlin

---

### Post by Pumalite on 2007-09-03
Boot with the old kernel from the Grub menu.

---

### Post by limemonkey on 2007-09-03
Similar (worse?) problem here with 2.6.20-16-generic, i had to select 2.6.20-15-generic from the menu. It gets stuck on a black screen with a blinking cursor. I will try to uninstall -16 now and wait for the next kernel upgrade...

Acer Aspire 5500 series laptop with fglrx, ipw2200

---

### Post by mayday73 on 2007-09-03
I also updated yesterday and found that resolution and firefox did not work well when 2.6.20-16-generic was selected.
To access websites by using firefox, I had to select 2.6.20-15-generic instead.
Similar problems occurred many times when updating in the past. Since then,  I became afraid of updating ubuntu and hesitated to recommend linux to others although Ubuntu was more easy to use than other distros.

---

### Post by stooge4ever on 2007-09-04
kernel switch did nothing. i tried two kernels - -16-lowlatency and -15-generic, both to no avail. actually, sound issue might've gotten worse. compiz is still fried, as well as printing. for printing, i know i'm using a hub - could that be an issue? it wasn't when i left...

---

