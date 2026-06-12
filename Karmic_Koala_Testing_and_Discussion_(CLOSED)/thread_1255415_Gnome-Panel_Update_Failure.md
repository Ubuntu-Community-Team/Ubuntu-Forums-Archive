---
title: "Gnome-Panel Update Failure"
date: 2009-09-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by drs305 on 2009-09-01
Ran today's update to the -9 kernel and other updates and upon reboot the Desktop continually flashed as it does when I run "killall gnome-panell".

Rebooted to the -8 kernel, same thing happened, as it then did for -6. I checked what was updated today and suspect it was gnome-panel. I tried booting in recovery mode and noticed that Gnome Panel Display (I think) failed.

I'm currently trying to restore my system from a backup image. Just wanted to record this for others who might be doing updates today. I will submit a bug report once I can further narrow down the problem.

[COLOR="DarkRed"]The solution is posted in #7.[/COLOR]

---

### Post by Nickedynick on 2009-09-01
Just checked, I've got the same issue. It seemed to stop for some reason when I clicked on the desktop though...

---

### Post by Darkshade on 2009-09-01
It's already fixed. If your server is not updated yet switch to the main server and update your system.

---

### Post by drs305 on 2009-09-01
Thank you to both for the inputs. I'll try updating again once I've restored my old image. Times like this make me appreciate apps like fsarchiver, partimage and clonezilla and my habit of making frequent backups.  ;-)

Later that very same day: Spoke too soon. On my 64-bit machine it is still misbehaving. It's definitely a gnome-panel problem. I was able to stop the constant reloading by either clicking on the Desktop as mentioned previously or by typing "killall gnome-panel" in a terminal (which I fortunately have autostart).

Once it stopped, I wasn't able to retrieve my panels with "gnome-panel", but I was able to see some of the error messages, including:
> 
Unable to open desktop file /usr/share/applications/bum.desktop for panel launcher: No such file or directory
Unable to open desktop file gconftool-2-2.desktop for panel launcher
(gnome-panel:7833): libglade-WARNING **: could not find glade file '/usr/share/gnome-panel/glade/clock.glade'

** ERROR **: /usr/share/gnome-panel/glade/clock.glade not found; this installation is incorrect.
aborting...
Trace/breakpoint trap (core dumped)


---

### Post by BackwardsDown on 2009-09-01
Great that its been fixed :D

Going to try updating now.

---

### Post by Darkshade on 2009-09-01
> **drs305 said:**
> Later that very same day: Spoke too soon. On my 64-bit machine it is still misbehaving. It's definitely a gnome-panel problem. I was able to stop the constant reloading by either clicking on the Desktop as mentioned previously or by typing "killall gnome-panel" in a terminal (which I fortunately have autostart).
...

It got fixed on my 64bit install before I made my previous post. Are you sure you have the latest updates installed?

---

### Post by drs305 on 2009-09-01
> **Darkshade said:**
> It got fixed on my 64bit install before I made my previous post. Are you sure you have the latest updates installed?

As far as I know - I've tried the main and US servers and no updates are showing. I wasn't able to save the error messages, but I was able to isolate the problem on my machine before I was forced to reboot.

The error causing the continuous recycling of the gnome-panel was the system not finding the proper files to run the panel clock. I know it had something to do with 'glade' and I've seen bug reports on Launchpad referencing glade as well.

In any case, I removed the clock applet from the panel and now the system boots normally.

[COLOR="DarkRed"]**SOLUTION:**[/COLOR]
Should anyone else experience this problem:
If you can get to a terminal: *killall gnome-panel* repeatedly until it stops cycling. Of course, now you won't have any panels.
Since you can't get to the panel to remove the clock, try to open a terminal, then *gconf-editor  /apps/panel/applets*.
Scroll through the list of applets and watch the right panel. Find the applet for the clock (OAFIID:GNOME_ClockApplet). 
Go to the right panel, find the *bonobo_iid* entry, right click and select "Unset key". That will stop the panel cycling.

Once I rebooted, I tried adding the clock back and immediately the panel started continuously cycling once again. Selecting "Unset key" for that newly created applet entry immediately fixed the problem.

---

### Post by Seventh Reign on 2009-09-01
I just gnome-do'd open my terminal while the panel was having its Seizure .. did a killall gnome-panel ... and then ran an apt-get upgrade ... rebooted into the new -9 kernel and everything was perfect.

---

### Post by drs305 on 2009-09-01
> **Seventh Reign said:**
> I just gnome-do'd open my terminal while the panel was having its Seizure .. did a killall gnome-panel ... and then ran an apt-get upgrade ... rebooted into the new -9 kernel and everything was perfect.

Are you using 32 or 64 bit? And do you have the clock on your panel?

My 32-bit is working fine, but 64-bit is still crashing with all the updates. I originally thought it was the -9 kernel but now am convinced it's one of the gnome-applets, gnome-utils or gnome-panel that's the problem - whichever contains the clock applet.

---

