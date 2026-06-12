---
title: "Where did my installs go?"
date: 2005-06-04
forum: Installation &amp; Upgrades
---

### Post by lworrell on 2005-06-04
Using synaptic, I installed several games and toys for my son.  The only problem is they do not show up on the K menu.  Is there a way to refresh the menu to get these to appear?  Or do I have to search all of these programs out manually? ](*,)

---

### Post by bored2k on 2005-06-04
[QUOTE=lworrell]Using synaptic, I installed several games and toys for my son.  The only problem is they do not show up on the K menu.  Is there a way to refresh the menu to get these to appear?  Or do I have to search all of these programs out manually? ](*,)[/QUOTE]
 Install menu and menu-xdg packages from synaptic then log in & out. If they dont show (or a Debian menu with them doesnt) try to see with the menu editor if the debian menu is hidden.

---

### Post by SGC on 2005-06-04
[QUOTE=lworrell]Using synaptic, I installed several games and toys for my son.  The only problem is they do not show up on the K menu.  Is there a way to refresh the menu to get these to appear?  Or do I have to search all of these programs out manually? ](*,)[/QUOTE]
 Try to use kde applications finder , just go to kmenu and then choose run command and type:
kappfinder

Once the program opens, hit the scan button.

---

### Post by mingus on 2005-06-04
As I recall, this is controlled by the package itself as well as setting up linkages.  I am not aware of any method to regen the entire K-Menu, but if the package didn't do the entire setup, that might not work anyway.  The menu is easy to edit manually (Control Center/Desktop/Panels/Menus/Edit K-Menu).  The command to use can be first tested with Applications/Run application.  Sometimes it is required to provide the explicit path, which you will see in the Synaptic description of package under the "installed files" tab.

Hope this helps.

---

