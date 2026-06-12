---
title: "How to enable ctrl-alt-bksp on kubuntu?"
date: 2009-08-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jbernardo on 2009-08-09
Now that the xorg developers, in their infinite wisdom (and arrogance) decided that the dontzap option could still be used by common mortals to enable ctrl-alt-bksp to kill the currently running x server, can anyone tell me how to enable this again in kde/kubuntu? I've checked the keyboard short-cuts and was unable to find anything related.

---

### Post by scaine on 2009-08-09
It's in keyboard preferences :
System/Prefs/Keyboard/Layouts/Layout Options/Key Sequence to Kill X Server.

Or stop being arrogant yourself and learn ALTGR-SYSRQ-K.  :P

Here's hoping you never need that particular key sequence anyway...

---

### Post by caryb on 2009-08-09
> It's in keyboard preferences :
System/Prefs/Keyboard/Layouts/Layout Options/Key Sequence to Kill X Server.

Is this in Gnome cause i'm stuffed if I can replicate this in Kubuntu:confused:


Cary

---

### Post by sammyboy405 on 2009-08-09
Add this to the bottom of your
/etc/X11/xorg.conf

```
Section "ServerFlags"
        Option  "DontZap"       "False"
EndSection
```


that will enable ctrl alt backspace to restart your gui.  Reboot or manually restart your gui once you add this.

---

### Post by jbernardo on 2009-08-09
1 - dontzap is deprecated, and the dontzap utility is no longer included in karmic, as now you have to do some extra settings using xmodmap. Also, I'd like something I could explain to a less technical user over the phone...
2 - scaine, what you wrote is for gnome, I specified kde; and no, the magic sysreq K sometimes isn't the best choice. I know about it and the reisub mnemonic has also helped me a few times, but the ctrl-alt-bksp key sequence is more convenient in quite a few scenarios.

So, how do I enable this back in kde? Anyone?

---

### Post by hikaricore on 2009-08-09
> **scaine said:**
> Or stop being arrogant yourself and learn ALTGR-SYSRQ-K.  :P

Because that's so much more useful than ctrl_alt_backspace.. a key combo that should never been disabled in the first place.

---

### Post by ranch hand on 2009-08-09
> **sammyboy405 said:**
> Add this to the bottom of your
/etc/X11/xorg.conf

```
Section "ServerFlags"
        Option  "DontZap"       "False"
EndSection
```


that will enable ctrl alt backspace to restart your gui.  Reboot or manually restart your gui once you add this.
This may work with an upgrade from Jaunty but I doubt it, at least on the final release.

Setting the key sequence is the way to go.

---

