---
title: "Enable touch-scrolling in Firefox"
date: 2016-12-05
forum: MINT
---

### Post by math19852 on 2016-12-05
In Firefox, swiping on the touch screen results in selecting text,  instead of scrolling (like on an iPad). Is it possible to change the  behaviour, so that the touch screen can be used to scroll, while the  mouse can be used to select text?

In Chrome, the behaviour is as expected (swipe to scroll, (mouse)drag to select).

I'm  using Firefox 50.0 on Linux Mint 18, which uses the Ubuntu 16.04 packages. I have  dom.w3c_touch_events.enabled set to 2, setting it to 1 does not help  either.

Thanks for any help!

---

### Post by howefield on 2016-12-05
Thread moved to the "*MINT*" forum.

---

### Post by math19852 on 2016-12-11
I finally found a solution: start firefox with:

env MOZ_USE_XINPUT2=1 firefox

This enables touch-scrolling for me. Pinch-to-zoom does not work for regular web pages, but it does work on some selected web pages such as Google Maps or OpenStreetMap.

---

