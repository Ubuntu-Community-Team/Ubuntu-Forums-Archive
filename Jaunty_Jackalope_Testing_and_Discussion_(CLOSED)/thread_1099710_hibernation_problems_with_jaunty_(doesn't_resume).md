---
title: "hibernation problems with jaunty (doesn't resume)"
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Cimi86 on 2009-03-18
Resume only works if I add resume=/dev/sdXY to the kernel line in menu.lst
Please help!
[https://bugs.launchpad.net/bugs/332365](https://bugs.launchpad.net/bugs/332365)

---

### Post by Rocket2DMn on 2009-03-18
Moved to Jaunty Jackalope Testing and Discussion.

---

### Post by mtbsoft on 2009-03-18
It's a bug... in **alpha** software... and will be addressed in good time.  

You need to learn some patience because bumping it in launchpad will just annoy people.

---

### Post by Rocket2DMn on 2009-03-18
I didn't look at the bug until just now.  Definitely **do not** bump bug reports, that is highly inappropriate and will get you no love there - it's not like the forums.

FYI, in my signature there is a link about how to file bug reports, which should help get you started with properly working with bugs.

---

### Post by mariner09 on 2009-03-18
I've always added a resume append in menus.list for hibernation.  Is this no longer needed?

---

### Post by odysseusjak on 2009-03-20
Mine works perfectly.  Finally.  8.04, 8.10 power settings didn't work.  9.04, though, works perfectly.  So, if it 'get's fixed', I hope it doesn't break my system.

---

### Post by mariner09 on 2009-03-22
The problem with suspend/hibernate on my system is that it appears the script /usr/lib/pm-utils/sleep.d/01PulseAudio keeps hanging the process.  It always exits with a return code = 1.  Then the process goes back to a resume state.

---

