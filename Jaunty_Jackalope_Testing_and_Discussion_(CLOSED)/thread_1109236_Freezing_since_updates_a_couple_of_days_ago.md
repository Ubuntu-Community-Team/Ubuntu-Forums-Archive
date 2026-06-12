---
title: "Freezing since updates a couple of days ago"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by bmarius on 2009-03-28
Hello

I'm having some trouble since updating a couple of days ago.

Whenever X starts the computer freezes. Sometimes with a black screen other times with artifacts: teared version of the splash screen and even a line from the first bios screen one time. I assume that is some screen-buffer that haven't been emptied correctly?

Either way when the freeze happens I can't Ctrl-Alt-F# to get out to a terminal nor exit X in any way (Ctrl-Alt-Backspace/AltGr-PrintScreen-k). The only thing that works is AltGr-PrintScren-reisub.

Ubuntu is Jaunty x86_64 and my graphics card is an ATI Radeon HD3870.

The last line in the Xorg.0.log is
```
(II) Initializing built-in extension DAMAGE
```

I have tried disabling the DAMAGE extension, but despite the xorg-log saying early on that it's disabled it still initializes it. (Because it is something vital? :))

I have tried ati, radeonhd and vesa drivers with same results, so I assume it's not driver related.

I use aptitude for updating, and if I'm not mistaken the breaking updates might have happened during the python happy-fun-time, could that have made any difference?

Are there other log files that might be interesting?

Anyone have an idea what is going on here?

Thanks in advance.

---

### Post by duanedesign on 2009-03-28
I have a similar problem and I have come across a few bug reports you might want to check out to see if they are related to your problem or provide you with any leads.

The freezing on lock up sounds like this one.
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/326344](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/326344)

Your reference to the Damage extension makes me think of this bug.

> "[the cause of the problem] is a race condition between the X server and compiz that's the result of a fundamental design problem in the way the Damage extension works." and "[fixing it] will require more changes to the Damage and GLX extensions, the X server, Compiz, and the NVIDIA X driver." 

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/269904?comments=all](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/269904?comments=all)

these bugs are posted by people using NVIDIA drivers. I noticed you are using ATI. However the second one sounds like a problem between X server and Compiz. Hope this helps.

Does disabling Compiz fix the problem?

---

### Post by bmarius on 2009-03-29
I don't think that issue is related, as my system freezes before X is loaded. As soon as I do startx or let gdm start, the screen freezes and shows artifacts and the whole system locks up.

Compiz haven't been enabled since I started using Jaunty, as the fglrx driver wasn't updated for the new x-server version.

Thanks for the suggestion, though :)

---

