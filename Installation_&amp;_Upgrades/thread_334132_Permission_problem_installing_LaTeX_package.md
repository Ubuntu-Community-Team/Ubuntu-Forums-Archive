---
title: "Permission problem installing LaTeX package"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by LJM on 2007-01-08
I'm trying to install the calrsfs.sty calligraphy package for LaTeX. The problem is that, although I have superuser priviledges (I'm the main and only Ubuntu user), the machine doesn't let me extract the files in the right folder, namely, /usr/local/share/texfm-texlive/tex/latex. If I try using the command line, it won't even show me (using ls -a) all the existing folders past /usr/local/share (only fonts, games, and a few others); if I try using the Gnome interface and get to the latex folder, it won't let me paste any files in there due to "lack of permission."

Does this make any sense? Thank you in advance. --LJM

---

### Post by lhtown on 2007-01-09
I am not sure I understand the problem. However, it sounds like you could start the Gnome file manager, Nautilus, by opening a terminal window and typing 'sudo nautilus' and then entering your password.

BE VERY CAREFUL. The Nautilus window this opens now has superuser powers (until you close it). You now have power to mess up anything and everything!

You should be able to navigate to the location where you want the file and paste it in.

If this doesn't work, try copying the steps you are following in the terminal window and paste them into your next post so we can see what is going on.

---

### Post by LJM on 2007-01-10
Thank you for your reply. Last night, before I had had a chance to read your answer, I solved the problem using brute force--like killing a fly with a cannon. 

I installed texlive-full, which is incredibly bulky, took quite some time, and probably gave me packages I'll never ever need, but now all packages I need seem to be there, including calrsfs.sty.

Thank you anyway for your advice. I'll wrote it down for trying out for possible similar problems in the future.

LJM

---

