---
title: "Placement of buttons on the titlebar"
date: 2010-03-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by VMC on 2010-03-09
Since this information is buried deeply into a few topics, several pages deep, I thought I would put the information here for easy reference.

Discription

Arrangement of buttons on the titlebar. The value should be a string, such as "**menu:minimize,maximize,spacer,close**"; the colon separates the left corner of the window from the right corner, and the button names are comma-separated. Duplicate buttons are not allowed. Unknown button names are silently ignored so that buttons can be added in future metacity versions without breaking older versions. A special spacer tag can be used to insert some space between two adjacent buttons.

Just high-lite the one of your preference and paste it into a terminal of use Run Application (Alt+F2): 

[LIST]
[*]**Using the Configuration Editor**:
gconf-editor /apps/metacity/general/button_layout[/LIST]

[LIST]
[*]**Buttons Right, Script**:
gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"[/LIST]

[LIST]
[*]**Buttons Left, Script**:
gconftool-2 --set "/apps/metacity/general/button_layout" --type string "minimize,maximize,close:"[/LIST]

---

