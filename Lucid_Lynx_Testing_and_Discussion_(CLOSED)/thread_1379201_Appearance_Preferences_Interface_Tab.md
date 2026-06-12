---
title: "Appearance Preferences Interface Tab"
date: 2010-01-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Robin Nixon on 2010-01-12
I'm just looking at the Appearances window in the latest Alpha update and have a question. Has the *System -> Preferences -> Appearance -> Interface* tab gone for good?

This is the one that used to offer the checkboxes for "Show icons in menus" and "Editable menu shortcut keys", as well as how text should be displayed (next to or below icons etc).

If so is there somewhere else I can access these options?

---

### Post by Puck7 on 2010-01-12
Since this is an alpha that you are testing, it may be that you'll see it later on. Such things happen in such early alpha releases.

---

### Post by david_ on 2010-01-12
It's not a bug it's a feature :-|

see: [https://bugzilla.gnome.org/show_bug.cgi?id=592756](https://bugzilla.gnome.org/show_bug.cgi?id=592756)

---

### Post by Robin Nixon on 2010-01-12
> **david_ said:**
> It's not a bug it's a feature :-|

see: [https://bugzilla.gnome.org/show_bug.cgi?id=592756](https://bugzilla.gnome.org/show_bug.cgi?id=592756)

Thanks for that info David.

I think that tab was just fine the way it was in 9.04, when all the options worked properly. Even in 9.10 2/3 of the options there still worked (turning icons off was the iffy one). Oh well.

---

### Post by chrisccoulson on 2010-01-12
This was also documented in the changelog of the upload: [https://lists.ubuntu.com/archives/lucid-changes/2010-January/003172.html]("https://lists.ubuntu.com/archives/lucid-changes/2010-January/003172.html")

---

### Post by tghe-retford on 2010-01-12
It's a permanent change and if I recall, there is going to be more changes to the UI (moving towards Gnome 3), and no tweak program will be able to change them, because they won't be part of Gnome!

Probably the biggest reason why I switched back to KDE.

---

### Post by chrisccoulson on 2010-01-12
> **tghe-retford said:**
> It's a permanent change and if I recall, there is going to be more changes to the UI (moving towards Gnome 3), and no tweak program will be able to change them, because they won't be part of Gnome!

The last statement there is untrue. The GNOME developers removed these options from the standard interface because they believe that they actually belong in an external tweak application (targetted at power users), and have encouraged people to step up to the plate in order to develop that.

Applications will still be able to modify settings in the usual way using the standard API's.

Someone needs to volunteer to develop that application though - it won't be a part of the core GNOME desktop.

---

### Post by celticbhoy on 2010-01-12
> **chrisccoulson said:**
> The last statement there is untrue. The GNOME developers removed these options from the standard interface because they believe that they actually belong in an external tweak application (targetted at power users), and have encouraged people to step up to the plate in order to develop that.

Applications will still be able to modify settings in the usual way using the standard API's.

Someone needs to volunteer to develop that application though - it won't be a part of the core GNOME desktop.

Step forward Ubuntu Tweak!

---

### Post by tghe-retford on 2010-01-13
> **chrisccoulson said:**
> The last statement there is untrue. The GNOME developers removed these options from the standard interface because they believe that they actually belong in an external tweak application (targetted at power users), and have encouraged people to step up to the plate in order to develop that.

Applications will still be able to modify settings in the usual way using the standard API's.

Someone needs to volunteer to develop that application though - it won't be a part of the core GNOME desktop.
When I read through the bug reports and first heard of this, there was talk of a suggestion that the relevant gconf keys would be removed completely. At that point, I switched to KDE (there were other reasons, KDE 4 maturing being a main one). My understanding is that the long term goal for Gnome was to remove the icons from menus and buttons to enable a clean UI, and removing the Interface tab from the Appearance window was part of this process.

---

### Post by conorsulli on 2010-02-22
> **chrisccoulson said:**
> The last statement there is untrue. The GNOME developers removed these options from the standard interface because they believe that they actually belong in an external tweak application (targetted at power users), and have encouraged people to step up to the plate in order to develop that.

Applications will still be able to modify settings in the usual way using the standard API's.

Someone needs to volunteer to develop that application though - it won't be a part of the core GNOME desktop.

Soon, we will need a poweruser app to change a wallpaper.....

---

### Post by joey-elijah on 2010-02-22
I can't even remember what the interface tab did let alone noticing it was gone so this move won't affect me that much at all.

---

### Post by 6205 on 2010-02-22
> **tghe-retford said:**
> It's a permanent change and if I recall, there is going to be more changes to the UI (moving towards Gnome 3), and no tweak program will be able to change them, because they won't be part of Gnome!

Probably the biggest reason why I switched back to KDE.

Yep... it's slowly again KDE time :)

---

### Post by emarkay on 2010-02-22
Wait, so how do I then select my Desktop theme, Font choices and preferences and my trusty old "solid black background"?

---

### Post by Darkshade on 2010-02-22
> **emarkay said:**
> Wait, so how do I then select my Desktop theme, Font choices and preferences and my trusty old "solid black background"?

Only the Interface tab was removed (options to change toolbar to icons, text, icons+text and to show or not icons in menus). The rest is still there.

---

### Post by emarkay on 2010-02-22
> **Darkshade said:**
> Only the Interface tab was removed (options to change toolbar to icons, text, icons+text and to show or not icons in menus). The rest is still there.

So the "Right Click" option will remain through release?

---

### Post by suprman2020 on 2010-03-13
So does anyone know how to remove the text from the icons? I'm getting sick of having forward next to the forward icon.

---

### Post by Sam on 2010-03-13
> **suprman2020 said:**
> So does anyone know how to remove the text from the icons? I'm getting sick of having forward next to the forward icon.

```
gconftool --set /desktop/gnome/interface/toolbar_style --type string icons
```

---

### Post by suprman2020 on 2010-03-13
> **Sam said:**
> ```
gconftool --set /desktop/gnome/interface/toolbar_style --type string icons
```

You're a life saver. Thank you very much...

---

### Post by jeffsa12 on 2010-03-21
You can add the icons to the main menu as follows:

1) In the terminal, call up gconf-editor 

2) Navigate to desktop/gnome/interface

3) Scroll down and check the menus_have_icons box.

