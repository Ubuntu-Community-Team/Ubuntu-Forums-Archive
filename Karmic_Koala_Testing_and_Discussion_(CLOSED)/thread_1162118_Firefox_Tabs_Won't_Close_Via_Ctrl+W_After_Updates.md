---
title: "Firefox Tabs Won't Close Via Ctrl+W After Updates"
date: 2009-05-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tripinva on 2009-05-17
Of all the strange problems I've had while using Alphas, I think this is the strangest.

Ctrl+W no longer works in Firefox after the KDE updates I just installed.  Any other Ctrl key combo that I've tried works, just not Ctrl+W.  It works in any other program I've tried.

I looked on Google and a post on Mozillazine mentioned a possible corrupt file in my profile, so I removed that file and it did not resolve the issue.

I'm stumped at this point, because it points to a problem with Firefox in my mind but I really do not know.

So does anyone have any idea what could be wrong?  I'm really missing my Ctrl+W right about now.

Thanks!

- Trip

---

### Post by fifth on 2009-05-17
No problems here, tbh didnt know about the Ctrl+W shortcut, but good to know. I usually use Ctrl+F4 to close the current tab, but thats not been working from KDE although its fine from Gnome. Never have looked for a reason, but I would guess a shortcut mapping within KDE itself.

What desktop are you using? Could the shortcut be mapped to something else?

---

### Post by tripinva on 2009-05-17
I'm using KDE 4.2.85, freshly updated.  Funny, it doesn't work in Konqueror either, now that I'm testing it.  Perhaps you're right; I'll poke at it a bit and post again if I find something else mapped to Ctrl+W.

- Trip

---

### Post by tripinva on 2009-05-17
Found it.

System Settings > Global Keyboard Shortcuts > khotkeys

Within this, there is an option which says "Remap Ctrl+W to Ctrl+F4 in Qt Designer."  Setting it from Ctrl+W to "None" fixed the issue.

Thanks!

- Trip

---

### Post by brm on 2009-05-17
Thanks for tracking this one down.

BTW, Ctrl-F4 in KDE defaults to "switch to virtual desktop 4" and therefore does not close a tab in Firefox.

The remapping in khotkeys is new in the KDE 4.3 beta and, as such, should be reported as an "undesirable feature," aka a bug.

---

### Post by fifth on 2009-05-17
> **brm said:**
> Thanks for tracking this one down.

BTW, Ctrl-F4 in KDE defaults to "switch to virtual desktop 4" and therefore does not close a tab in Firefox.

The remapping in khotkeys is new in the KDE 4.3 beta and, as such, should be reported as an "undesirable feature," aka a bug.

Was about to post on the Ctrl+F4, had a look in hot keys and found the desktop switch hotkeys Ctrl F1-F4. I've removed the mapping as its not something I use. So got F4 tab closing back in Firefox now :D

Thanks brm.

---

