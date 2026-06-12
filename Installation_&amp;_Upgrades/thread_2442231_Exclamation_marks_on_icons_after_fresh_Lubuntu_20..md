---
title: "Exclamation marks on icons after fresh Lubuntu 20.04 install"
date: 2020-05-01
forum: Installation &amp; Upgrades
---

### Post by highsider on 2020-05-01
Exclamation marks on icons after fresh 20.04 install. 

Any reason for this? 

Installed on a couple of machines but have the the same issue. All works okay - just don't want the exclamation marks.

[IMG]https://live.staticflickr.com/65535/49840317943_c64d8f61bd_b.jpg[/IMG]

---

### Post by guiverc on 2020-05-01
The exclamation point is because you don't own those 'files'  (they are owned by 'root')

If you click "File Properties" in `pcmanfm-qt` you'll note you have restricted rights in the Permissions tab. The exclamation point is how `pcmanfm-qt` tells you they're not owned by you.

I suspect using `pcmanfm-qt` to view menu applications wasn't treated as a special case (to hide the non-ownership) to be consistent with it's use in other locations, by the developer who created the application (pcman or [COLOR=#252525][FONT=sans-serif]Hong Jen Yee[/FONT][/COLOR])

---

### Post by highsider on 2020-05-01
Thanks. Shame it's not subtle and looks like something is wrong rather than informative.

---

