---
title: "Faroese keyboard layout crashes 'keyboard preferences'"
date: 2005-04-30
forum: Installation &amp; Upgrades
---

### Post by Topper on 2005-04-30
I can't install Faroese keyboard layout from the 'system'->''preferences'->'keyboard' as the application crashes on selecting Faroese layout(go to 'Layout'->'Add'-> and choose Faroese. Application crashes). Is there another way to install it, maybe manually?

---

### Post by Alexander Kirillov on 2005-05-02
[QUOTE=Topper]I can't install Faroese keyboard layout from the 'system'->''preferences'->'keyboard' as the application crashes on selecting Faroese layout(go to 'Layout'->'Add'-> and choose Faroese. Application crashes). Is there another way to install it, maybe manually?[/QUOTE]
 Yes, indeed. Please report this bug to bugzilla.gnome.org 

You can manually change the keyboard layout to Faroese systemwide by 
editing Xorg.conf file: in the line
	Option		"XkbLayout"	"us"
replace "us" by the appropriate 2-letter code.

---

