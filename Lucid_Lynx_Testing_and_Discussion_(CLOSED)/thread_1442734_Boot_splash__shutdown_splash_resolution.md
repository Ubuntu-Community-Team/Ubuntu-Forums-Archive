---
title: "Boot splash / shutdown splash resolution"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by _simon_ on 2010-03-30
Since installing the unrestricted nvidia drivers the resolution for the boot and shutdown splash has completely messed up. I can't find anywhere to check/change what resolution it's using.

Is this just an outstanding bug or can someone tell me where I should be looking?

---

### Post by FreakTech on 2010-03-30
I am having the same issue.

---

### Post by linux4me on 2010-03-30
> **_simon_ said:**
> Since installing the unrestricted nvidia drivers the resolution for the boot and shutdown splash has completely messed up. I can't find anywhere to check/change what resolution it's using.

Is this just an outstanding bug or can someone tell me where I should be looking?
Do you mean the *restricted* nvidia driver? If so, it's not really a bug, more the development of the new splash screen not being set up yet for the restricted driver. It has changed for me since the last updates, and from what I've read, it's a matter of being patient while the developers first address the new splash with the unrestricted nvidia driver first, then get to the restricted driver.

There's [a thread here]("http://ubuntuforums.org/showthread.php?t=1416872") regarding the issue that may address your questions regardless of whether you're using the restricted nvidia driver or not.

---

### Post by keybuk on 2010-03-30
With the nouveau driver (the one installed by default), the resolution should match that your panel claims to prefer.

With the restricted nvidia-glx driver, the resolution will be 640x480 in 16 colours.

---

