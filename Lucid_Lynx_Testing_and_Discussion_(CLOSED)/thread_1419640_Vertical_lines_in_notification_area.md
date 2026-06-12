---
title: "Vertical lines in notification area"
date: 2010-03-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kindofabuzz on 2010-03-02
I can't seem to figure out what is causing these vertical lines in my notification area. After a reboot there are no lines, then over time it keeps getting more.
[IMG]http://img30.imageshack.us/img30/3163/screenshot006w.png[/IMG]

---

### Post by Keyper7 on 2010-03-02
> **kindofabuzz said:**
> I can't seem to figure out what is causing these vertical lines in my notification area. After a reboot there are no lines, then over time it keeps getting more.
[IMG]http://img30.imageshack.us/img30/3163/screenshot006w.png[/IMG]

Are you using a fully updated Lucid? There was a bug in Empathy causing black lines, but it was (apparently) fixed. Next time it happens, try closing Empathy completely (not just the window, go to the file menu and quit) and see if the lines disappear.

---

### Post by Polniy on 2010-03-02
It looks highly unlikely he's using Empathy (Pidgin in the N.area).

---

### Post by Keyper7 on 2010-03-02
> **Polniy said:**
> It looks highly unlikely he's using Empathy (Pidgin in the N.area).

I haven't installed Pidgin, so I don't know the behavior when it's installed, but perhaps the MeMenu is automatically opening Empathy (minimized) when a non-offline status is set?

---

### Post by aethralis on 2010-03-02
I have sometimes also such vertical lines, albeit not so many. Also not using empathy but installed pidgin.

---

### Post by tgpraveen on 2010-03-02
i got that line once and on lciking the line i found out it was gnome-power-manager. even right clicking it brought up power-manager options
it was like the panel was not allowing the icon to load.

---

### Post by kindofabuzz on 2010-03-02
I figured out the lines for me are caused by not having the Indicator Applet on the panel. Re-added the applet and no more lines.

---

### Post by mirmos192 on 2010-03-15
I have the same vertical lines with Lucid (I know, it's Alpha!), as in the picture posted by kindofabuzz. They grow in number over time, but disappear after a reboot (and come back again after a while, natch). Very irritating.

I'm using Indicator Applet Session 0.3.3 and not Indicator Applet - because if I use Indicator Applet I get two Volume Control icons - the other being already in my Notification Area (2.29.92.1), and, anyway I don't need Indicator Applet (we should have the choice, no?).

Anyone know of a fix that doesn't involve using Indicator Applet? Alternatively, I'd be fairly relaxed about using it, if I must, if I could work out how to remove Volume Control either from my Notification Area or from the Indicator Applet....

(Also not using Empathy (not installed))

---

### Post by tekstr1der on 2010-03-15
> **mirmos192 said:**
> I'm using Indicator Applet Session 0.3.3 and not Indicator Applet...

I've got the vertical lines showing up with exactly the opposite indicator configuration. I am using indicator-applet and not indicator-applet-session.

Every time I launch rhythmbox, a thick gray vertical bar appears in my notification area.

Is a bug filed on this yet? My bug queue is jacked up ATM waiting for apport fix.

---

