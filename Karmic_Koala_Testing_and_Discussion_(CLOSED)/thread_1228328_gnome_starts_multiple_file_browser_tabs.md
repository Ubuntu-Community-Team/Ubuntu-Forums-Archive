---
title: "gnome starts multiple file browser tabs"
date: 2009-07-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by doctordruidphd on 2009-07-31
I wanted to stop gnome from displaying icons on the desktop, so I opened gconf-editor and unchecked the "visible" boxes under apps/nautilus/desktop. That got rid of the icons, but now when gnome starts up, it also starts an apparently infinite number of "open file browser" icons in the bottom panel. I can make them go away by issuing several "pkill nautilus" commands. I tried setting the gconf options back  to where they were; this did not help. I also tried copying over the .gnome and .gnome2 directories from another installation that works OK, but this did not help either. This problem does not exist in my 9.04 installation. I couldn't find anything about this by searching. Any ideas what's wrong and how to fix? 
P.S. I'm primarily a kde user, so not all that familiar with gnome tricks. Thanks in advance.

---

### Post by hetx on 2009-07-31
Not sure how to fix your latter problem, but not showing icons on desktop is easiest done by apps -> nautilus -> preferences -> show desktop UNCHECK in gconf-editor.

I have had your problem too when I installed Gnome in Arch, could it be "All windows are browsers?" I never fixed it and I switched distro on it so I can't check.

---

### Post by Regenweald on 2009-07-31
This is an old bug that i assumed was fixed as i experienced it in the Jaunty development cycle but it went away late in one of the alphas. It returned in Karmic which was suprising to me, but that thread i started is laying somewhere on the 42nd page of this sub forum i think.

I can only assume that it is something that occurrs when we sync from debian sid. The devs are aware and will fix it i guarantee :) just give it time. The re-occurrence is puzzling to me though.

Edit: Reports.

[https://bugs.launchpad.net/nautilus/+bug/325973/comments/0](https://bugs.launchpad.net/nautilus/+bug/325973/comments/0)

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/332765](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/332765)

---

### Post by doctordruidphd on 2009-07-31
Thanks for the suggestions and info. 

The problem arises when the gconf-editor > apps > nautilus > preferences > show_desktop box is unchecked. 

I did some experimenting, and found that I can make the problem go away by unchecking the gconf-editor > apps > nautilus > preferences > exit_with_last_window box.

At that point, the problem does not appear when unchecking the show_desktop box.

For now, working.

---

### Post by Regenweald on 2009-07-31
> **doctordruidphd said:**
> Thanks for the suggestions and info. 

The problem arises when the gconf-editor > apps > nautilus > preferences > show_desktop box is unchecked. 

I did some experimenting, and found that I can make the problem go away by unchecking the gconf-editor > apps > nautilus > preferences > exit_with_last_window box.

At that point, the problem does not appear when unchecking the show_desktop box.

For now, working.
No such luck on my end with that solution, but i'm glad you found a work around.

---

### Post by drs305 on 2009-07-31
> **Regenweald said:**
> No such luck on my end with that solution, but i'm glad you found a work around.

I had the 'infinite' nautilus windows during my initial installs of both Jaunty and Karmic. 

The immediate solution (to stop the spawning) is to open terminal (Alt-F2) and enter "killall nautilus". I usually have to run it more than once (I may just be impatient, but eventually the windows close).

The permanent solution for me is to edit this file:
```
gksudo gedit /usr/share/applications/nautilus.desktop
```
and change "X-GNOME-AutoRestart=true" to
> X-GNOME-AutoRestart=false 

---

### Post by Regenweald on 2009-07-31
> **drs305 said:**
> I had the 'infinite' nautilus windows during my initial installs of both Jaunty and Karmic. 

The immediate solution (to stop the spawning) is to open terminal (Alt-F2) and enter "killall nautilus". I usually have to run it more than once (I may just be impatient, but eventually the windows close).

The permanent solution for me is to edit this file:
```
gksudo gedit /usr/share/applications/nautilus.desktop
```
and change "X-GNOME-AutoRestart=true" to

Thanks, worked perfectly!

With this change, anything to look out for with future updates ?

---

### Post by drs305 on 2009-07-31
> **Regenweald said:**
> Thanks, worked perfectly!

With this change, anything to look out for with future updates ?

I haven't experienced any noticeable problems and I don't think the problem reoccurs with kernel updates. I have had it happen in karmic on three occasions but I don't think it was just a simple kernel update - I believe I was restoring an image from before I changed that file.

---

