---
title: "Help! I managed to break 11.04 upgrade &amp; Compiz totally"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by azupan on 2011-04-30
OK, here's the story.

I Happily used 10.x with Cairo Dock and Compiz with all its bells & whistles. Then this message "11.04 upgrade is finally out, blah blah" popped up, and I said, OK, why not, and upgraded.

After successful upgrade, I tried to re-enable Compiz Cube, and at some point, window decorations vanished. I somehow managed to reenable them back, but I still couldn't drag/resize windows with the mouse. I presumed, that Emerald decorator is to blame, and uninstalled it. Emerald caused similar problems before. That didn't solved the problem, so I decided to uninstall Compiz completely together with its settings, and install it again. My assumption was, that some old setting causes the problem, and that things should be working OK if I start with fresh settings. In marked Compiz for complete removal Synaptic Package Manager,  and removed it.

Then, I tried to install Unity again in Ubuntu Software Center in safe/classic mode. Result: Nothing works. Instead of Unity, I get blank screen without even a button to log off or shut down. In classic mode, Compiz doesn't work anymore.

Any ideas about how to fix this mess, or revert back to 10.x?

**EDIT:** I managed to get Unity working again. Installing Unity doesn't automatically install Compiz. I had to do it manually in Synaptic Package Manager. At first, there were no windows decorations. They reappeared when I checked "Windows Decoration" option. It's still not possible to move/resize windows with mouse. It's impossible to grab window frame with mouse.

---

### Post by dino99 on 2011-04-30
to revert back, from synaptic:
- remove/purge unity & ubuntu-desktop
- set back your previous config

---

### Post by carvish on 2011-04-30
Hi there,
I am also having the same problem, How did you revert back to seeing your task bar, I don't see mine or how do you revert back to 10.x when you can't get to your synaptic???

---

### Post by mc4man on 2011-04-30
> At first, there were no windows decorations. They reappeared when I checked "Windows Decoration" option. It's still not possible to move/resize windows with mouse. It's impossible to grab window frame with mouse.
First of all - when you tried to set rotate/cube you unset all the plugins, nothing was removed, nor did anything have to be re-installed
You still need to enable some plugins in ccsm like move, resize, scale, expo, ect.

