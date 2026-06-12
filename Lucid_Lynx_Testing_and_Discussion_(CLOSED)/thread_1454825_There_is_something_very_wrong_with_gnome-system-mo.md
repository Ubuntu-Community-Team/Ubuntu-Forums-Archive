---
title: "There is something very wrong with gnome-system-monitor sometimes"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-04-15
the problem is with the cpu column every now and then the resources tab show 100% cpu because maybe software I'm trying to install and etc like utorrent via wine but in the cpu column in processes there is nothing i can see the little blue windows at the bottom panel
that i added there completely blue but see nothing in processes. 

in fact virtually nothing move in processes for instance i now use Firefox but in processes 
everything except gnome-system-monitor is in state sleep so what is going on here?

---

### Post by Luffield on 2010-04-15
I'm not sure I understand what you mean, but:
There are proccesses that you won't see in the system monitor. If for example, the kernel is using 100% of the CPU for some reason, you won't see it in this list (I think it only shows the current user's proccesses). If it happens to you, you can use the command top in the terminal.

---

### Post by BrokeMahPC on 2010-04-15
Just been staring at my CPU history for several minutes - no jumps to 100% - this does not happen to me. I imagine it might if you were installing something which makes sense.

In processes, Firefox does not use cpu resources until you do something with it. eg open a web page - then it uses the cpu.
When it's idle with a web page open - it's just using RAM.

Are you still using the unsupported kernel aviramof? I remember from past posts you preferred to use 2.6.33-xx.

---

### Post by aviramof on 2010-04-15
at the moment i'm using 2.6.32-21 and it just happen again now for no apparent reason forget what i said about utorrent and wine  it just goes up to 100% and stayed there and the problem is that even log off doesn't fix it you need to restart to fix it and there is no process to close so maybe it 
is a problem with the new kernel. 

and by the way that is why i prefer to use 2.6.33 because it's stable once the fglrx problem be solved with this kernel i would 
resume using it at least until final lucid kernel be released.

---

### Post by mick222 on 2010-04-20
I have a similar problem compiz was crashing "i was losing the buttons on my windows and the system was slowing to a crawl " when i checked system monitor even with effects off it was using 70% of my cpu according to top the rest was being used mostly by dbus-daemon. I am using the xorg egers ppa for my radeon graphics card  could this be affecting it. When i stopped system monitor cpu usage seemed to go back to a reasonable level.

---

