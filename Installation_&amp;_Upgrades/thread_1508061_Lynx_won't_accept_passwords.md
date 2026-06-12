---
title: "Lynx won't accept passwords"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by EoRaptor013 on 2010-06-12
OK, this is just weird. Did a fresh install from the alternate CD, including deleting original Win XP partition. Installation went just fine. Building this for my wife, so when asked for user name and password, entered those for her. As required, entered password, then re-entered for verification. 

When setup completed, I tried to login, but absolutely could not. System recognizes the keyboard, responds to enter key, enters dots in the PW box as I'm typing but only returns Authentication Failed. 

Thinking I must have mistyped the PW both times, I reinstalled. This time, I created _my_ user name and password; the one my hand muscles know so I don't even have to think about it. Get to the end, reboot and, _I can't log in!_

Does anybody have any idea what's going on here? I'd truly love to find out; my wife is getting restless!

Thanks.

Randy

---

### Post by _Mark_ on 2010-06-12
Now don't shout at me I have to ask..... Caps lock?

---

### Post by arrange on 2010-06-12
You might have used a different layout when installing from the Alternate or something like this.

If really at a loss, go to [Terminal](https://help.ubuntu.com/community/GnomeTerminal) and change the password manually```
sudo passwd input_user_name_here
```(it will not ask for the old password)

---

### Post by EoRaptor013 on 2010-06-12
> **_Mark_ said:**
> Now don't shout at me I have to ask..... Caps lock?
Thanks for asking. I've done dumber things, but not this time.

---

### Post by EoRaptor013 on 2010-06-12
> **arrange said:**
> ...
If really at a loss, go to [Terminal](https://help.ubuntu.com/community/GnomeTerminal) and change the password manually```
sudo passwd input_user_name_here
```(it will not ask for the old password)

Um, how do I get to a functional terminal when I can't log into the system? I tried Ctrl-Alt-F3 to get a console, but that also asked me to log in.

---

### Post by EoRaptor013 on 2010-06-12
Har! I just took a flyer, based on arrange's suggestion, rebooted and selected xterm as the session to start. Entered my password, and what do you know, I get an xterm window, properly logged in. But, there were no window borders, no title bars, no nuthin' except the Lynx pinky-purplely, funky wallpaper and the bare xterm window. Interestingly, I can launch GUI apps, like gedit, from the xterm prompt. Like xterm, no decorations whatsoever. Ah ha! says I, it's a metacity problem. 

The machine is an old iDeq, among the earliest of the shuttle style, mini-computers. An embedded Via chip provides the graphics using shared memory (64Mb out of the 2Gb pool). So, I tried two things. First, I ran synaptic, and marked all updates. I also noticed there is a Via driver of some sort (forgot now what it is) so I grabbed that too. Then, just for extra credit, I also installed xUbuntu. Finally, I restarted the whole mess, but selected xUbuntu for the session. Now there is great joy and rejoicing in the land! I haven't tried a Gnome session, will try after the wife catches up on her email. 

In any event. This problem is solved!

Thank you all for your input; I couldn't have done it without you!

Randy

---