Done!!

I always edit the panel to use the "gnome main menu". 
I added an entry for gconf-editor in the menu under the "System Tools" heading, using the edit menu function.

---

### Post by dino99 on 2010-03-21
other nice applet: search magicchicken into synaptic

---

### Post by Sophont on 2010-03-21
Getting tired of having to change half a dozen settings for every install - and now having to start gconf-edit to do it too I wrote a tiny Python Script.

Just comment/delete out any settings you want to stay at default.


```
#! /usr/bin/python

import gconf

def set_gconf_val (key, value):
    client = gconf.client_get_default ()
    
    if type (value) == type (""):
        client.set_string (key, value)
    if type (value) == type (True):
        client.set_bool (key, value)
    if type (value) == type (0):
        client.set_integer (key, value)
    
#=== main ======================================================================
if __name__ == "__main__":
    #=== System -> Preferences -> Appearence ===
    # Show icons in menus
    menus_have_icons = False
    set_gconf_val ("/desktop/gnome/interface/menus_have_icons", menus_have_icons)
    
    # Toolbar button labels
    #"both", "both-horiz", "icons", "text".
    toolbar_style = "icons"
    set_gconf_val ("/desktop/gnome/interface/toolbar_style", toolbar_style)

    #=== Nautilus ===
    # Always use the location entry, instead of the pathbar
    always_use_location_entry = True
    set_gconf_val ("/apps/nautilus/preferences/always_use_location_entry", always_use_location_entry)
    
    #=== Update Notifier ===
    # Always use the location entry, instead of the pathbar
    auto_launch = False
    set_gconf_val ("/apps/update-notifier/auto_launch", auto_launch)
    

```

---

### Post by HoboJ on 2010-03-21
> **jeffsa12 said:**
> You can add the icons to the main menu as follows:

1) In the terminal, call up gconf-editor 

2) Navigate to desktop/gnome/interface

3) Scroll down and check the menus_have_icons box.

Done!!


Thanks so much! I don't understand why that's off by default. It just looks so disjointed without those additional icons.

---

### Post by Uncle Spellbinder on 2010-03-21
> **chrisccoulson said:**
> ...GNOME developers removed these options from the standard interface because they believe that they actually belong in an external tweak application (targetted at power users), and have encouraged people to step up to the plate in order to develop that.

Applications will still be able to modify settings in the usual way using the standard API's.

Someone needs to volunteer to develop that application though - it won't be a part of the core GNOME desktop.[QUOTE=celticbhoy;8654106]Step forward Ubuntu Tweak![/QUOTE]

Indeed. Ubuntu Tweak has been a wonderful app in Karmic and has proven quite valuable in Lucid as well. I'm happy that the Ubuntu Tweak dev(s) have implemented a way to replace the "interface" functionality.

---

### Post by emarkay on 2010-03-21
> **chrisccoulson said:**
> The last statement there is untrue. The GNOME developers removed these options from the standard interface because they believe that they actually belong in an external tweak application (targeted at power users), and have encouraged people to step up to the plate in order to develop that.
Applications will still be able to modify settings in the usual way using the standard API's.
Someone needs to volunteer to develop that application though - it won't be a part of the core GNOME desktop.

Sort of like GM saying , oh we won't be putting a switch on the dash to turn on the headlights anymore, but  wait for the aftermarket to design and test one. Then you can find it and install it yourself.  Meanwhile...

Now that's assinine logic here for sure!

---

### Post by IndyGunFreak on 2010-04-05
> **jeffsa12 said:**
> You can add the icons to the main menu as follows:

1) In the terminal, call up gconf-editor 

2) Navigate to desktop/gnome/interface

3) Scroll down and check the menus_have_icons box.

Done!!

I always edit the panel to use the "gnome main menu". 
I added an entry for gconf-editor in the menu under the "System Tools" heading, using the edit menu function.

The menu icon thing kind of annoyed me at first, but if thats all there is to it, its not a big deal.

---

