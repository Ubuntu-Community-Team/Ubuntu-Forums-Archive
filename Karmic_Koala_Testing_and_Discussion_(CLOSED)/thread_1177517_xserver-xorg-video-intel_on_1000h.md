---
title: "xserver-xorg-video-intel on 1000h"
date: 2009-06-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nyarnon on 2009-06-03
Hi guys,

Just upgraded to flavor 30 kernels and guess what? xserver-xorg-video-intel gives me pain. As soon as I login X seems to segfault and returns to the login manager. Seen from syslog we have:

Jun  3 17:12:31 roelf-laptop kernel: [   68.708567] Xorg[4585]: segfault at 0 ip 08135150 sp bfe8c4c4 error 4 in Xorg[8048000+1c3000]
Jun  3 17:12:32 roelf-laptop kernel: [   68.800889] [drm:i915_get_vblank_counter] *ERROR* trying to get vblank count for disabled pipe 0
Jun  3 17:12:32 roelf-laptop gdm[4580]: WARNING: gdm_slave_xioerror_handler: Fatale X-fout - :0 wordt opnieuw gestart 

So as soon as I remove xserver-xorg-video-intel version: 2:2.7.99.1+git20090602.ec2fde7c-0ubuntu1

I'm able to run in low graphics mode. As soon as I install the xdriver again we segfault again. 

Anyone experiencing the same problem? I hate to go lowres till the rc :-)

---

### Post by TrueTom on 2009-06-03
I have the same problem, though, it usually works after a few tries...

---

### Post by nyarnon on 2009-06-03
> **TrueTom said:**
> I have the same problem, though, it usually works after a few tries...

Your right didn't notice that, I'm not the type to try at least 5 times :-) You a persistent guy I guess :-)

---

### Post by TrueTom on 2009-06-03
> **nyarnon said:**
> Your right didn't notice that, I'm not the type to try at least 5 times :-) You a persistent guy I guess :-)

I would call it desperate but I'm fine with persistent... ;)

---

### Post by meeples on 2009-06-03
ok im not sure if this is the same because im a bit noobish. but if i boot into any kernel less the 2.6.30-6 ( i think thats right) i get "ubuntu is running in low graphics mode"

 but when in the previous stated kernel everytime i try to play teeworlds i get taken to the login screen

 (and i think it happens when my display goes to sleep to because whenever i go away for a while i come back and my pc is at login screen.)

---

### Post by Foaming Draught on 2009-06-03
Similar bug since yesterday.  At screen idle (which I've now disabled in Power Management), at running Atomic Tanks in full screen (you see my priorities ;)  ), at expanding a .mpg or other video file to full screen and at running a youtube video full screen, I get kicked out to the log-in screen.  I would post or join a bug, but I don't know what output Launchpad wants.

---

### Post by nyarnon on 2009-06-04
I now filed a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/383468](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/383468)

chip in please.

---

### Post by nyarnon on 2009-06-04
After the compiz update of today the login is no longer a problem, but now the screen blanks soon after login and pressing whatever key will not bring it up again. I have screenblanking stopped in energy and screensaver settings but this actually seems to be ACPI related considering:

Jun  4 08:47:16 roelf-laptop kernel: [  195.745050] ACPI: EC: missing confirmations, switch off interrupt mode.
Jun  4 08:47:17 roelf-laptop kernel: [  196.261095] ACPI Exception (evregion-0422): AE_TIME, Returned by Handler for [EmbeddedControl] [20090
320]

---

### Post by nyarnon on 2009-06-04
Seens that the update of the gnome power manager took care of the last problem.

---

### Post by geojorg on 2009-06-04
The bug you report is a duplicate of this one [383129]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/383129") is confirmed and it has currently a workaround, i had the same problem in my Dell Inspiron but the workaround works fine just by now.

---

### Post by Foaming Draught on 2009-06-04
Fixed with this morning's xorg update.  Thank you anonymous devs  :D

---

