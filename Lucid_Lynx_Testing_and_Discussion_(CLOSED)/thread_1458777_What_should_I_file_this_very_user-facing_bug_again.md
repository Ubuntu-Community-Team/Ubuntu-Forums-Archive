---
title: "What should I file this *very* user-facing bug against?"
date: 2010-04-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by QwUo173Hy on 2010-04-20
I had nautilus open and attempted to drag an image to a folder in the Places pane on the left. Whatever I did - I ended up with the image linked in my Places menu and I can't get rid of it.

Is this a nautilus or gnome-panel issue. Also, if anyone can suggest how I get rid of it, that would be lovely.

---

### Post by qamelian on 2010-04-20
I think that is handled by nautilus. You should be able to open nautilus and delete this from the nautilus bookmarks.

---

### Post by aysiu on 2010-04-20
I can't replicate it. If I try to drag an image to the sidebar, it either goes into the folder I'm dragging to or just bounces back to where I was trying to drag it from.

---

### Post by QwUo173Hy on 2010-04-20
qamelian, you're right - I was able to remove it from the menu. Thank you. I guess it's not really a bug then.

---

### Post by QwUo173Hy on 2010-04-20
> **aysiu said:**
> I can't replicate it. If I try to drag an image to the sidebar, it either goes into the folder I'm dragging to or just bounces back to where I was trying to drag it from. Aysiu, I can't replicate it either now. I'll stay at it for a while and see if I can figure out how the heck I did that.

---

### Post by aysiu on 2010-04-20
Well, I could replicate it finally... but I had to add the bookmark manually. I couldn't just drag it to the side panel.

---

### Post by QwUo173Hy on 2010-04-20
Finally, I've figured out how to reproduce this. It was in fact a Save As.. dialog that was the culprit. Sorry for missing that detail.

Basically, open Gimp and create or open a file and click Save As. We're only interested in the save as dialog so it's not so important how we get to it.

Finally, browse to any file on your file system and drag it to the left Places pane. It will end up in your Places menu.

---

### Post by aysiu on 2010-04-20
That does seem like a bug, then. If it works that way in GIMP's save dialogue but not in Nautilus, then it's inconsistent behavior, which is confusing to users.

---

### Post by qamelian on 2010-04-20
> **jarlath said:**
> qamelian, you're right - I was able to remove it from the menu. Thank you. I guess it's not really a bug then.
Every once in a while a sneeze or hicccup at in inopportune time causes me to create "accidental" bookmarks, so I was pretty sure it would work! :)

---

### Post by QwUo173Hy on 2010-04-20
So the Save dialog then, that's hardly a gimp component is it? I'd imagine GIMP summons a gnome dialog of some sort that I should file against.

---

