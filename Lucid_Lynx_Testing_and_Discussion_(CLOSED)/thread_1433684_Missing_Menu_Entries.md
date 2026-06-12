---
title: "Missing Menu Entries"
date: 2010-03-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Uncle Spellbinder on 2010-03-19
I seem to have some missing menu entries. System Toopls used to have Gconf Editor, Gdebi and several more. Now empty. Nvidia settings is also missing in administration. I can only get to nvidia settings by doing *gksudo nvidia-settings*. Same for gconf. Anyone else seeing this?

---

### Post by PenguinInside on 2010-03-19
> **Uncle Spellbinder said:**
> Running March 18th daily build. I seem to have some missing menu entries. System Toopls used to have Gconf Editor, Gdebi and several more. Now empty. Nvidia settings is also missing in administration. I can only get to nvidia settings by doing *gksudo nvidia-settings*. Same for gconf. Anyone else seeing this?

gconf and Gdebi weren't there in default new installs of Karmic Koala either.

---

### Post by Uncle Spellbinder on 2010-03-19
> **PenguinInside said:**
> gconf and Gdebi weren't there in default new installs of Karmic Koala either.

Yes they were. In Karmic as well as Lucid Alpha 3 

When you went to *system > preferences > main menu*, you could check what items you wanted to see under various catagories. The *system tools* entry is now blank (except for 2 things I installed). It use to have half a dozen items to choose from. See image below:

---

### Post by gillmt on 2010-03-19
I can't find them either - searched the menu editor and searched synaptic to see I have them installed - can't find control centre either.

---

### Post by Uncle Spellbinder on 2010-03-19
> **gillmt said:**
> I can't find them either - searched the menu editor and searched synaptic to see I have them installed - can't find control centre either.

Finally!  I was beginning to think I was alone.



Best image I could locate of how it looked in Karmic (and Lucid Alpha 3)

[img]http://content.imagesocket.com/images/menueditor9ac.png[/img]

---

### Post by Uncle Spellbinder on 2010-03-19
Wow. You're right. Control Center is gone, too. The menu seems to be a mess now.

---

### Post by cariboo on 2010-03-19
That's strange, because the only things in the system tools on my system are items I've installed myself. I'm running gnome-shell atm, that's why I have the control center. see screen-shot.

---

### Post by Uncle Spellbinder on 2010-03-19
Bug? New "Feature"?  

Either way, I don't like it.

---

### Post by PenguinInside on 2010-03-19
> **Uncle Spellbinder said:**
> Yes they were. In Karmic as well as Lucid Alpha 3 


Oops, sorry, you're right. Thanks.

I was looking under System>Preferences and System>Administration in the menu editor. (Right click on the menu > Edit Menus.)

Gdebi and gconf are in Applications > System Tools

---

### Post by Didius Falco on 2010-03-19
This is why I prefer to upgrade rather then fresh install. Still, I think I'm going to wipe a partition (I have several clones of my current 9.10 install all set up for backup and future testing releases - I'm good until after 11.10 at this point) and do a fresh install, just to see what happens...

---

### Post by Uncle Spellbinder on 2010-03-19
Thanks for the screenie, PenguinInside

So here's the bottom line. 

Karmic and Lucid Alpha 3:
[img]http://content.imagesocket.com/images/Main_Menu_Originala52.png[/img]

Lucid Beta 1:
[img]http://content.imagesocket.com/images/Main_Menu_Lucid_Beta2cd.png[/img]

---

### Post by forcecore on 2010-03-19
Beta1 still has lost those icons...

---

### Post by Uncle Spellbinder on 2010-03-19
So, are there only a few of us with this issue, or are others seeing this as well?

---

### Post by forcecore on 2010-03-19
it is just strange anomaly, daily 17 was ok, beta1 icons gone, now after update icons back??????

---

### Post by Uncle Spellbinder on 2010-03-19
> **forcecore said:**
> it is just strange anomaly, daily 17 was ok, beta1 icons gone, now after update icons back??????
Just had 26 updates. System Tools is still empty and Control Center is still not present.

