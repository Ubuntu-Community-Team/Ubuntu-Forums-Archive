---
title: "btnx workaround in intrepid"
date: 2008-10-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by DLGandalf on 2008-10-01
With btnx broken in intrepid, I did some thinking.
xevdev now works pretty good with all buttons and all, so we can catch these with xbindkeys
Now I can bind commands to buttons but that isn't really what I want because I do not want to run a command but output/emulate a keypress just like btnx did.

xvkbd can do this, but there are a few things holding me back

1. $xvkbd -xsendevent --text "\A\t" 
     for example isn't caught by compiz, but is directly run in the running console (in my test case gnome-terminal) how could I make this a "global" keypress?
2. Howto send hex coded buttons like for example '0xa2' which sends a pause command to gnome/rhythmbox or whatever.

If someone can help me with these 2 things I think this would be a viable btnx alternative, be it a very dirty workaround.
I've already sent an email to the author of xvkbd, so this thread will be a possible solution to future googlers with the same problem.

---

### Post by DLGandalf on 2008-10-01
Ok so I found out xmacroplay is way better to emulate keys and so, should have read more tutorials..

but one question remains, howto send hex keys in xmacroplay

---

