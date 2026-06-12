---
title: "Dual head glitch ATI"
date: 2010-01-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Anduu on 2010-01-27
Upgraded to Lucid without a hitch a couple of days ago and  my dual head setup spanning both monitors is working fine except for one small problem.

Wallpapers no longer stretch across both displays.They show up as if the screens were cloned.

I thought perhaps it was because of my modified xorg.conf but on reconfiguring xserver-xorg to default the problem persists.

Is this perhaps a bug or a feature not implemented yet or am I missing something?

---

### Post by Anduu on 2010-01-28
Can anyone confirm/deny whether wallpapers stretch properly across both displays on their systems?

---

### Post by Woody1987 on 2010-01-29
Same for me. Not sure if its a bug or not.

---

### Post by Anduu on 2010-01-29
> **Woody1987 said:**
> Same for me. Not sure if its a bug or not.

Are you running a fresh install or an upgrade?

---

### Post by _Doc_ on 2010-01-29
I have the same problem and I am running a new install... using the open source ATI drivers.

---

### Post by Woody1987 on 2010-01-30
> **Anduu said:**
> Are you running a fresh install or an upgrade?

upgrade

---

### Post by Toe on 2010-01-30
I can confirm this bug for Nvidia Twinview setups - running an upgrade from Karmic.

Is there already a launchpad report on this?

---

### Post by Anduu on 2010-01-30
> **Toe said:**
> I can confirm this bug for Nvidia Twinview setups - running an upgrade from Karmic.

Is there already a launchpad report on this?

That's what I am trying to figure out.I have searched through launchpad but haven't found anything yet.

The big question is where are things going wrong?There are a few suspects to choose from.Is it a bug in Gnome,Nautilus or Xorg itself causing the problem.I think we can safely rule out drivers as it occurs with both NVidia and ATI.

---

### Post by cariboo on 2010-01-30
Does anything show up in /var/log/Xorg.0.log?

---

### Post by Anduu on 2010-01-30
> **cariboo907 said:**
> Does anything show up in /var/log/Xorg.0.log?

No obvious Xorg errors for me.

---

### Post by Toe on 2010-01-31
I did some testing:
By activating Xinerama in my xorg.conf, I can get my wallpaper to once again span both monitors.
However, previously (on Karmic) Twinview alone was sufficient.

Additionally, Xinerama messes up window maximizing, so it isn't really a viable option.

---

### Post by Anduu on 2010-02-01
Well I am at a loss....

I have scoured logfiles and reconfigured xorg six ways from Sunday and cannot find anything "wrong" or change how the desktop is rendered.

I do get an odd error in my xorg log...it states VGA-1 has an invalid EDID however VGA-1 does not exist on my system.Xrandr reports my displays as DVI-0 and VGA-0.

Another thing I have noticed going between Windows and Ubuntu is I have to manually adjust my primary monitor's screen alignment every time even though I use the same resolution/refresh rate on both.This has never been the case in previous versions of Ubuntu.

So I guess this should be reported but how does one report a bug without knowing what package is the culprit not being able to present error logs etc?

---

### Post by Aenima99x on 2010-02-01
Can you guys tell me how you even got the dual monitors working? Maybe my scenario is different....I've got a HP laptop on a docking station with 2 external monitors connected to the docking station. one connected by VGA, the other with DVI. My setup was working perfectly in Karmic using the FGLRX drivers. Now I can't even get proper displays under Lucid using the open-source ATI drivers. The best I've been able to achieve is getting the laptop display and one monitor working. I've been through a ton of xorg.conf configs and now I can't get any display outside of the laptop. Any advice?

---

### Post by junior aspirin on 2010-02-01
Thanks to this thread I checked to see if I can get my dual display working since I have had no luck before. It works nearly perfectly by enabling through System>Preferences>Displays. I say nearly perfect because compiz still has issues on my pc leaving artefacts on the screen, although that could be an issue with KMS. Turn off compiz and all works fine. The radeon drivers are coming along nicely.

I can't get the wallpaper to stretch across, but my set-up is different to yours.

