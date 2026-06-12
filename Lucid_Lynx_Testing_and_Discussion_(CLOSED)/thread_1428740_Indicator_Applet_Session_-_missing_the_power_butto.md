---
title: "Indicator Applet Session - missing the power button"
date: 2010-03-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2010-03-13
I somehow screwed up and have lost the indicator applet's power button. It's also gone with a fresh user so it's nothing in my home dir.

[img]http://img.xrmb2.net/images/713590.png[/img]

Any ideas on how to bring it back?

---

### Post by Keyper7 on 2010-03-13
If the Me Menu is there, then the indicator-applet-session is installed.

Check if the package indicator-session is installed.

---

### Post by MacUntu on 2010-03-13
ROFL - that did it, thanks! :)

I wonder why/when this package got uninstalled on this system.

---

### Post by tekstr1der on 2010-03-13
> **MacUntu said:**
> I wonder why/when this package got uninstalled on this system.

Based on your screenshot, it never did. Both indicator-sound and indicator-messages are displayed, which tells you that the Indicator Applet is running. The battery indicator displays inside of this applet. Perhaps you are experiencing:

Bug #529052: battery applet comes and goes in notification area
[https://bugs.launchpad.net/ubuntu/+source/indicator-application/+bug/529052](https://bugs.launchpad.net/ubuntu/+source/indicator-application/+bug/529052)

Also, Keyper7's comment was correct, but should not have any bearing on your issue. Indicator-applet-session contains the MeMenu and session options like logging off and changing users. Both applets are described well in the applet selector (for a change). This was a papercut focus.

---

### Post by MacUntu on 2010-03-13
> **tekstr1der said:**
> battery applet
Maybe there's a misunderstanding. When I say power button I mean the button we all know from our remotes.

---

### Post by Keyper7 on 2010-03-13
tekstr1der, by "power button", MacUntu meant "shutdown button", not "battery button".

EDIT: it's just lovely when everyone is posting at the same time and I end up posting redundant stuff...

---

### Post by tekstr1der on 2010-03-13
> **MacUntu said:**
> Maybe there's a misunderstanding. When I say power button I mean the button we all know from our remotes.

Oops, yes I did misunderstand that. Didn't see the battery and have been dealing with that bug.

> **MacUntu said:**
> 
Nope, try it yourself and remove indicator-session. What you add as "Indicator Applet Session" will only contain the MeMenu.

This, again goes to the misunderstanding. Yes, indicator-session and indicator-me packages are, by default displayed inside the "Indicator Applet Session". Removing either, while still using the applet will make the removed disappear. Sorry for the confusion, I was subconsciously hoping for another victim of the disappearing battery problem!

---

### Post by MacUntu on 2010-03-13
> **tekstr1der said:**
> I was subconsciously hoping for another victim of the disappearing battery problem!

I'm sorry - seems I'm only getting the boring bugs. :KS

---

