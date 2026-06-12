---
title: "&quot;11.10 upgrade&quot; preview features window not resizable"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by ErkDemon on 2011-10-22
I thought I might as well upgrade my little-used netbook from 10.10 to 11.10.

When the Software Centre tells you that a major update is available, and asks if you want to find out about the new features, it opens the animated presentation in a small window that's nowhere near full-size, and which (on an ASUS PC900) is too small to see what's going on. There are scrollbars around the window contents, but the thing's not watchable. 

Unfortunately, even though I'm guessing that there might be enough screen space to show the presentation (ish) inside the window space allowed by the (1024/600?) screen, the window doesn't seem to be manually resizable to let me use the available desktop space more sensibly, and it's also missing a maximise icon.

So, although the tiny corner of the presentation that I can see looks nice, I'm guessing that the window-sizing code was done on a large screen, and hard-coded to use a particular proportion of the desktop size, and maybe nobody thought to test the thing on a netbook. 

On the plus side - easily fixed, by changing the preview window's attributes to make it resizeable.
On the minus side - it makes it look like 11.10 isn't really aimed at users of mobile devices.

---

