---
title: "Very odd mouse issue"
date: 2010-04-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by myurko on 2010-04-07
This issue seems to occur randomly on my machine which is running a fully updated Kubuntu Lucid Beta 1. It also occurs in different apps using both GTK and Qt. The mouse will seem to get stuck in a selection mode. I can select text within a text box and even access context menus via right click. However, the left mouse button won't work anywhere except in context menus launched by the right mouse button and to select text in the original text box. I know that this is not a mouse hardware issue since it occurs with multiple mice and even across synergy. Has anyone encountered this issue? Does anyone know of a fix for this?

---

### Post by lavinog on 2010-04-07
I have experienced this while testing lucid in a kvm-qemu virtual machine.
The main issue was that the mouse was causing high cpu usage, but I was also never able to use copy and paste from the right click menu due to the behavior you described.

My issue may not be exactly the same as yours, but I was able to fix it by removing xserver-xorg-input-vmmouse and restarting.  See if that does anything for you.

---

### Post by myurko on 2010-04-09
Thanks for the suggestion, but it didn't work for me. I think that I'll just downgrade back to 9.10. Its just a shame because my favorite feature is the ability to automatically put two windows side by side.

---

