---
title: "restore normal scrollbars in Xubunto 12.10"
date: 2013-09-07
forum: Installation &amp; Upgrades
---

### Post by scubscub on 2013-09-07
I recently upgraded to 12.10, and my scrollbars disappear, being replaced by some funny floating thing that looks like a bandaid. Granted, I think I recall having this same problem and fixing it last time I "upgraded," but that was a year ago or so.

Following the instructions on some website, I disabled "overlay-scrollbar" or something like that in synaptic. That fixed the problem for most, but not all programs.

To wit: the scrollbar in evince (and a few other programs) is still very strange. Though not as bad as the "floating bandaid" version, the slider (or what you drag in the middle of the scrollbar) is very, very thin, so trying to click on it is essentially pixel hunting. Also, there are no arrows at the top and bottom of the scrollbar, and clicking on part of the scrollbar moves to that part of the document (instead of advancing a page which is the accustomed behavior).

I would really like to fix this because it has made evince unusable. I've been using acroread as a backup but that is in so many ways an inferior program. Any help? Firefox, and most other programs, work fine since the overlay was removed. But I would just like to be able to have normal, functional scrollbars on all of my windows/programs.

---

### Post by vasa1 on 2013-09-07
What is the name of the theme you are using? The appearance of scrollbars could be affected by the choice of theme.

---

### Post by scubscub on 2013-09-07
I switched the theme around a few times, had no effect. Like I said, not all programs are affected -- evince is an example. Firefox, the regular windows are normal now.

---

### Post by scubscub on 2013-09-11
Bump

---

### Post by Toz on 2013-09-11
If you change to the default Greybird theme, do the scrollbars return to normal? 
Other than evince, what other apps are affected? 
Any chance you could post a screenshot?

---

### Post by scubscub on 2013-09-11
Hi, and thanks for the quick reply.  Here is a screenshot of the appearance settings manager in Greybird with a similar issue -- no up/down arrows, although the scroller itself is not as small as in evince. I'm not sure of what all programs have this issue, since the ones I use primarily -- firefox, thunderbird, chromium -- do not. Acroread does not, though evince does. It is a puzzlement.

---

### Post by Toz on 2013-09-12
Did you make any manual edits to any of the theme files?

Do any of the following files exist on your system? If so, can you post back their contents:
- $HOME/.gtkrc-2.0
- /etc/gtk-2.0/gtkrc

and the results of:
```
ls $HOME/gtk-3.0
ls /etc/gtk-3.0
env | grep -i gtk
```

---

### Post by scubscub on 2013-09-12
Hmm, well there is no - $HOME/.gtkrc-2.0 or - /etc/gtk-2.0/gtkrc ...

Of the terminal commands, only ls /etc/gtk-3.0 had a result, which was:

im-multipress.conf  settings.ini

---

### Post by Toz on 2013-09-12
Can you post back the contents of /etc/gtk-3.0/settings.ini?

Did you make any manual edits to any of the theme files?

---

### Post by scubscub on 2013-09-12
> **Toz said:**
> Can you post back the contents of /etc/gtk-3.0/settings.ini?


Did you make any manual edits to any of the theme files?

Here are the contents of settings.ini:

[Settings]
gtk-theme-name = Ambiance
gtk-icon-theme-name = ubuntu-mono-dark
gtk-fallback-icon-theme = gnome
gtk-sound-theme-name = ubuntu
gtk-icon-sizes = panel-menu-bar=24,24


I don't believe I made any manual edits to any theme files.

---

### Post by Toz on 2013-09-12
Looks like your gtk3 theme settings are being overridden to use the Ambiance theme. This would affect gtk3 apps like evince, chrome, etc. Try this:

1. Edit that file as root (from a terminal window):
```
gksudo leafpad /etc/gtk-3.0/settings.ini
```
...enter your password when prompted.

2. Change the file so that it looks like this (delete the other lines):
```
[Settings]
gtk-fallback-icon-theme = gnome
```

3. Save the file. Change the appearance theme away from and back to Greybird. Any better?

---

### Post by scubscub on 2013-09-12
Success!  I did actually have to switch back and forth between themes a few times for the difference to kick in though. In any event this has fixed the problem for evince.

Thank you so much!

---

### Post by scubscub on 2013-09-12
Well... I was a bit hasty there.

Now switching back and forth between themes causes evince to start showing the scroll buttons. However, if I close evince and then reopen it, I still get the bizarre behavior.

 I can then open the appearance manager, switch between themes a few times, and then the buttons will reappear. But this has to be done every time evince starts, it seems.

So still no dice. I also tried rebooting on the off chance, with no luck.

---

### Post by Toz on 2013-09-12
I think there maybe some sort of bug with evince. Looking at it here on my computer, I'm noticing that as I'm changing the appearance themes, evince doesn't seem to apply some properly (most notably with respect to the rendering of the scrollbars). However, if I select one theme, close and restart evince, it renders properly again.

I believe evince requires a gtk3-compatible theme to render properly. Which theme are you trying to use? Greybird? If so, you might want to try downloading the latest version of greybird to see if that helps. You can either use the [shimmerproject PPA]("https://launchpad.net/~shimmerproject/+archive/ppa") or download directly from [their website]("http://shimmerproject.org/project/greybird/") (grab the [tarball]("https://github.com/shimmerproject/Greybird/tarball/master") and extract it into ~/.themes creating the folder if required.) Using the tarball method, the new theme will show up as "shimmerproject-Greybird-26eea3d" in the Appearance list.

---

### Post by scubscub on 2013-09-12
Alright, so I installed the updated version of Greybird. When I have this selected, I can close evince and reopen it, and it is a little better, as there is now an actual scroller, but still no up/down arrows on the scrollbar. I should mention that Greybird still looks like it did in my initial screenshot, where there is a bar of sorts but no arrows.

---

### Post by Toz on 2013-09-13
I don't think the greybird theme (or at least the new version) has the arrows. Try another theme (bluebird, blackbird, albatross). Newer versions of those themes are also available at the [shimmerpproject ]("http://shimmerproject.org/")home page.

---

### Post by scubscub on 2013-09-13
Okay, this seems to work.  It also fixes the issue in Pulse Audio, which I just discovered is another program affected by the scrollbar issue.

So I need to find a GTK+3 theme I like and stick with it, to get these programs to work normally.

Still, there is the weird fact that if I open Evince (or Pulse Audio) in an older theme (like HumanME for example), it has the messed up scrollbars -- then if I switch into a gtk3 theme, and then back into HumanME, evince now shows the correct scrollbars for HumanME. Why would that be happening?

---

### Post by Toz on 2013-09-13
> **scubscub said:**
> Still, there is the weird fact that if I open Evince (or Pulse Audio) in an older theme (like HumanME for example), it has the messed up scrollbars -- then if I switch into a gtk3 theme, and then back into HumanME, evince now shows the correct scrollbars for HumanME. Why would that be happening?
I'm guessing that the gtk3 theme is setting up the scrollbars properly and HumanME is not undoing (or overwritting) those settings. Just a guess.

---

