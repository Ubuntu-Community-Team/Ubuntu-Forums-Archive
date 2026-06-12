---
title: "White borders when I switch background image."
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by phibxr on 2010-03-20
At the moment I'm trying the Beta 1 of Lucid Lynx. While being really impressed with the system, I have bumped into a small bunch of annoyances.

When I switch to another background image, I get a 1 pixel wide white border on the left and right edges of the screen. I can cover this area by moving windows above it, so the borders seem to be rendered at the desktop level. The top and bottom bars do extend to the full width of the monitor.

Logging out and back in again solves the problem until I switch background again.

Can someone reproduce this behavior, or should I suspect my video drivers?

---

### Post by macstevejb on 2010-03-20
As indicated elsewhere, a temporary fix for this seems to be issuing the following command in a terminal:

nautilus -q

regards,

---

### Post by phibxr on 2010-03-20
> **macstevejb said:**
> As indicated elsewhere, a temporary fix for this seems to be issuing the following command in a terminal:

nautilus -q

regards,

Thanks! I was about to test this to confirm whether it made a difference, but for some reason I can't get the problem to manifest anymore, despite testing it several times before my last post. :???:

Let's hope the issue is gone for real when Lucid Lynx goes live. :)

---

### Post by AaronMT on 2010-03-20
Thanks for the solution - perhaps this should be pinned?

---

### Post by ElSlunko on 2010-03-21
I think this bug got resolved. Doesn't seem to happen anymore after today's nautilus update.

---

### Post by phibxr on 2010-03-22
I haven't updated Nautilus yet, but the workaround fixed it now when it showed up again. :)

Thanks for the information, and glad to hear that the bug has been fixed!

---

