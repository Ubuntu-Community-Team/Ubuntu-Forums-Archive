---
title: "Mint 16 Cinnamon DE: Hot corner w/optical mouse &quot;bug&quot;."
date: 2013-12-31
forum: MINT
---

### Post by schema2 on 2013-12-31
I am running mint 16 with cinnamon DE. My bug is pretty annoying. I am annoyed to the point now that I want to give up on hot corners. I have 1 hot corner in the top right of my screen. When I move my optical mouse to the left side of my screen, in the proximity of one of the corners, the cursor will "teleport" to the hot corner on the right side and put me into expo view of my workspaces. I've tried using two different mouses on different surfaces. I am not sure that this problem is hardware related. Is it inherent in mint cinnamon? I can't get a response from anyone on the mint forums, and I haven't read about this issue. I can only assume that I am the only one having it. Is there a solution to this? Will reinstalling be worth the hassle?

post script: it only occurs when I have an application open. And no, I don't have hot corners enabled in all corners. Just one, on the top right.

---

### Post by tgalati4 on 2013-12-31
Try enabling hot corners in all 4 corners and set up null commands for the other 3 and see if that works as a temporary measure.  Also, do you have window scrolling turned on?  You want your mouse to stop at the left or right edge and not continue to scroll past to the next workspace.  That might cause the behavior that you are seeing.

---

### Post by schema2 on 2014-01-02
thanks, I will give that a shot. how exactly do I set up null commands?

---

### Post by tgalati4 on 2014-01-02
Put this in the command box for each corner:

```
notify-send "Hot Corner Selected" "Oops, you hit the lower left corner."
```

Modify it for each corner.

---

