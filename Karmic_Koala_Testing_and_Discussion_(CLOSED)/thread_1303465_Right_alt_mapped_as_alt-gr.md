---
title: "Right alt mapped as alt-gr"
date: 2009-10-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by michael37 on 2009-10-28
By default, my Karmic got installed with right Alt mapped to Alt-Gr functionality aka ISO_Level3_Shift.

Given the changes in Karmic, I don't even understand if the binding happens in gnome or in udev.

For some people, having level 3 switch might be interesting.  I have a simple US keyboard and I don't have third level keys, so I don't care for Alt-gr.  I want my right alt to be right alt.  How can I do that?

[xev tells me that]("https://wiki.ubuntu.com/Hotkeys/Troubleshooting"):
'Right alt
keycode 108 = (keysym 0xfe03, ISO_Level3_Shift), state = 0x0
keycode 108 = (keysym 0xfe03, ISO_Level3_Shift), state = 0x80
'Left alt 
keycode 64 = (keysym 0xffe9, Alt_L), state = 0x0
keycode 64 = (keysym 0xffe9, Alt_L), state = 0x8

---

