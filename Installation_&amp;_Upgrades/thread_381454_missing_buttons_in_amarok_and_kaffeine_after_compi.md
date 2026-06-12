---
title: "missing buttons in amarok and kaffeine after compiz removal"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by wxnker on 2007-03-10
**[COLOR="Red"]EDIT RESOLVED[/COLOR]**

Since I upgraded about a week ago/or since I removed compiz. I've been having problems in Kubuntu.

I am missing the ICONS or BUTTONS in several KDE applications like: Amarok, Kate, kaffeine etc.
I can get the ICONS back in most programs, but I have to "right click the toolbars and choose ICON SIZE=small, medium etc". I have to do this everytime I start the programs, because they keep "forgetting" the ICONS. In Amarok there's nothing I can do because I can not right click and get the ICON SIZE option.

___________________________________________________________________________________________________

BUT today I discovered something that I had not noticed.

I was wondering why "Kate" kept loosing the toolbar icons when started normally, but when started in the terminal with "sudo kate" the icons were there.

So I tried "sudo amarok" and then the buttons and icons work perfectly.

I guess I'm getting closer to the solution but I do not understand what's wrong. **Why do the programs need to be opened with ROOT privileges to show ICONS?** :confused:

Can someone please suggest what could be wrong?

---

### Post by wxnker on 2007-03-12
Problem solved.

I did a back up of the /home/user/.kde folder. I then deleted several files in the /.kde/share/config folder. 
I only kept files I knew I needed, like Kmail and Kicker files. I'm not sure which particular files caused the problems, but it works. :D

Did a ctrl+alt+backspace and everything is back to normal.

Now I only need to set the wallpaper, themes and a few other minor settings and all is perfect.

Thanks to "claydoh" from the Kubuntu forum for showing me the solution.

---

