---
title: "Xorg eating cpu cycles"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jwssr on 2010-03-29
Xorg 1.7.6 
2.6.32-16  _64
Gnome 2.29.92
nvidia  195.36.15
amd

cpu cycling between 2-104 (?)   on this process....just started today...maybe yesterday..

Im also running another box intel/ati graphics 3200 with new drivers (ok)  also doing the same thing...

anyone else seeing this...no threads here lately on this subject.

screenshot

---

### Post by t.n. on 2010-03-30
I have the same problem. It does not happen all the time I think, but once X has started using a lot of CPU it get worse over time. I have to reboot every few days (which I usually don't).

---

### Post by psyke83 on 2010-03-30
> **jwssr said:**
> Xorg 1.7.6 
2.6.32-16  _64
Gnome 2.29.92
nvidia  195.36.15
amd

cpu cycling between 2-104 (?)   on this process....just started today...maybe yesterday..

Im also running another box intel/ati graphics 3200 with new drivers (ok)  also doing the same thing...

anyone else seeing this...no threads here lately on this subject.

screenshot

Try to disable compositing (KDE's compositor or compiz; whichever is active on your system) and see if it helps.

---

### Post by jwssr on 2010-03-30
yes...Ive tried starting/stoping compositing...but thru gconf-editor...not thru preferences\appearances/visual effects...

gconf-editor  apps/metacity/general/compositing manager (check box)

If I try to activate visual effects  normal or extra...all sorts of weird action on screen...lots of screen off/on....icons popping up/off for 10/15 seconds....then a message that visual effects cannot be turned on. Reminds me of old days with windows getting a popup virus!!!!

admin/nvidia x server settings tells me that Im using driver 195.36.15 (current)
but if I go to admin/hardware drivers....it tells me "this driver is activated but currently not in use."  So, Im not sure.

all of this started after installing activity journal and docky.....on both machines...docky soes some strange stuff with screen..mainly
putting a very wide black border around wallpaper....popup states that docky needs compositing to run.....

process of elimination seems to point to docky.

I will reinstall a nightly build on my intel cpu/ati3200 box and see if anything changes.

---

### Post by Nexeh on 2010-04-04
I have noticed this same problem the last 2 days. It's driving me nuts because it renders my computer useless... I am going to be forced back to windows to get my work done. Someone find a fix and fast!

Xord process starts at 20% cpu at start-up/idle but easily hits 90% when opening simple applications such as a browser.

I have disables compiz saw no improvement.

Im on Karmic: Linux jeremy-desktop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

---

### Post by strobe on 2010-04-04
Have you tested just using the nouveau drivers out of the box?  I too have noticed with the nvidia 173 drivers cause 100% cpu usage while watching videos.  With the nouveau, cpu usage is around 55%.  This issue did not exsist in Karmic for me.  Lucid doesn't like my laptop running any 3d effects. With the nouveau running, Lucid has removed most of the flare that draws a demographic to run Ubuntu over Windows.  Linux 3D was already struggling to compete with the Windows OS, now with the current kernel, Ubuntu has made sure I can't even attempt 3d effects.

---

