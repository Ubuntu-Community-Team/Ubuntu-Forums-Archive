---
title: "Possible Hibernation Bug"
date: 2008-09-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by zoomy942 on 2008-09-27
As of Sept 26, I believe I found a hibernate bug.

What happens is when I use hibernate on my HP 2710p tablet PC, once it wakes up the battery level is stuck forever - meaning, if i hibernate her at 44% battery and charge it overnight, the next morning when i wake her up, the battery life is still stuck at 44%; even though the charge light is off (which means its fully charged).

Anyone else notice this?

---

### Post by zoomy942 on 2008-09-28
So i have confirmed it with Stand By mode too.

So - 2 questions... should i report this bug on the launchpad?  i looked around and saw some mention of it, - but i feel its a pretty big bug (if it isnt already known)

next - would the kubuntu alpha have the same trouble? i am curious becasue i know they use different power managers, but if the info comes from some sort of ACPI, then they are probably the same.

can anyone else reproduce this bug too?  i was using my tablet earlier, and it said i had 34% left but my battery light was flashing.  i figured i would wait to see who was right and sure enough, my tablet just shut off.

---

### Post by zoomy942 on 2008-09-28
i found a few posts online that said if i reinstalled the power manager from a deb and not from the package manager it works better.  i have done this and will report back soon.  

heard about people using the kde manager also - i dont know how i wouold do that.  simply unchec the gnome ones in the package manager and install the kde one?  will that hurt anything?

---

