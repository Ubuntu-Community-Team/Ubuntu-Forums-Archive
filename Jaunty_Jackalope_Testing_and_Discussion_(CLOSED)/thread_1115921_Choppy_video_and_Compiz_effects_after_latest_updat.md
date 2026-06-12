---
title: "Choppy video and Compiz effects after latest update"
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by lakerssuperman on 2009-04-04
After the latest round of updates my desktop feels sluggish in terms of opening new menus and windows.  Also, when I play an video, either through Totem or Vlc it is very choppy.  I am running a Radeon 4870 with the fglrx drivers.  I have tried disabling Compiz but the choppy video remains.  I will probably just wait for the next round of updates to see if the issue is resolved but I was just wondering if anyone else is having these issues and if they knew of a workaround.  Thank you.

---

### Post by zaarin on 2009-04-04
I have the same problem.  Entire machine lags badly when performing the simplest of tasks.  I have had problems with this machine from the get-go because I guess my video card is a pile of junk, but things are significantly worse since the update.

---

### Post by lakerssuperman on 2009-04-04
Mine was running very smooth before the update.  It was even more smooth than 8.10 was for me.  I'm going to see if something is using a lot of the CPU, but I have a quad core so I'm not sure if that would be an issue either.

---

### Post by bcat on 2009-04-06
Same problem here. Compiz works, but it's horribly "laggy". Simple things like restoring windows after clicking the Show Desktop button or resizing a window take several seconds. This is just insane.

It doesn't seem to be a CPU usage problem, as far as I can tell. This is on a fairly new laptop running Jaunty 64-bit with an ATI Mobility Radeon HD 3650 and the fglrx driver. I'll try switching back to xserver-xorg-video-ati with Metacity's compositor and see if that makes a difference...

---

### Post by zika on 2009-04-06
> **bcat said:**
> Same problem here. Compiz works, but it's horribly "laggy". Simple things like restoring windows after clicking the Show Desktop button or resizing a window take several seconds. This is just insane.

It doesn't seem to be a CPU usage problem, as far as I can tell. This is on a fairly new laptop running Jaunty 64-bit with an ATI Mobility Radeon HD 3650 and the fglrx driver. I'll try switching back to xserver-xorg-video-ati with Metacity's compositor and see if that makes a difference...
it will make a world of difference! I have HD 3650.  ... be sure to wipe out all of fglrx in the process including kernel ... and not to use compositing in metacity ...
I start to wonder when we are going to see some improvement for our card ...

---

### Post by oldrocker99 on 2009-04-06
Interesting...I have no video drivers installed yet (building ATI fglrx packages as I type), but my wobbly windows are as snappy, or snappier than ever. I'll see what happens after I install the packages.

:guitar:

---

### Post by oldrocker99 on 2009-04-06
OK, when I tried to install the ATI packages, I was informed that newer versions existed in the repositories. So, I went into Synaptic and installed them. No graphics at bootup.

So, I dropped into a root shell prompt and installed them, downgrading the packages, and now I have graphics, but no Compiz at all ("Desktop effects could not be enabled").


:-k

:guitar:

---

### Post by screaminj3sus on 2009-04-06
> **bcat said:**
> Same problem here. Compiz works, but it's horribly "laggy". Simple things like restoring windows after clicking the Show Desktop button or resizing a window take several seconds. This is just insane.

It doesn't seem to be a CPU usage problem, as far as I can tell. This is on a fairly new laptop running Jaunty 64-bit with an ATI Mobility Radeon HD 3650 and the fglrx driver. I'll try switching back to xserver-xorg-video-ati with Metacity's compositor and see if that makes a difference...

Same thing here with an  mobility 2600 unminimizing a window takes 3 freaking seconds.

---

### Post by Twitch6000 on 2009-04-06
From the looks of it,it seems this is a ATI problem.

Can anyone with a NVIDIA card claim they have the same problem?

I have a NVIDIA 8200m g and I am not having this problem.

However I am having a similar one where when opening one or two programs my cpu usage skyrockets.

---

### Post by macstevejb on 2009-04-06
I have an nvidia card which uses the 96 driver and dont have any problems with compiz even after the latest updates.

regards,

---

