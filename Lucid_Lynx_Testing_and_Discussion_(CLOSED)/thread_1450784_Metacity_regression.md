---
title: "Metacity regression"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lucazade on 2010-04-09
Look at this bug report:
[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/558327](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/558327)
bug reported by Mark Shuttleworth on 2010-04-08

"The close button, now that it is in the corner, is too clickable because it is possible to click anywhere to the left of it and still activate it. That makes the close button quite a bit larger than the other two buttons, when it should be the same size. The space to the left of the button, between the button and the edge of the window, should not be clickable."

I usually remove the top panel (mainly because I don't need all those applets) and keep only the bottom one.
This way I *was* able to close any maximized window just left-clicking in the top-right corner. I can't anymore... 

Any advice on how to restore the old, sane, cross-os behavior?

---

### Post by Queue29 on 2010-04-09
What, you're saying we should copy Windows and OSX in terms of usability? 

Don't be preposterous.

---

### Post by lucazade on 2010-04-09
> **Queue29 said:**
> What, you're saying we should copy Windows and OSX in terms of usability? 

Don't be preposterous.

No, I haven't said that.
Just don't change things have worked for ages in GNOME (and also in the other os).

I'm talking about the new patch (not upstream) of metacity.

---

### Post by clhsharky on 2010-04-09
HI 

I see no regression, I can not reproduce your complaint on Gnome 2.30 using Metacity in Lucid.


Sharky

---

### Post by lucazade on 2010-04-09
> **clhsharky said:**
> HI 

I see no regression, I can not reproduce your complaint on Gnome 2.30 using Metacity in Lucid.


Sharky

Hi

I mean I cannot close anymore a window clicking in the top-right corner of the screen (outside the close buttont there was a little pixel tollerance area).

Look at the screenshot attached.. I was able to close w/o looking at the close button, just moving the mouse to the corner and clicking.

In the meanwhile i've rebuilt metacity from source w/o that "patch" and it works as expected and as in the old releases.
(debian/patches/13_better_support_for_button_layout.patch)

hope to be clear

---

### Post by lucazade on 2010-04-09
I've attached a fixed release of metacity 2.30 w/o that patch

[http://dl.dropbox.com/u/1338581/metacity/libmetacity-private0_2.30.1-0ubuntu9_i386.deb](http://dl.dropbox.com/u/1338581/metacity/libmetacity-private0_2.30.1-0ubuntu9_i386.deb)
[http://dl.dropbox.com/u/1338581/metacity/metacity_2.30.1-0ubuntu9_i386.deb](http://dl.dropbox.com/u/1338581/metacity/metacity_2.30.1-0ubuntu9_i386.deb)
[http://dl.dropbox.com/u/1338581/metacity/metacity-common_2.30.1-0ubuntu9_all.deb](http://dl.dropbox.com/u/1338581/metacity/metacity-common_2.30.1-0ubuntu9_all.deb)

---

### Post by MacUntu on 2010-04-09
This has been fixed, I'm not seeing it anymore.

---

### Post by clhsharky on 2010-04-09
HI lucazade

Thank you, I will look further in to it.

Sharky

---

### Post by vredley on 2010-04-09
I can confirm this issue, and it's driving me nuts.

---

### Post by lucazade on 2010-04-09
New Metacity update (2.30.1-0ubuntu1) doesn't solve the issue.. :(

---

### Post by lucazade on 2010-04-10
Anyone else having this problem?

---

### Post by vredley on 2010-04-10
Bug reported: [https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/560118](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/560118) . But let's be honest - this isn't going to be fixed, is it?

---

### Post by MacUntu on 2010-04-10
Sorry, I misunderstood you guys - yes, the "problem" is still there if you wanna see it as such (I don't).

---

### Post by Uncle Spellbinder on 2010-04-10
> **MacUntu said:**
> Sorry, I misunderstood you guys - yes, the "problem" is still there if you wanna see it as such (I don't).
Same here. I fail to why this is a "bug" at all. Maybe I just don't get it, I guess.

---

### Post by lucazade on 2010-04-10
> **Uncle Spellbinder said:**
> Same here. I fail to why this is a "bug" at all. Maybe I just don't get it, I guess.

Do You use a top gnome-panel? Have you tried using a touchpad?
Without it this bug is clearly visible.

---

### Post by mc4man on 2010-04-10
I'm using the ambiance theme and with either all the buttons to the right or what I use - max, min on left, exit on right you still get button -> out as clickable in a maxed window, button -> out several pixels in an unmaxed window

---

### Post by vredley on 2010-04-10
That was quick:

> There was incentive for this change and a decision was reached. If you wish to discuss it, see bug #558327.
Nobody wants a chain of "yes, no, yes, no" bug reports.

Changed in metacity (Ubuntu): 
status: 	New &#8594; Invalid

---

### Post by Mr. Picklesworth on 2010-04-10
The point is pretty simple: that's a bug report about a bug report. It just isn't very productive when discussion about the patch in question is open to happen at [bug #558327]("https://bugs.edge.launchpad.net/ubuntu/+source/light-themes/+bug/558327").

I think it would be unfair to bypass the discussion which has taken place by filing a different bug report, especially since those involved in the original discussion are not all subscribed to it.

---

### Post by Uncle Spellbinder on 2010-04-10
> **lucazade said:**
> Do You use a top gnome-panel? Have you tried using a touchpad?
Without it this bug is clearly visible.

Touchpad? NO

Top Panel? NO

I hate having a panel at the top. Only one panel, at the bottom.

---

### Post by vredley on 2010-04-10
> **Mr. Picklesworth said:**
> The point is pretty simple: that's a bug report about a bug report. It just isn't very productive when discussion about the patch in question is open to happen at [bug #558327]("https://bugs.edge.launchpad.net/ubuntu/+source/light-themes/+bug/558327").

I think it would be unfair to bypass the discussion which has taken place by filing a different bug report, especially since those involved in the original discussion are not all subscribed to it.

Ah, I see. I thought that since the original bug was marked 'Fix Released', I would have to file a new bug on what has now become the default behaviour.

---

### Post by Mr. Picklesworth on 2010-04-10
> **vredley said:**
> Ah, I see. I thought that since the original bug was marked 'Fix Released', I would have to file a new bug on what has now become the default behaviour.

Well, it's by no means a strict regulation that I'm following. I'm rather bothered at how design discussions can get bypassed in bug reports. I don't think the bug tracker is a good medium for such things since a single design change can affect many different, unexpected projects.

As long as we treat those design things like minor technical issues and fix them individually with little patches and no thorough decision on direction, nothing good will happen; we'll just wobble uncontrollably and have these weird little things that vary each release, depending on who filed the last bug report. Thus, I wanted to keep things tighter, hopefully to encourage a richer discussion.

And come to think of it, I sounded a little cranky when I triaged your bug report. Meant nothing by it! The more people concerned about usability, the better :)

As for bug status, though, indeed: it can be changed back at any time. If the released fix is not an effective fix, for example.

---

### Post by Merk42 on 2010-04-10
> **Mr. Picklesworth said:**
> The point is pretty simple: that's a bug report about a bug report. It just isn't very productive when discussion about the patch in question is open to happen at [bug #558327]("https://bugs.edge.launchpad.net/ubuntu/+source/light-themes/+bug/558327")

What's to discuss?
sabdfl wants it, so it will happen. Fitts' law be damned.

---

### Post by MacUntu on 2010-04-11
> **Merk42 said:**
> sabdfl wants it, so it will happen.

I want it too. It's totally stupid to have buttons when clicks are registered outside of them. Just learn how to use your input devices. :KS

> **Merk42 said:**
> Fitts' law be damned.

Yeah, good old Fitts. I guess you could also make the whole title bar act as close button - wouldn't Fitts love it?

---

### Post by lucazade on 2010-04-11
> **MacUntu said:**
> Just learn how to use your input devices. 
It is not about learning how to use mouse.. 
changing this kind of interactions in a LTS just because of a theme is not good in my opinion.
A new theme cannot break all the others.

e.g. In Osx Exposé can be activated by moving the mouse to a corner of the desktop using a feature called Active Screen Corners.

---

### Post by MacUntu on 2010-04-11
> **lucazade said:**
> A new theme cannot break all the others.

I'd rather call the prior state broken. Why should one button have a larger clickable area than the others? I understand that you've gotten used to it and now miss it, but that doesn't automatically make it a bug (else I'd file tons of bugs against GNOME :D).

> **lucazade said:**
> e.g. In Osx Exposé can be activated by moving the mouse to a corner of the desktop using a feature called Active Screen Corners.

How's that related to this topic? Anyways, doesn't Compiz offer corner/edge triggered actions?

---

### Post by lucazade on 2010-04-11
> **MacUntu said:**
> I understand that you've gotten used to it and now miss it, but that doesn't automatically make it a bug (else I'd file tons of bugs against GNOME :D)

(Sorry for the following comment but I can't resist!)
It is like if I have to look for my ***** when I go peeing. :D

---

### Post by MacUntu on 2010-04-11
I totally understand what you mean. It's the same with the top panel's menu bar: I just (blindly) move my mouse to the top left and click to open the 'Applications' menu. Indent the menu by 20px and it would drive me crazy - at least for a while... man is a creature of habit.

---

### Post by vredley on 2010-04-11
> **MacUntu said:**
> I'd rather call the prior state broken. Why should one button have a larger clickable area than the others? I understand that you've gotten used to it and now miss it, but that doesn't automatically make it a bug (else I'd file tons of bugs against GNOME :D).

I got used to it in Windows. So it's all Bill's fault.

@ Mr. Picklesworth - thank you for the explanation. You are forgiven. :P

@ all the doubters - try using a netbook with a touchpad the size of a postage stamp. :)

@ Lucazade - thanks for those debs, but they don't work with Compiz on my system; no decorations, and gtk-window-decorator shows 100% CPU usage. :(
Any ideas?

---

