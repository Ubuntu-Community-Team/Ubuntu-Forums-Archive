---
title: "how to set the window frame/border resize width?"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mdurham on 2010-03-24
Hi guys, I'm not sure of the words to describe it. I want to increase the apparent mouse sensitivity width of the window borders, the bit that you click and drag to make a window bigger or smaller. It appears to be only about 1 pixel wide at the moment.
Any ideas?
Cheers, Mike

---

### Post by Zayfox on 2010-03-24
[img]http://i40.tinypic.com/wrb79w.jpg[/img]

---

### Post by mdurham on 2010-03-24
Yes, that's it, but how do I increase the width of the mouse-sensitive part, the border?

---

### Post by tekstr1der on 2010-03-24
I'm pretty sure there is no easy way to configure the window border width. Hence, the existence of this papercut bug:

Resizing windows by grabbing window borders is difficult
[https://bugs.edge.launchpad.net/ubuntu/+source/metacity/+bug/160311](https://bugs.edge.launchpad.net/ubuntu/+source/metacity/+bug/160311)

I've been hoping to see this make it into karmic and now lucid, but don't hold your breath. It was just triaged lately, though so here's hoping. The fix proposed to enlarge the clickable area without visually increasing the width of the border would be ideal and a boon for laptop/touchpad users everywhere!

---

### Post by QLee on 2010-03-24
> **mdurham said:**
> Yes, that's it, but how do I increase the width of the mouse-sensitive part, the border?

Since the border is set in the theme, a quick and easy way to acheive what you describe with a GUI might be to "customise" your theme and choose one with a wider border. System-->Preferences--Appearence, on the Theme tab choose Customize

---

### Post by mannheim on 2010-03-24
You can also modify one of the existing themes, if you are happy editing the relevant files and don't mind that your windows will have a heavier-looking border.

Eg, to create a version of Ambiance with thicker borders, do the following as root[LIST=1]
[*]Create a copy of /usr/share/themes/Ambiance and call it /usr/share/themes/Ambiance-Mod
[*]In the new Ambiance-Mod directory, edit index.theme. Change "Ambiance" to "Ambiance-Mod" in the "Name" line and in the "MetacityTheme" line.
[*]Edit the file metacity-1/metaticity-theme-1.xml. Change the name tag. Then look for the lines with "left_width" and "right_width", and change the value from "1" to something like "4" (or whatever).
[*]Now got to Preferences->Appearance, and select the new theme.
[/LIST]

The result isn't perfect (the drawing of the corners is now a little off. Making the bottom corners not rounded helps).

It really is a bit crazy that the new themes have been given 1-pixel side-borders. This design choice seems to be driven only by appearance, with no thought to actual use. Until the paper-cut bug is fixed in some other way, I think the default themes should have wider borders. (I know there are other ways to resize a window than grab the borders ...)

---

### Post by mdurham on 2010-03-24
Thanks for all your replies, I'll have a bash at modifying a theme. I did add to the bug thanks to tekstr1der's reference.
Cheers, Mike

---

### Post by squiddie on 2010-04-03
Thanks, that helped me.

There are some more tags called 'width' or containing 'width' you can change to enhance the appearance after tweaking the frame. Those are in 'draw_title' and 'draw_title_inactive' and set gradient.

You will also have to change 'YourThemeName/index.theme' and replace the the names, else your theme will be called same as the parent when choosing.

_Button Layout on Lucid_

When using Lucid you will note that they confused the button layout (maximize, close, ...) with Macintoshs which is totally inconvenient to right handers and doesn't support userfriendlyness. Anyhow, in 'YourThemeName/index.theme' change 'ButtonLayout' to 'menu:minimize,maximize,close'.

---