The way to set the profiles back to the defaults is to run these 2 commands
```
gconftool --recursive-unset /apps/compiz-1
gconftool --recursive-unset /apps/compizconfig-1

```
One way to set the cube/rotate without unsetting all the plugins is shown here, there are a couple of other ways
[http://ubuntuforums.org/showthread.php?p=10734118#post10734118](http://ubuntuforums.org/showthread.php?p=10734118#post10734118)

---

### Post by azupan on 2011-04-30
> **dino99 said:**
> to revert back, from synaptic:
- remove/purge unity & ubuntu-desktop
- set back your previous config
ubuntu-desktop wasn't installed in the 1st place. I installed it, but problem wasn't solved. 

Completely uninstalled unity & ubuntu-desktop again, installed again, the problem persists.

As a reminder: I can't drag/resize windows. Mouse cursor changes when I hover around the edges, but I'm unable to grab anything with mouse. As far as I can tell, keyboard shortcuts don't work either.  Alt+F9 (Minimize Window) works, but when I press Alt+F7 or Alt+F8 (Move/Resize Window), nothing happens. Everything else, like mose wheel, or clicking on windows seems to be working.

---

### Post by ufmace on 2011-04-30
I've got a similar problem. I was using Ubuntu Classic and everything was going more or less okay until I installed CompizConfig settings manager. I tried to enable the cube, and somehow ended up in a state where 1. all of the window title bars were gone, and it was impossible to move or resize windows, closing was only possible with the dock menu and 2. All new windows opened with the top edge a little above the top of the screen, and since they couldn't be moved, this was really annoying.

I haven't made any progress in getting it working right again, but I was able to log out and log into Unity, where everything worked fine. I was also able to log out and log into Classic (no effects) where everything also worked fine. At the moment, I actually like (no effects) better, since dragging and resizing windows is now smooth, where it was choppy before. That makes me think there's some kind of problem with my video card drivers, but I'm not sure if it affects the other problem with the window titlebars/effects and initial position. Since the other modes work fine for that problem, I think I must have messed up some kind of config file somewhere.

---

### Post by azupan on 2011-04-30
> **mc4man said:**
> The way to set the profiles back to the defaults is to run these 2 commands
```
gconftool --recursive-unset /apps/compiz-1
gconftool --recursive-unset /apps/compizconfig-1

```One way to set the cube/rotate without unsetting all the plugins is shown here, there are a couple of other ways
[http://ubuntuforums.org/showthread.php?p=10734118#post10734118](http://ubuntuforums.org/showthread.php?p=10734118#post10734118)Phewww! That helped, at least partially. Got to write these commands down somewhere :)

I said "at least partially" because immediately after the above commands were executed, the following happened: When I grabbed one window, some other window was dragged. Then, I logged off, logged on again, and ended up with empty screen. I enabled Ubuntu Unity Plugin in CompizConfig, and everything went back to normal- more or less. I say more or less, because there are still some strange things going on. Desktop Wall, for example is not enough for Workplace Switcher to work; Expo must also be enabled. I fiddled with settings a little bit, and... aww, crap, I'm back to unmovable/unresizeable window again. More in a minute, got to log off.

**EDIT:** OK, it looks like disabling and enabling Ubuntu Unity Plugin in CompizConfig Settings Managed makes things go haywire. To restore everything (more or less) back in order, 

gconftool --recursive-unset /apps/compiz-1

seems to be enough.

I suspect the 11.x upgrade started to act weird because I had autohide property set in upper panel in Ubuntu 10.x. I guess there's no way of hiding that thing in 11.x - or is it?

---

### Post by azupan on 2011-04-30
After a couple of hour of fiddling around with this I came to the conclusion, that Unity seriously sucks. Gnome + Cairo on the outside, Compiz plugin on the inside. No wander preferences & administration is so well hidden. Start CompizConfig Settings Manager, disable Ubuntu Unity plugin, one careless mouse click, and BAM! - you're left with nothing. No menu, no logoff button, nothing. The only thing someone not knowing the ctrl-F1 shortcut can do is to curse the Ubuntu and install another Linux distro. I'm seriously considering this as well. I sincerely hope I'm wrong, but for the time being, Unity looks like a BAD idea.

---

### Post by bigbeck89 on 2011-04-30
> **azupan said:**
> OK, here's the story.

After successful upgrade, I tried to re-enable Compiz Cube, and at some  point, window decorations vanished. I somehow managed to reenable them  back, but I still couldn't drag/resize windows with the mouse. 

I did this EXACT same thing. my windows would all open with the top half off the screen and I couldnt move/resize them.

> **mc4man said:**
> First of all - when you tried to set rotate/cube you unset all the plugins, nothing was removed, nor did anything have to be re-installed
You still need to enable some plugins in ccsm like move, resize, scale, expo, ect.

The way to set the profiles back to the defaults is to run these 2 commands
```
gconftool --recursive-unset /apps/compiz-1
gconftool --recursive-unset /apps/compizconfig-1

```One way to set the cube/rotate without unsetting all the plugins is shown here, there are a couple of other ways
[http://ubuntuforums.org/showthread.php?p=10734118#post10734118](http://ubuntuforums.org/showthread.php?p=10734118#post10734118)

THANK YOU! after entering these commands I restarted my computer and everything is working correctly. windows open properly on the screen and i can alt click on them to move them.

---

### Post by azupan on 2011-05-01
> **bigbeck89 said:**
> I did this EXACT same thing. my windows would all open with the top half off the screen and I couldnt move/resize them.I think I figured out the reason, see my previous post. Unity is just a Compiz plugin, and if it's disabled for whatever reason, everything goes haywire. Installing Unity2d might help, though. Haven't got time to look into it yet.

**EDIT: **Tried to install unity2d, it doesn't help. So, the only solution seems to be to logout (or hit the reset button if you don't know how to logout from completely blank screen), and reenable unity in safe mode.

---

### Post by afrodeity on 2011-05-01
thanks, this saved me. Now if only I can figure out the performance issues, feels like I downgraded from Maverick running 2.6.38.4-candela kernel.

---

