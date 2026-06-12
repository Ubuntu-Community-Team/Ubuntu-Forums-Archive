---
title: "Keeping wallpapers from sliding in Karmic"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Birion on 2009-10-05
Hi, I just installed the new beta (not brave enough for alphas) and there's a small issue which I'm (fairly) certain was not in Jaunty. When you switch viewports (or whatever it's in English), the wallpaper slides with the rest of the applications, and it's dizzying enough to give me a strong headache. Is there a way to hold the wallpaper (and the icons) still? It wouldn't be a problem, I believe, if it were possible to put different wallpaper on each viewport, possibly even separate icons, but now it's just annoying.

---

### Post by oboedad55 on 2009-10-05
> **Birion said:**
> Hi, I just installed the new beta (not brave enough for alphas) and there's a small issue which I'm (fairly) certain was not in Jaunty. When you switch viewports (or whatever it's in English), the wallpaper slides with the rest of the applications, and it's dizzying enough to give me a strong headache. Is there a way to hold the wallpaper (and the icons) still? It wouldn't be a problem, I believe, if it were possible to put different wallpaper on each viewport, possibly even separate icons, but now it's just annoying.

Are you talking about when you access other desktops? If that's it then I don't follow your problem. Could you give a little more info?

---

### Post by Birion on 2009-10-05
> **oboedad55 said:**
> Are you talking about when you access other desktops? If that's it then I don't follow your problem. Could you give a little more info?

I guess. What I mean is when I'm on desktop 1 and click on desktop 2 in the little area in the lower right, the wallpaper actually slides from right to left and is replaced by the same picture sliding in from the right, just like what happens with any open applications (application on desktop 1 is replaced by sliding by the application on desktop 2). But since it's replaced by the same picture, it's rather hard on the eyes, and downright confusing when I switch from e.g. desktop 1 to desktop 4, as it slides through all the desktops between them.

EDIT: Okay, so apparently it was caused by /something/ in Compiz (no idea what, I spent several hours going through it yesterday), since turning the desktop effects off and on again solved everything. :confused:

---

### Post by oboedad55 on 2009-10-05
> **Birion said:**
> I guess. What I mean is when I'm on desktop 1 and click on desktop 2 in the little area in the lower right, the wallpaper actually slides from right to left and is replaced by the same picture sliding in from the right, just like what happens with any open applications (application on desktop 1 is replaced by sliding by the application on desktop 2). But since it's replaced by the same picture, it's rather hard on the eyes, and downright confusing when I switch from e.g. desktop 1 to desktop 4, as it slides through all the desktops between them.

EDIT: Okay, so apparently it was caused by /something/ in Compiz (no idea what, I spent several hours going through it yesterday), since turning the desktop effects off and on again solved everything. :confused:

I understand what you mean now. I have the cube enabled so when I switch desktops the cube flips which may be more to your liking. Experiment in compiz until you find what you like.

---

### Post by ad_267 on 2009-10-05
You can install the compizconfig-settings-manager package to change Compiz settings, you might find something in there to specify the behaviour you're after.

---

### Post by Xgen on 2009-10-05
You can change the wall sliding duration in compiz through the settings manager (ccsm), under Desktop Wall -->Viewport Switching. Set to 0 and uncheck  Show Viewport Switcher Preview under View Switch Preview. I also have it set to switch viewports by clicking the edges of the screen with the mouse under Bindings.

---

### Post by Birion on 2009-10-05
Actually, that's the funniest part - it does exactly what I want it to now, and yet I can't tell any difference in either the plugins used or their settings. It's a mystery. But as long as it works...

---

### Post by mister_pink on 2009-10-05
The behaviour you describe was the default before jaunty, but for jaunty they changed it to what you prefer. I actually prefer the old way, so when I installed jaunty I had to figure out how to change it.

The key is in the compiz settings manager, go to desktop wall, viewport switching. In the "non-sliding windows" bit you need to add "| type=Desktop" to the end of the line.

---

