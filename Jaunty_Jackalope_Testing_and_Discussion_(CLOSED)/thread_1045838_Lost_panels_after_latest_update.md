---
title: "Lost panels after latest update"
date: 2009-01-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jerrynewt on 2009-01-20
Just performed latest update and after restarting, the boot process is normal. After login my desktop comes up just fine, but my panels (Applications -- Places -- System) comes up for about two seconds then disappears, comes up again same way and disappears again over and over. Restart or turning off the computer has same results. Any ideas ? By the way, at first - right after upgrade, the panels would appear then disappear and not come back. Did Cntl>Alt>F8 and logged in; then did another update and upgrade (wireless was working) and that is when the repetition began. Any ideas ??

---

### Post by sofasurfer on 2009-01-20
Try uninstalling and reinstalling gnome-panel.

---

### Post by autocrosser on 2009-01-20
A update has just been issued--if you have the ability to right-click to get a terminal--do a apt-get update/upgrade....If you haven't installed nautilus-open-terminal, go in with recovery-mode & apt-get the update.....someone forgot the important extra files for gnome-panel & it seg-faults.....

---

### Post by cdtech on 2009-01-20
Or try to restart gnome panel:
```
pkill gnome-panel
```

**UPDATE::.**
I just seen your post autocrosser.........

---

### Post by Slug71 on 2009-01-20
Sweet, i has got my panels back. :D
That sucked. #-o

Have added Terminal to Docky for any future instances.

---

### Post by autocrosser on 2009-01-20
I use nautilus-open-terminal---I like to just right-click & get a term anywhere.....

Ya--I had just got home & grabbed the updates for the day :(

I just right-clicked & did a apt-get 'date/'grade & all was smooth again......

---

### Post by gtdaqua on 2009-01-20
Sorry to hijack this thread, but window borders are still not coming up. I have to manually type compiz in the terminal to get the borders. 

Compiz is not running in the background when I log in to the desktop.

---

### Post by taavikko on 2009-01-21
> **gtdaqua said:**
> Sorry to hijack this thread, but window borders are still not coming up. I have to manually type compiz in the terminal to get the borders. 

Compiz is not running in the background when I log in to the desktop.

That has nothing to do with panels, try to search for an existing thread or start a new one, thanks.
That would benefit all, since querying a different problem in a wrong thread, makes it harder to people find it. :)

btw, check session properties that you have added compiz to session startup

---

### Post by UBfusion on 2009-01-21
I am running and updating Jaunty in a virtual machine since January 13 and I can confirm the problem.

- Uninstalling and reinstalling gnome-panel did not fix it

- apt-get update/upgrade did neither.

- attempting to manually run gnome-panel leads to a small message being displayed for a few milliseconds and the following error:

```
ERROR:applet.c:969:panel_applet_load_idle_handler: code should not be reached
Aborted (core dumped)
```

Being a noob, I don't know where precisely in /var/log a detailed crash log is found... I opened most of the logs and saw nothing.

By the way, my quick and dirty solution to open a terminal on a blank desktop is to right-click, Create Launcher, choose Type: Application in Terminal and type some gibberish in the command. A shortcut gets created and displayed on the desktop.

Going to Launchpad to see whether this is already submitted. I feel that since my findings are within a VM, without further confirmation from other people I cannot yet submit a bug (maybe the fix is not on the repos yet?)

Update: I see no similar bugs for Jaunty or gnome-panel. More testers needed.

---

### Post by autocrosser on 2009-01-21
Are you using a mirror repo or the main? I only use the main--updates hit there first & it's sometimes hours or days for it to filter out to the rest of them.....

---

### Post by marmuta on 2009-01-21
UBfusion, better report it. If others hit the same problem they can confirm it in the bug report.

When you get "... (core dumped)" then apport should be already active and you can find the crash dumps /var/crash. 
The easiest way to get them to launchpad is to use the apport popup "Sorry the app ... closedy unexpectedly". If it doesn't open automatically you can do it manually with
```
apport-cli -c /var/crash/<my crash file>.crash

```or with gui
```
/usr/share/apport/apport-gtk -c /var/crash/<my crash file>.crash

```

---

### Post by habtool on 2009-01-21
I had same problem but after apt-get update/upgrade the panel would still not show up,

I logged into a new standard user account and that showed the panel properly
(I did not work here either before the update)

I had to:
rm -rf ~/.gconf/apps/panel

After logging back in the std panels where back in my normal user account with modified panels.

The bug for me was glipper.
When I tried to add glipper back to the panel it forze the screen.

logged out back in, no panels
rm -rf ~/.gconf/apps/panel
log out back in and panel back :)

sudo apt-get remove glipper
sudo apt-get install parcellite

alt f2: parcellite
(it gets added to session start up, but can run alt f2 parcellite so you dont need to logout the 1st time)

Ok, hope this helps any one else having this error in jaunty around about 21 jan 2009

[https://bugs.launchpad.net/ubuntu/+source/glipper/+bug/320202](https://bugs.launchpad.net/ubuntu/+source/glipper/+bug/320202)

---

### Post by DougieFresh4U on 2009-01-21
Currently showing 69 updates. Is it safe to say I should hold off until the problem is fixed?

---

### Post by lalitgaur on 2009-01-21
can confirm the same 
even updates do not work

---

### Post by philinux on 2009-01-21
Just updated and then logged out. Logged back in but chose different session. Ie xclient instead of last session. All back to normal now.

---

### Post by ronacc on 2009-01-21
at bootup this morning my panels were gone ,I just updated and they are back after reboot . gnome AMD64 .

---

### Post by gjoellee on 2009-01-21
> **Slug71 said:**
> Sweet, i has got my panels back. :D
That sucked. #-o

Have added Terminal to Docky for any future instances.

GNOME DO is good to have in such moments as well

---

### Post by ronacc on 2009-01-21
one of the very first things I do with a fresh install is add icons for the terminal , file browser , synaptic and my web browser to both the top panel and the desktop .I also install AWN although I'm using gnome-do/dockey this go around .

---

### Post by UBfusion on 2009-01-21
Thanks everybody for the suggestions. It was a matter of lagging mirrors, I was missing 31 updates. Now the panel works.

Lesson to be learned: during development/testing of new Ubuntu versions  don't trust local mirrors...

---

### Post by lalitgaur on 2009-01-21
rm -rf ~/.gconf/apps/panel
restored the panels for me

---

### Post by jerrynewt on 2009-01-21
I did the update and all is normal now. Thanks to all who replied.

---

### Post by vhaarr on 2009-01-21
> **UBfusion said:**
> I am running and updating 
Being a noob, I don't know where precisely in /var/log a detailed crash log is found... I opened most of the logs and saw nothing.


For future reference, I believe these things are logged to $HOME/.xsession-errors

---

### Post by gtdaqua on 2009-01-28
> **taavikko said:**
> That has nothing to do with panels, try to search for an existing thread or start a new one, thanks.
That would benefit all, since querying a different problem in a wrong thread, makes it harder to people find it. :)

btw, check session properties that you have added compiz to session startup

Thanks, taavikko! I have manually added compiz to session startup and the window manager starts up automatically! Wonder why this broke after an upgrade!

---

