---
title: "Compiz Plugins Cannot Be Disabled"
date: 2009-03-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Robert Marley on 2009-03-15
I upgraded to Jaunty Alpha 6 and am having some problems configuring Compiz.

First, I am unable to enable/disable/configure some Compiz plugins.  For example, I am unable to disable "Static Application Switcher" through CCSM.  When I uncheck it, it remains enabled, (It still uses the same switcher when I press Alt-Tab.  When I close and relauch CCSM, it will be checked again.  This behavior seems to be happening with all plugins.  I have tried removing these plugins using gconf-editor in /apps/compiz/general/allscreens/options/active_plugins and it doesn't work either.  Removing plugins from the list doesn't seem to disable them.

Secondly, using CCSM, the settings for keybindings are really strange.  If I enter the configuration for the "Static Application Switcher" plugin,the keybinding for "Next Window" which I assume should read "<Alt>Tab", reads "<Alt>Button65289".  This behavior is shared with the keybinding entries for all plugins.  This is unusual to say the least.  If I click to change the keybinding, the dropdown list has "Button 1" through "Button 9" listed, and then "Button 65".  In gconf-editor, they are listed correctly (such as "<Alt>Tab"), but that doesn't seem to have any kind of effect.  I can change these values, or even set them to "Disabled" without and change in Compiz behavior.

My system is fully updated.  If anyone else is having problems, please share.

I'm not sure if this problem is just happening in my system or if it's an actual bug in either Compiz or CCSM.  If other people are having this problem, we should probably file a bugreport, but I don't really know how to do that.

Thanks,
Robert Marley

---

### Post by Nightstrike2009 on 2009-03-18
I find that in compiz config settings manager (>general options>desktop size>horizontal size>) when you adjust the horizontal slider to 4 it resets to 2 but doesn't seem to do this on any other value. This makes "Desktop cube" impossible to activate.

I think this is a bug too but i don't know how to report either.:(

---

### Post by rburkartjo on 2009-03-18
night try this right click on add to panel select workplace switcher. once installed on tool bar click pref on workspace switcher and change to 4 columns 1 row. it did this to get the desktops to 4. see if you have cube now and then delete the workspace switcher from the panel. worked for me

---

### Post by scaine on 2009-03-18
Button assignments in CCSM look okay here - I don't use Static App Switcher, but I looked in there to confirm your issue and it was fine.

You might want to try Simple-CCSM from the repos to see if it "resets" any of these issues you're having.  For example, in Simple-CCSM, you only have one drop down to choose which switcher you'd like to activate.

It's a long shot, I know.

---

