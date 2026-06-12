---
title: "Console/TTY Keyboard Layout Wrong"
date: 2010-03-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by cyberkilla on 2010-03-05
Hello,

Just recently, I noticed that the keyboard layout in my TTYs is not correct. The "\" is shown as "<" for one.

I tried "env" to see if there was some sort of environment variable set, but I can't see any obvious ones. In GNOME Terminal (which works fine), "env" has a few keyboard layout related variables, most of them set to "gb". Heck, I don't even know if there has to be an environment variable set - it's just all I have to go on;)

My keyboard layout in GNOME: Generic 105 key, Qwerty, United Kingdom.

Is this something widespread or related to my own actions (though I don't recall changing anything)?

---

### Post by MacUntu on 2010-03-05
I'm seeing the same, let's see if there's alread a bug reported at Launchpad.

Well, there's this: [https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/524439](https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/524439)

---

### Post by cyberkilla on 2010-03-05
> **MacUntu said:**
> I'm seeing the same, let's see if there's alread a bug reported at Launchpad.

Well, there's this: [https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/524439](https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/524439)

Thanks a lot. I'm clearly not very good at searching for bug reports;)

---

### Post by VMC on 2010-03-05
Its okay for US keyboard. I guess its just UK that's effected.

---

### Post by cyberkilla on 2010-03-05
> **VMC said:**
> Its okay for US keyboard. I guess its just UK that's effected.

That's because it /defaults/ to the US keyboard layout. Everyone else is screwed ATM, but a fix is in the works so I don't mind.

---

### Post by timosha on 2010-03-06
> **VMC said:**
> Its okay for US keyboard. I guess its just UK that's effected.

And the German, French, Italian, Belgian, etc... etc... etc...

---

### Post by CylnZ on 2010-03-07
Well, USA dvorak is also screwed.

---

### Post by QwUo173Hy on 2010-03-13
Fixed in the updates!

---

### Post by cyberkilla on 2010-03-14
Looks like it. Thanks:-)

---

### Post by CylnZ on 2010-03-14
Which updates? I have the same layout issue that's annoying as heck when I try to reinstall my nvidia drivers instead of using nouveau.

---

### Post by MacUntu on 2010-03-14
> **CylnZ said:**
> Which updates?

Package console-setup, version 1.34ubuntu11.

---

### Post by CylnZ on 2010-03-14
Thanks :) Got it, updated, and reinstalled my video drivers in a snap. So much easier to do when what you type is what you intend. :)

---

