---
title: "Keyboard layout chosen at installation not applied to ttys"
date: 2010-03-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by QwUo173Hy on 2010-03-05
A bug (which I'll report) left me unable to log back in from my locked screen.

I switched to a TTY so I could bring the system down gently but couldn't log in there because the TTYs use QWERTY, despite me choosing Dvorak at install-time. I use the Dvorak layout and my keyboard reflects that - so in the absence of another computer, I had to grab a QWERTY touch typist and get her to issue the commands for me.

Is Ubiquity the correct package to file this against?

---

### Post by zombiepig on 2010-03-05
It could be related to this bug I just filed:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/530430](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/530430)

The "Apply System Wide" button in keyboard preferences is broken at the moment. Maybe Ubiquity uses the same broken process for setting the keyboard layout?

---

### Post by QwUo173Hy on 2010-03-05
I *think* the TTYs are outside of the scope of Gnome. In which case responsibility would lie elsewhere. But I'll link to your bug in my report when I make it. Feel free to do the same! (and thank you)

---

### Post by zombiepig on 2010-03-05
Yeah - what I mean is my hunch is that both ubiquity and gnome-keyboard-preferences use the same broken code to set the keyboard layout for the whole desktop. Normally, I can set my keyboard layout in gnome-keyboard-preferences, then hit the "apply system wide" button, and have that layout apply to every program, ttys, etc. 

If you post your bug report here, I'll also confirm that, since I ran into the same problem with the installation not applying my latin-american keyboard layout properly.

---

### Post by QwUo173Hy on 2010-03-05
Oh right, now I get you. I reported it here. 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/533047](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/533047)
It would be great if this was sorted for the final release.

---

