---
title: "How to launch GRASS from the menu?"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by badaveil on 2008-07-10
The 6.2.2-2ubuntu1 Geographic Resources Analysis Support System(GRASS)was successfully installed in my computer but by default can only be launch from the terminal by the command line "grass". I would like it to launch from the Gnome menu of the UBuntu 8.04. I read it is possible to launch GRASS under the Debian menu as it is more thorough so I managed to install the Debian menu but it doesn't appear to be so. Can anyone advise how to add a GRASS link under the Gnome main menu?

---

### Post by Joshuwa on 2008-07-10
If you click on 'System' -> 'Prefences' -> 'Main Menu' it will open up the menu configuration, where you can add a new item - in this case, a launcher that runs the command 'grass62'

---

### Post by iaculallad on 2008-07-10
> **badaveil said:**
> The 6.2.2-2ubuntu1 Geographic Resources Analysis Support System(GRASS)was successfully installed in my computer but by default can only be launch from the terminal by the command line "grass". I would like it to launch from the Gnome menu of the UBuntu 8.04. I read it is possible to launch GRASS under the Debian menu as it is more thorough so I managed to install the Debian menu but it doesn't appear to be so. Can anyone advise how to add a GRASS link under the Gnome main menu?

Right-click on the "Applications" menu (Top panel) and select "Edit Menus", click on Applications and Accessories (but you could use other menu options). Click on the "New Item" button to launch "Create Launcher". For the values:

Type: Application in Terminal
Name: GRASS
Command: grass
Comment: Optional

and click on OK. So everytime you want to launch GRASS, navigate to Applications->Accessories, and select GRASS.

---

### Post by badaveil on 2008-07-11
iaculallad,joshuwa

Yes, the GRASS link under the main menu works. Thanks.

If I could ask another favour, would you happen to know what the command line is instead of "grass" so that whenever I click GRASS under the main menu, it would jump straight to the GRASS startup as if I were to hit RETURN to continue?

That would be brilliant.

---

### Post by dfs700 on 2008-07-22
Instead of "grass", use "grass -wxpython" or "grass -tcltk" respectively to launch with GIS Manager.

---

### Post by badaveil on 2008-07-22
> **dfs700 said:**
> Instead of "grass", use "grass -wxpython" or "grass -tcltk" respectively to launch with GIS Manager.

Thanks, actually I'm already happy with the creation of the link via Gnome launcher. My current adventure is trying to figure out how to run the software and I flumble my way through as I am only familiar with ArcView/ArcGIS

---