---

### Post by scradock on 2010-03-19
> **Uncle Spellbinder said:**
> Just had 26 updates. System Tools is still empty and Control Center is still not present.

I fresh-installed March 18th daily (amd64) and see Control Center below Preferences and Administration in the system menu.

---

### Post by Uncle Spellbinder on 2010-03-19
> **scradock said:**
> I fresh-installed March 18th daily (amd64) and see Control Center below Preferences and Administration in the system menu.
I just reformatted and fresh-installed Beta 1 (32-bit) and there is **no** Control Center below Preferences and Administration in the system menu. And nVidia settings is not preaent. And *system > preferences > main menu >system tools* is empty.

---

### Post by Uncle Spellbinder on 2010-03-19
If someone could direct me where to file a bug, I'd be glad to. I've not had the need to file a bug recently. Rusty I guess.

---

### Post by Uncle Spellbinder on 2010-03-19
Bug here: [Missing Menu Entries - Lucid Beta 1](https://bugs.launchpad.net/ubuntu/+bug/542300)

Please comment or click "this bug effects me".

---

### Post by Uncle Spellbinder on 2010-03-20
Just a friendly bump.

I know this is not the most pressing issue for 10.04, but I'd sure like to see this addressed.

---

### Post by mc4man on 2010-03-20
Your bug has been marked as invalid and a dup of the gnome-panel deal from last night ( which I don't think is what you were talking about.

I've seen several things not enabled by default and now not available to be enabled in 'edit menus'

Like '[File Management]("https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/534115")', gconf-editor, gstreamer-properties (MSS), ect., ect.

---

### Post by Uncle Spellbinder on 2010-03-20
> **mc4man said:**
> Your bug has been marked as invalid and a dup of the gnome-panel deal from last night ( which I don't think is what you were talking about.)

It had/has nothing to do with the mess last night. This is odd. Why mark as invalid? It sure is valid as far as I'm concerned.

:-k

---

### Post by Uncle Spellbinder on 2010-03-20
OK. The last updates seem to have corrected the nVidia setting and Control center issue. However, the menu entries in s*ystem > preferences > main menu >system tools* is still empty and *menu > system tools* is still empty.

---

### Post by jpeddicord on 2010-03-20
> **Uncle Spellbinder said:**
> It had/has nothing to do with the mess last night. This is odd. Why mark as invalid? It sure is valid as far as I'm concerned.

:-k

Commented on the report. Looking deeper, it's a duplicate of bug #542343, definitely. Those are the same .desktop parsing errors that were appearing when launching gnome-panel. It's an issue with the build system that was causing malformed .desktop entries in packages to be sent out, so when the menu tries to read them, it can't and just skips them.

For the affected packages/menu entries, you'll just have to wait for them to be rebuilt with the newer cdbs.

---

### Post by Uncle Spellbinder on 2010-03-20
@ jpeddicord

Appreciate the clarification. Thanks, much.

---

### Post by gillmt on 2010-03-21
Not sure whether my fix will survive a reboot but I just added gconf-editor, GDebi and control centre to the menu (by looking up the commands on my Karmic machine) and they have all appeared on the menu.

---

### Post by jaoc223 on 2010-03-23
Where do you find control center? is it for kde or gnome?
Thanks

---

### Post by philinux on 2010-03-23
> **jaoc223 said:**
> Where do you find control center? is it for kde or gnome?
Thanks

gconf-editor is for gnome. It should be under Apps>system tools. Or at least in system>admin or prefs.

Seeing as gconf-editor is one way to shift those darn windows buttons.

---

### Post by Uncle Spellbinder on 2010-03-23
Just had a big update, 104 of them. was hoping this issue/bug would get fixed. Not yet, it appears. "Control center", along with "Configuration Editor", "File Browser", "GDebi", "Report A Problem" and "Root Terminal" are still missing in system > preferences > main menu > system tools.

---

### Post by philinux on 2010-03-23
> **Uncle Spellbinder said:**
> Just had a big update, 104 of them. was hoping this issue/bug would get fixed. Not yet, it appears. "Control center", along with "Configuration Editor", "File Browser", "GDebi", "Report A Problem" and "Root Terminal" are still missing in system > preferences > main menu > system tools.

This is a worrying trend. Together with windows buttons, nautilus breadcrumbs, no ubuntu-one icon in notification area. etc etc..

---

### Post by Uncle Spellbinder on 2010-03-23
I know ther's still another beta and an rc to go. Nevertheless, I must agree. This *is* a "worrying trend."

Edit: And the [bug I filed](https://bugs.launchpad.net/ubuntu/+bug/542300) has been marked status - confirmed, importance - low. 

*Low*? Really???

---

### Post by jaoc223 on 2010-03-23
Got it. Thanks phil

---

### Post by gillmt on 2010-03-23
The items I have added to the menu are still there after reboots and they were easy enough to add to the menu - even appeared with the correct icons.

---

### Post by ankspo71 on 2010-03-23
> **Uncle Spellbinder said:**
> Just had a big update, 104 of them. was hoping this issue/bug would get fixed. Not yet, it appears. "Control center", along with "Configuration Editor", "File Browser", "GDebi", "Report A Problem" and "Root Terminal" are still missing in system > preferences > main menu > system tools.

My system tools menu was completely empty when I did a clean install of beta1. 
I added gconf-editor myself.
Nvidia settings menu entry I always had since enabling "current" drivers.

I also installed wine and it created the Wine menu directory at the top of my menu. It didn't alphabetize itself like it used to do.

---

### Post by Uncle Spellbinder on 2010-03-24
> **gillmt said:**
> The items I have added to the menu are still there after reboots and they were easy enough to add to the menu - even appeared with the correct icons.
Items I've added are there too. I'm not talking about that. I'm talking about "Control center", along with "Configuration Editor", "File Browser", "GDebi", "Report A Problem" and "Root Terminal" missing in *system > preferences > main menu > system tools.*

---

### Post by Uncle Spellbinder on 2010-03-26
88 updates today. Still no fix.

:?

---

### Post by gillmt on 2010-03-26
Sorry - my thread appeared in the wrong place - I looked up the menu descriptions for GDebi, control cetre etc and added them to the menu - then rebooted. The items are still there and the correct icons appeared next to them. Like you, no fix has appeared in any of the updates

---

### Post by forcecore on 2010-03-26
tested 26 daily still no icons like control panel, gconf editor....

---

### Post by Uncle Spellbinder on 2010-03-30
Nearly 200 updates the past several days. Still nothing. [This bug](https://bugs.launchpad.net/ubuntu/+source/gnome-menus/+bug/542300) is not being addressed. 

"Importance - Low / Unassigned"

In the grand scheme of things, this may not be the most important of bugs. But I don't consider it "low" on the importance meter. After all, "Control center" is missing, along with "Configuration Editor", "File Browser", "GDebi", "Report A Problem" and "Root Terminal" in *system > preferences > main menu > system tools*.

Really? Low?

:???: :-s :-k

---

### Post by Uncle Spellbinder on 2010-04-01
Finally! This bug is fixed in the package gnome-menus - 2.30.0-0ubuntu2.  Hmmmm. They've moved Synaptic in System Tools Menu, too. I can live with that. It is a "tool" after all. And with Software Center being focused on as a replacement for Synaptic, I guess it makes sense.

Glad this is fixed, finally. Though I still cannot locate 'Control Center'. Hopefully this will be addressed soon.

---

### Post by mc4man on 2010-04-01
> They've moved Synaptic in System Tools Menu, too. 

Whether that was intended or not can't say. It does have an improper launch command and is of no value, so it would seem to be a mistake.
(Logically it doesn't really belong there

---

