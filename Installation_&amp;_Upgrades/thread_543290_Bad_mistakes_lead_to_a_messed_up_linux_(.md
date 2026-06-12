---
title: "Bad mistakes lead to a messed up linux :("
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by blithen on 2007-09-04
So I was having some problems with GNOME, and I decided to say screw it, removed/and installed it again.
Now it removed some things that it didn't reinstall. 
And programs are failing.
So my actual question is, is there a command to reinstall ubuntu. Without formatting.
Like
sudo apt-get install ubuntufiesty-desktop7.04
or something?

---

### Post by qalimas on 2007-09-04
The package name is ubuntu-desktop ;)

---

### Post by blithen on 2007-09-04
Nice! Thanks a lot! didn't think it was that simple :P

---

### Post by southernman on 2007-09-05
As I've seen in a signature here (forget who) and floating around on the internet...

*The nice thing about Linux... If you break it, you get to keep both pieces*

---

### Post by isaacj87 on 2007-09-05
When I was first beginning (I'm still a newbie, I just have a better grip on Linux now) I was reinstalling left and right. It would be nice to make Ubuntu/Linux a little bit more bulletproof. In fact I saw plans to make X more bulletproof in Gutsy. I'm not sure what or how they're going to do it. Or even if the devs are working on anything at all. But it definitely piqued my interest.

---

### Post by koenn on 2007-09-05
Ubuntu/Linux a little bit more bulletproof ?
What you mean ? Either your a user, and the only harm you can do is to your own files, either you sudo, give your password, become root, and have the power to configure (or possibly mess up) the system. So unless you want to wrap "are you sure ?" "really sure ?" "very very sure ?" dialogs around everything related to system administration(and you'll still just click yes), I don't see what's there to bulletproof. 

The X thing is different. X fails if it can't produce the requested resolution.refresh rate, so it's all or nothing : a GUI, or no GUI at all. The "buullet-proofing" of X is to create an "always work fail safe" eg falling back to a conservative 640x480 resolution - not fun to work with, but at least some drag&drop environment for users who can't handle  CLI to fix corg.conf.

---

### Post by isaacj87 on 2007-09-05
> **koenn said:**
> Ubuntu/Linux a little bit more bulletproof ?
What you mean ? Either your a user, and the only harm you can do is to your own files, either you sudo, give your password, become root, and have the power to configure (or possibly mess up) the system. So unless you want to wrap "are you sure ?" "really sure ?" "very very sure ?" dialogs around everything related to system administration(and you'll still just click yes), I don't see what's there to bulletproof. 

The X thing is different. X fails if it can't produce the requested resolution.refresh rate, so it's all or nothing : a GUI, or no GUI at all. The "buullet-proofing" of X is to create an "always work fail safe" eg falling back to a conservative 640x480 resolution - not fun to work with, but at least some drag&drop environment for users who can't handle  CLI to fix corg.conf.

I was mostly referring to X. It seems most new comers have some sort of display issues, whether it resolution or improper drivers. And more than likely, people will advise modifying xorg.conf. Which can lead to problems, that are fixable, but may not seem so to a new user.

---