ATI radeon 9800 to monitor and TV screen via s-video/RCA

---

### Post by Toe on 2010-02-02
@Anduu:

I have found a similar EDID error message in my Xorg.log

```
(WW) Feb 02 09:17:05 NVIDIA(0): The EDID for HSD HannStar C174 (DFP-0) contradicts itself:
(WW) Feb 02 09:17:05 NVIDIA(0):     mode "640x360" is specified in the EDID; however, the
(WW) Feb 02 09:17:05 NVIDIA(0):     EDID's valid HorizSync range (31.000-80.000 kHz) would
(WW) Feb 02 09:17:05 NVIDIA(0):     exclude this mode's HorizSync (26.2 kHz); ignoring
(WW) Feb 02 09:17:05 NVIDIA(0):     HorizSync check for mode "640x360".
```

I can't remember it showing up when I was still running Karmic. There have been no hardware changes since.

---

### Post by Anduu on 2010-02-03
A little update.....

In Karmic,with dual monitors and wallpaper spanning working,notification bubbles appeared on the top left of my secondary monitor.So far with Lucid they have been on the top left of the primary monitor.

Since recent updates...today's/yesterday's the notification bubbles are now appearing on my secondary monitor again as in karmic.Still no wallpaper spanning though.

Seems baby steps are being taken in the right direction :)

---

### Post by Toe on 2010-02-14
I've searched launchpad and found two bug reports about this issue, which also seems to be known upstream.

Here are the links:
[https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/521492](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/521492)
[https://bugzilla.gnome.org/show_bug.cgi?id=603551](https://bugzilla.gnome.org/show_bug.cgi?id=603551)

I've marked the second launchpad report as a duplicate.

---

### Post by Anduu on 2010-02-14
> **Toe said:**
> I've searched launchpad and found two bug reports about this issue, which also seems to be known upstream.

Here are the links:
[https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/521492](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/521492)
[https://bugzilla.gnome.org/show_bug.cgi?id=603551](https://bugzilla.gnome.org/show_bug.cgi?id=603551)

I've marked the second launchpad report as a duplicate.

Good news!

Thanks for the heads up =]

I wonder how long a patch like this will take to get to us?

---

### Post by Anduu on 2010-02-23
Apparently not long :o

Well...steps are being made to get things working.

I have recieved a few updated packages ie gnome-desktop-data,libgnome-desktop and nautilus-data to name a few who's changelog's say support for spanning wallpapers has been added.

Still no functionality yet that i can find.I have tried searching through gconf to see if there is a setting there yet but nothing.

I suspect there may be a few more packages to come to complete things.

---

### Post by Anduu on 2010-02-26
In case anyone is interested wallpaper spanning is now functional.It has not been implemented into gnome-appearance-preferences yet so it must be set using gconf.

Open gconf-editor and go to desktop/gnome/background and set "picture_options" to "spanned".

Two small caveats however:

[LIST=1]
[*]Any time you change backgrounds or open the background tab in gnome-appearance-preferences you will have to go back into gconf-editor and reset the spanned option.

[*]Presently the wallpaper is only *scaled* across both desktops...not stretched.Therefore if your wallpaper doesn't match the aspect ratio of your virtual desktop resolution it will not completely fill the desktop area.
[/LIST]

Anyway this feature made my week.Hope it brightens your day ;)

---

### Post by zykotick9 on 2010-02-26
Anduu thank you so much.

I was the one who reported bug 521492.

Until reading your work-around, the only way I had discovered to get dual-monitor backgrounds to display correctly was using Compiz's wallpaper feature; which disabled Gnome's ability to use the desktop for icons.

Thanks for finding a solution not requiring the application of the upstream's patch!

---

### Post by Anduu on 2010-02-26
Don't thank me...thank the devs for getting it in so fast ;)

---

### Post by EMCGFX on 2010-04-27
I have this issue too with Nvidia GeForce 9400 GT and two LCD monitors. I can confirm that 10.04 RC still have this bug. Stretch function for wallpaper is not working properly.

---

