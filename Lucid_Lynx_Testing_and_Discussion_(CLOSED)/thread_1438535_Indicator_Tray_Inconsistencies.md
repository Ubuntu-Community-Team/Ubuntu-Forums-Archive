---
title: "Indicator Tray Inconsistencies"
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ghindo on 2010-03-25
I'm loving the Lucid Beta and the new themes, but have had some trouble with the indicator tray.  (Is that even the right name?)  The battery icon has a strange habit of disappearing and reappearing with no particular rhyme or reason.  Also, there seems to be some inconsistency with the Rhythmbox icon; the icon changes theme depending on whether or not I have music playing.

Has anyone else experienced these issues?  I looked a bit here on the forums and couldn't find anything.

Thanks! :D

---

### Post by rahilm on 2010-03-25
Is your system up to date???
yes. the rhythmbox icon changes when you play music...but on my sytem it is:
the fist attachment is not-playing while second is playing:

---

### Post by ghindo on 2010-03-25
> **rahilm said:**
> Is your system up to date???
yes. the rhythmbox icon changes when you play music...but on my sytem it is:
the fist attachment is not-playing while second is playing:Yes, I am completely up-to-date.  I figured the Rhythmbox icon should change like your pictures show, but it's strange that it's not doing so on my system.  Interesting.

---

### Post by cdEWoozy on 2010-03-25
> **ghindo said:**
> The battery icon has a strange habit of disappearing and reappearing with no particular rhyme or reason.

You can configure when the battery icon should be displayed (system -> preferences -> power management). It defaults to only show when the battery is being charged or discharged, which works for me.

---

### Post by ViperScull on 2010-03-25
> **rahilm said:**
> Is your system up to date???
yes. the rhythmbox icon changes when you play music...but on my sytem it is:
the fist attachment is not-playing while second is playing:

Any way to remove the envelope icon from the tray?

---

### Post by 23meg on 2010-03-25
> **ViperScull said:**
> Any way to remove the envelope icon from the tray?

Remove the indicator-messages package.

---

### Post by _h_ on 2010-03-25
> **23meg said:**
> Remove the indicator-messages package.

Or just unlock it and remove it from the panel.

---

### Post by Queue29 on 2010-03-25
> **23meg said:**
> Remove the indicator-messages package.

> **_h_ said:**
> Or just unlock it and remove it from the panel.


But that also removes the volume control. How do you get that back?

---

### Post by 23meg on 2010-03-25
> **_h_ said:**
> Or just unlock it and remove it from the panel.

That will remove the whole indicator panel. Removing indicator-messages will remove only the messaging menu component.

> **Queue29 said:**
> But that also removes the volume control. How do you get that back?

It doesn't.

---

### Post by _h_ on 2010-03-25
> **23meg said:**
> That will remove the whole indicator panel. Removing indicator-messages will remove only the messaging menu component.

Right click the envelope, unlock it, right click again and remove it from panel, and I still retain my indicators.

---

### Post by 23meg on 2010-03-25
> **_h_ said:**
> Right click the envelope, unlock it, right click again and remove it from panel, and I still retain my indicators.

That's not possible, if what you mean by "the envelope" is the messaging menu (not some other mail notification applet). What you retain are the probably the notification area icons.

---

### Post by kklimonda on 2010-03-25
The wrong rhythmbox icon shows only if you don't use a indicator-application and fall back to the notification area. I'm not sure if it has been reported but I've seen it when I worked on another bug. I should probably take a look at this one as well if it's not already being worked on.

---

### Post by 0004tom on 2010-03-25
LOLs I've just removed it, and all the other icons, now when i drag the applet back onto the panel, it doesn't show :(

Oh and you can't move, or do anything with the network icon

---

### Post by ghindo on 2010-03-25
> **cdEWoozy said:**
> You can configure when the battery icon should be displayed (system -> preferences -> power management). It defaults to only show when the battery is being charged or discharged, which works for me.I have my preferences set to "Always display an icon," but the icon still sporadically appears.  Very strange.> **kklimonda said:**
> The wrong rhythmbox icon shows only if you don't use a indicator-application and fall back to the notification area. I'm not sure if it has been reported but I've seen it when I worked on another bug. I should probably take a look at this one as well if it's not already being worked on.I have the indicator-application package installed.

Interestingly enough, I don't have the envelope icon in my indicator tray, nor ever have.  Am I missing some required package?

---

### Post by kklimonda on 2010-03-25
> **ghindo said:**
> I have my preferences set to "Always display an icon," but the icon still sporadically appears.  Very strange.I have the indicator-application package installed.

It is installed, but are you actually using it? You probably don't have the Indicator Applet added to your GNOME panel. From the screenshot you have pasted it seems that Rhythmbox is using Notification Area and the bug you are seeing (wrong rhythmbox icon when playing) is triaged and going to be fixed.

---

### Post by ghindo on 2010-03-25
> **kklimonda said:**
> It is installed, but are you actually using it? You probably don't have the Indicator Applet added to your GNOME panel. From the screenshot you have pasted it seems that Rhythmbox is using Notification Area and the bug you are seeing (wrong rhythmbox icon when playing) is triaged and going to be fixed.Ah, interesting.  It seems you're right, and I don't have the Indicator Applet added to the panel.  I must have removed it in Karmic.  I added it and it seems to have solved both problems.  Thanks! :D

---

### Post by Bluesan on 2010-03-25
> **23meg said:**
> Remove the indicator-messages package.

Nice tip, thanks.

---

### Post by enceladus47 on 2010-03-25
I had the same problem of the power icon appearing and disappearing and ya I guess I might have removed it in karmic, re-added it now and it got sorted, thanks :)

---

### Post by Luke has no name on 2010-03-26
Why is the indicator applet required (Battery consistently, volume)? Why can't I just have "Notification Area"?

If it is some Ubuntuification of the taskbar, then why do I need a notification area (wireless status, for example)?

I don't see why both should be needed.

THAT SAID, thank you for the tip, this is what I needed.

---

