---
title: "NEW new theme idea."
date: 2010-03-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by asmoore82 on 2010-03-06
OK, I've been telling people for years that GNOME's menubar in the upper-left
corner makes more sense than anything else for English speakers
because we read left-to-right, top-to-bottom.

So this new theme comes along with the window management buttons moved to the left,
and I want to argue about it but I can't for the very same reason as above.

The "looks like a Mac" argument is no good either because if the buttons stay
where they've always been, it "looks like a Windows."

So we're stuck, where do we go from here?

I have a solution!
The buttons must go on the left because English speakers read left-to-right, top-to-bottom.
But, the close button needs to stand alone, where it is impossible to hit by accident: on the right.

I've tweaked and attached the Ambiance theme for this.
Run this command to get the buttons in the right places:
```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string "maximize,minimize:close"
```

P.S. I also darkened the grip on the scrollbars

---

### Post by LKjell on 2010-03-06
You might read from left to right but you keep your mouse to the right more often because the scroll bar is there and when you read a mouse on the left side will distract more than it was on the right side. 
And when you use your mouse you tend to pull it to the right since you are using the right hand. It is more comfortable to move the mouse to the right than to the left side.

I might be wrong but you might see where your mouse is often on your screen.

---

### Post by asmoore82 on 2010-03-06
I hear some partially valid arguments but I don't see any suggestions...
Where to do you keep your Main Menu/Menubar?

---

### Post by Owen.C93 on 2010-03-06
TBH I could get used to having the buttons in the center. But the left? eww.

---

### Post by VMC on 2010-03-06
> **LKjell said:**
> ...
I might be wrong but you might see where your mouse is often on your screen.

Your right. I knew there was a reason I kept my mouse to the right.

=== off-topic, and to the right ===
It's like for the people in the US driving a car on the right side seems the right thing to do, until they go to somewhere like Japan, then get confused, even if someone else drives...

---

### Post by KrazyPenguin on 2010-03-06
Try switching the brake/ accelerator pedals and see what happens!!??
:shock:

---

### Post by gexi on 2010-03-06
lol @ the brake/accelerator comment :)

hmmn, have to say, i don't really have a problem with differing positioning of the buttons.

i think there is a problem with the buttons themselves (at least if i seriously consider how my perception works). i can't really distinguish fast enough between the minimize and maximize button. i'm using the theme for one day now, and the problem stayed the same (usually i'm not that slow in relearning coordinative behaviour). i still have to really look at the buttons half a second before i know which one to push.

what do you guys think?

(well actually i think those buttons are only placeholders, but if not ...)

---

### Post by kansasnoob on 2010-03-06
> So we're stuck, where do we go from here?

AFAIK that's only true of notify-osd, pretty much everything else is totally configurable one way or another.

And it's only a matter of time until someone comes up with a decent workaround for the notify-osd placement, time displayed, etc.

Regarding one set position for window controls I can never see that happening. It's Linux, what flavor do you prefer today sir???????????????

---

### Post by LKjell on 2010-03-06
> **asmoore82 said:**
> I hear some partially valid arguments but I don't see any suggestions...
Where to do you keep your Main Menu/Menubar?

I am using XMonad to do the tiling/resize for me. There is no close, maximum and minimum button for me. No menubar either. However this is not a suggestion since not everybody likes tiling WM.

---

