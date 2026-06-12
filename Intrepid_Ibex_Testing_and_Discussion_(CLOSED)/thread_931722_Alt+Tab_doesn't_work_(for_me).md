---
title: "Alt+Tab doesn't work (for me)"
date: 2008-09-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by forumache on 2008-09-27
Hi,

I'm on Intrepid, all updated. Alt+Tab doesn't work for me. I'm running in default mode, no Desktop Effects active. When I press alt+Tab I get only tab (sometimes) and other times it is ignored.

Could you please check on your computer and post back? Maybe I'm the only one...

Thanks.

---

### Post by psyke83 on 2008-09-27
From: [http://www.ubuntu.com/testing/intrepid/alpha6](http://www.ubuntu.com/testing/intrepid/alpha6)

> After upgrading to this version, some keys might misbehave in X. Please make sure you have set the keyboard model as Generic Evdev-managed keyboard in System &#8594; Preferences &#8594; Keyboard, in the tab Layouts. If some keys still have problems, please file a bug against xkeyboard-config, and provide the output of setxkbmap -print and xkbcomp :0 - both run in the Terminal. 

---

### Post by forumache on 2008-09-28
Thanks psyke83,

I originally believed that keyboard is the problem, but now I see that when Desktop Effects are active Alt+Tab works without problems, whatever switcher I select.

So I guess the problem is with the Gnome/Metacity application switcher...

I'll test more and come back with a bug report...

---

