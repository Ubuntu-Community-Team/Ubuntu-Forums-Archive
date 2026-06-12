---
title: "Add link to msql-admin in applications menu"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by Floppyjoe on 2007-04-24
When I updated to Feisty Fawn the link to the mysql-admin disappeared from the applications menu. Can somebody please tell me how to create a link to this file in my menu system?

---

### Post by Floppyjoe on 2007-04-25
Bump.......anyone?

---

### Post by jpeddicord on 2007-04-25
To add a menu item:
[LIST=1]
[*]Right-click on the menu bar and choose **Edit Menus**
[*]Search through the list on the left. If there is a *MySQL Administrator* item that is unchecked, check it to add it to the menu. If there is not one, continue.
[*]Click on a category to store the item in (ie, System Tools).
[*]Click** New Item** on the right.
[*]For ***Name***, type *MySQL Administrator*.
[*]For ***Command***, put *mysql-admin*.
[*]If you want to pick an icon for it, click the **No Icon** button on the left.
[*]Click **OK** to save, and then close the menu editor.[/LIST]Hope this helps!

Jacob

---

### Post by Floppyjoe on 2007-04-27
Thanks Jacob!

I found it in another menu area where it wasn't before in the programming section.

---