### Post by scaine on 2009-08-10
No, my apologies, I missed that this was kubuntu (you could try tagging posts in future so that numpties like me who don't read titles very well might pick up on it).

As far as I know, ALT-SYSRQ is exactly the same as CTRL-ALT-BS, but since that's now deprecated across pretty much every distribution in the world, it's probably fighting a losing battle to turn it back on.  Painful, I know, but only for a short while.

The bottom line is that this is a key sequence that shouldn't be "convenient".  You simply shouldn't have to restart X unless it's borked competely and that shouldn't happen often enough to warrant having a "convenient" key sequence.

But I know that that's not answering your question and I don't use KDE enough to help you.  I'll just shut up now...

---

### Post by slakkie on 2009-08-10
> **scaine said:**
> 
As far as I know, ALT-SYSRQ is exactly the same as CTRL-ALT-BS, but since that's now deprecated across pretty much every distribution in the world, it's probably fighting a losing battle to turn it back on.  Painful, I know, but only for a short while.


It is not deprecated, it has been favored to disable the feature on a default installation. The feature will not be removed.

And Xorg made it non-default, distributions just package it with that default, see also this comment: [http://bugs.freedesktop.org/show_bug.cgi?id=10510#c3](http://bugs.freedesktop.org/show_bug.cgi?id=10510#c3)

---

### Post by jbernardo on 2009-08-10
xorg just made it even more difficult to enable - now it has "dontzap false" as a default, but to enable the "terminate_server" action you have to use xkb rulesets -[ http://lists.freedesktop.org/archives/xorg-devel/2009-April/000626.html]("http://lists.freedesktop.org/archives/xorg-devel/2009-April/000626.html"). To me, the bug you linked to starts from a non-existing problem (users pressing ctrl-alt-bksp by mistake), throws some far fetched use cases to justify fixing that "problem", and when a workaround enters mainstream (dontzap) a extra level of difficulty is added (xkb rulesets), just to make sure a emergency measure isn't available unless you enable it very explicitly first. But that is just my opinion and of a few others, and it is dismissed by xorg developers, as you can see by [comment #6]("http://bugs.freedesktop.org/show_bug.cgi?id=10510#c6") on that bug.

---

### Post by wayne_cat on 2009-08-10
> **jbernardo said:**
> xorg just made it even more difficult to enable - now it has "dontzap false" as a default, but to enable the "terminate_server" action you have to use xkb rulesets -[ http://lists.freedesktop.org/archives/xorg-devel/2009-April/000626.html]("http://lists.freedesktop.org/archives/xorg-devel/2009-April/000626.html"). To me, the bug you linked to starts from a non-existing problem (users pressing ctrl-alt-bksp by mistake), throws some far fetched use cases to justify fixing that "problem", and when a workaround enters mainstream (dontzap) a extra level of difficulty is added (xkb rulesets), just to make sure a emergency measure isn't available unless you enable it very explicitly first. But that is just my opinion and of a few others, and it is dismissed by xorg developers, as you can see by [comment #6]("http://bugs.freedesktop.org/show_bug.cgi?id=10510#c6") on that bug.

Well ... if the Xorg developers are too ignorant ... maybe the KDE developers could add this useful feature to the control center

---

### Post by jbernardo on 2009-08-10
> **wayne_cat said:**
> Well ... if the Xorg developers are too ignorant ... maybe the KDE developers could add this useful feature to the control center

I never called them ignorant. Stubborn - maybe. But anyway, it isn't like I am a developer or contributor. I am just a (frustrated) non paying end user - better if I say that before any developer reminds me of my status.

---

### Post by wayne_cat on 2009-08-10
> **jbernardo said:**
> I never called them ignorant. Stubborn - maybe. But anyway, it isn't like I am a developer or contributor. I am just a (frustrated) non paying end user - better if I say that before any developer reminds me of my status.


Sorry ... did not want say that you called them ignorant ... I call them ignorant .

---

### Post by slakkie on 2009-08-10
> **jbernardo said:**
> xorg just made it even more difficult to enable - now it has "dontzap false" as a default, but to enable the "terminate_server" action you have to use xkb rulesets -[ http://lists.freedesktop.org/archives/xorg-devel/2009-April/000626.html]("http://lists.freedesktop.org/archives/xorg-devel/2009-April/000626.html"). To me, the bug you linked to starts from a non-existing problem (users pressing ctrl-alt-bksp by mistake), throws some far fetched use cases to justify fixing that "problem", and when a workaround enters mainstream (dontzap) a extra level of difficulty is added (xkb rulesets), just to make sure a emergency measure isn't available unless you enable it very explicitly first. But that is just my opinion and of a few others, and it is dismissed by xorg developers, as you can see by [comment #6]("http://bugs.freedesktop.org/show_bug.cgi?id=10510#c6") on that bug.

I never said the reason why was valid. IMO ctrl-alt-bs is very known in the Unix world. If people want to disable it then that should have been documented. 

A similar issue you have with openssh-server, which allows root login as a default. One of the reasons why Ubuntu has disabled root logins..

---

### Post by MickS on 2009-08-10
I case it helps some one else the AltGre+SysRq+K works fine on my KDE4.3 you do have to hold the keys down for about 3 seconds before it does though.


Mick

---

### Post by inportb on 2009-08-11
Theoretically, Alt+SysRq+K should be cleaner and more reliable than Ctrl+Alt+Bksp because it's lower-level (intercepted by the kernel rather than the X-server, and not dependent on X-server responsiveness).

---

### Post by wayne_cat on 2009-08-11
I think they also prefer the sysrq key because it will still work with KMS

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=79e539453b34e35f39299a899d263b0a1f1670bd](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=79e539453b34e35f39299a899d263b0a1f1670bd)

---

### Post by inportb on 2009-08-11
> **wayne_cat said:**
> I think they also prefer the sysrq key because it will still work with KMS

I hadn't thought about that, but it's a good point.

---

### Post by jbernardo on 2009-08-16
> **wayne_cat said:**
> I think they also prefer the sysrq key because it will still work with KMS

Well, I have KMS enabled, and last night I needed to restart X and ctrl-alt-sysrq-K didn't work. ctrl-alt-sysrq-E worked, but after that you need to do the rest of the "magic REISUB" sequence and reboot or shutdown your machine, as it terminates all processes.

So, any idea on how to re-enable ctrl-alt-bksp on kubuntu?

---

### Post by jbernardo on 2009-08-23
Thanks to kubicle in the kubuntuforums, I've now found how to enable it back:

"You can set the option via systemsettings, as well:
SystemSettings>Regional&Language>KeyboardLayout>Advanced>KeySequenceToKillXServer"

This shall work until the xorg guys invent new ways to complicate life for advanced users.

---

