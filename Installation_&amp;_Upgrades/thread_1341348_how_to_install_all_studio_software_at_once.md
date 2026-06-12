---
title: "how to install all studio software at once?"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by dabarnyarddawg on 2009-11-29
the answer to this question should be obvious, but clearly i'm missing something.

when installing ubuntu studio for the first time, when the additional software installer page comes up, how do i choose to install all four software suites (graphics, audio, audio plug-ins, and video)?  The first time doing it, I started at the top of the list and chose the 2d/3d graphics option, thinking the installer would return to this screen after installing the graphics software.  it did not, though, and i was never given the option to install the other three software suites.  how do i do this, short of downloading each individual program from the linux software repository?

again, hoping this is a really simple answer.  thanks for the help.

---

### Post by audiomick on 2009-11-29
Hi.
I made the same mistake. You have to select them all before you continue, if I remember rightly.

edit:
Now that I think about it, I think, but I am not sure, that you can load the various modules as meta packages via synaptic.
I will have a look, and do another edit on this post.

2nd. edit
If you open synaptic package manager from system> administration and use the fast search function. It might be called something slightly different, mine is in German, and is called "Schnellsuche", which means fast search. It is the text window in the task bar, not the icon for the search function.
Type in
```
ubuntustudio
```

I get a list of stuff including "ubuntustudio-audio", "ubuntustudio-video" and "ubuntustudio-graphics". I think that is what you need to install what you missed out on.

Michael

---

### Post by dabarnyarddawg on 2009-11-29
That worked.

Thanks!

---

### Post by audiomick on 2009-11-29
Great. Have fun with it.
Put a  solved tag on the thread, wont you? It's in the thread tools at the top of the thread.

---

