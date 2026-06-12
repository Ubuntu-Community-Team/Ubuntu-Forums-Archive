---
title: "Proposal : Solution to small-screen resolution issues"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by ricster on 2008-08-04
This can probably apply anywhere where a window or dialog is physically too large for the screen resolution:

With keyboard:

1. If the in-focus window is wider or taller than the visible resolution...

2. And the user has tabbed to a control (button etc.) ...

3. check if the coords of the window + control + screen are greater (or lesser if it's off the top/left) than the width/height of the screen.

4. adjust window position (to negative screen coords if needed) so that control is visible.



With mouse:

1. If the in-focus window is wider or taller than the visible resolution...

2. And the mouse is at the edge of the screen...

3. And hovering over the window in question...

4. "scroll" the window in the opposite direction (at a non-cpu-clock related speed!) to reveal more contents of the window to the user.




That's a few IFs to verify for every keypress or mousemove hence the first check is a straight comparison of window height/width vs the screen - which could be in turn set in a flag when the window receives focus.


Aside: My original idea - and a potentially more destructive and far-reaching one - and one that the good old Amiga was easily capable of supporting - would be to decouple the screen resolution from the desktop resolution. So if the installer demands a "desktop" of 800x600 and your device only supports a "screen" of 640x480 then moving the mouse to the edge of the screen would scroll the desktop beneath it. I can imagine this being handy for people like me who prefer multiple monitors to multiple-desktops, just make your desktop four times the size of your screen and scroll around each "quadrant" :-)

---

