---
title: "Simple problems with Unity"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by 2uRcJQ34G1 on 2011-04-29
Hiya,

I just upgraded to Ubuntu 11.04 from 10.10:guitar:

I have almost all of my settings transferred except:
[LIST=1]
[*]My clock screenlet does not start on startup even though the Start at startup is checked. My other screenlets do open though, its just this one.
[*]My custom mouse cursor only shows up when I am using an application and not say if I am pointing at the Desktop.
[*]I have the 3D cube checked but it is not working! - I need me cube :"(.
[*]If I have a program running, the title bar which is supposed to be showing in the top Unity bar, only shows when I pont at it, is this the default or is something wrong?
[*]Whenever I try to change a setting in the CCSM then the Unity Bar(at the top), goes weird. I have the menu item kind of memorised and they still work if I click on them, but the bar itself has a whole lot of lines and funny graphic stuff on it and I cannot see the icons.
[/LIST]

These are the things that worry me. Any solutions to any of the problem will be much appreciated.

Cheers!:)

---

### Post by 2uRcJQ34G1 on 2011-04-29
I was under the wrong impression that UIs were supposed to make your life easier, this is such a pain! I love my terminal and emacs!!

---

### Post by dino99 on 2011-04-29
> **gore_grinder said:**
> I was under the wrong impression that UIs were supposed to make your life easier, this is such a pain! I love my terminal and emacs!!

As always, the first get the headache, better to wait for fixes a few days/weeks after main release

but you can still read/watch the sticky into "general help" subforum about unity

and this one too:
[http://ubuntuforums.org/showthread.php?t=1741293](http://ubuntuforums.org/showthread.php?t=1741293)

---

### Post by 2uRcJQ34G1 on 2011-04-29
New Revelation: There is a cube, however, it is flat- no depth. If I do Ctrl+Alt+Left then it simply switches to the next workspace and then if I hit those keys again, I end up on the original workspace. This is not right since I have four workspaces in total and I can see them from the workspace switcher from unity panel. I have also enabled the skydome option and it is enabled, however, it does not show.

Cheers!

---

### Post by 2uRcJQ34G1 on 2011-04-29
A brand new problem: If I was to minimize a window, the programs appears not to have run in the first place in the Unity panel. However, I can go Super+tab to switch to it and then everything runs fine again. This only happens sometimes if I do Alt+F9

---

### Post by 2uRcJQ34G1 on 2011-04-29
Update: I have found a zombie process running trying to exit- I am guessing it cannot find a parent. I have tried kill and end process signal with no avail. Process name: zeitgeist_datah

---

### Post by 2uRcJQ34G1 on 2011-04-29
I guess, there is nothing more I can do. I will slowly watch my thread disappear into oblivion. Special thanks to gore_grinder for trying. LOL

---

### Post by 2uRcJQ34G1 on 2011-04-29
[B]A miracle:[\B] If you have any problems with the unity title bar, then check to see if the Workaround option in CCSM is unchecked. If it isn't then try then uncheck it. Solved one of my problems!!

This might also solve problems with the Unity panel. Hope this helps someone!

---

### Post by tsaunders on 2011-04-29
Have you tried not running unity and seeing if the cube works?

Take a look here:

[http://ubuntuforums.org/showthread.php?t=1741293](http://ubuntuforums.org/showthread.php?t=1741293)

---

### Post by MugOTea on 2011-04-29
> **gore_grinder said:**
> [B]A miracle:[\B] If you have any problems with the unity title bar, then check to see if the Workaround option in CCSM is unchecked. If it isn't then try then uncheck it. Solved one of my problems!!

This might also solve problems with the Unity panel. Hope this helps someone!

Lol - I have those problems, and workarounds was checked... so I unchecked it and the unity bar disappeared again! As you mentioned the menus still work but the bar has gone completely. Oh well.

How did you get your screenlets to work? Mine are still in the start up and appear to be running but I cant see any of them?

---

### Post by 2uRcJQ34G1 on 2011-04-29
Yes, I have already tried that, unfortunately, it works in Ubuntu Classic alone. I am trying to run with Unity. On the other hand the mouse pointer should work perfectly unity, but it doesn't :(.

---

### Post by 2uRcJQ34G1 on 2011-04-29
> **MugOTea said:**
> Lol - I have those problems, and workarounds was checked... so I unchecked it and the unity bar disappeared again! As you mentioned the menus still work but the bar has gone completely. Oh well.

How did you get your screenlets to work? Mine are still in the start up and appear to be running but I cant see any of them?

Try this:

- go to quick search(top left corner)
- search for screenlets
- hit re-start all
- check if your screenlets, show up now
- if they do then individually change one setting for each of them and revert back to the original setting(i think this overwrites the original file)
OPTIONAL - if the screenlets do not show up, then launch a new screenlet for all the screenlets that you originally had and then continue with the previous step
- restart computer and see

The screenlet would not sometimes not show up in the previous Ubuntu as well. But I hope this help, I just restarted my computer and everything was exactly in its place. See if that helps!

---

### Post by 2uRcJQ34G1 on 2011-04-29
As for the #4 problem, it IS the default behaviour. Now apart from the cube and my precious mouse pointer, everything is working perfectly!!!

---

### Post by MugOTea on 2011-04-29
> **gore_grinder said:**
> Try this:

- go to quick search(top left corner)
- search for screenlets
- hit re-start all
- check if your screenlets, show up now
- if they do then individually change one setting for each of them and revert back to the original setting(i think this overwrites the original file)
OPTIONAL - if the screenlets do not show up, then launch a new screenlet for all the screenlets that you originally had and then continue with the previous step
- restart computer and see

The screenlet would not sometimes not show up in the previous Ubuntu as well. But I hope this help, I just restarted my computer and everything was exactly in its place. See if that helps!

Yep, that got it - sort of, the ring sensors and other screenlets I was using were gone, but new ones to replace them? I can monitor my CPU temp again and that's the important thing on this crummy laptop.

I think the menus only show up in the top bar when you mouse over is a deliberate thing. Someone else was saying that it's by design that it shows the window title by default. In the beta version there was apparently a bug where the menu overlapped the window title up there and this could have been the solution.

I just wish I could get the window decorations to work in unity then I could probably cope with some of the niggles until the updates are released...

Thanks for your help with the screenlets matey! :)

---

### Post by 2uRcJQ34G1 on 2011-04-29
Glad to help!

---

### Post by gordo_0518 on 2011-04-29
I don't know why but i would loose the top statuse bare and the dash on the left after i would install compiz config manager(advanced) both on an update from 10.10 and 10.04 and on a fresh install formating my drive all i know is I'm not going to install ccsm for now

---

### Post by 2uRcJQ34G1 on 2011-04-29
I had similar problems when I first used CCSM. However, you should get a hang of it once you play with a litte bit. The problem you are describing occurs when you screw up every value in the properties for multiple properties to the extent that they no longer function properly together.

---

### Post by 2uRcJQ34G1 on 2011-04-30
bump^^

---

### Post by libreleaks on 2011-05-06
Not sure if you guys found a way to fix the cube in Unity. Launch a terminal and type gnome-panel

Then, you should be able to right click the panel and "add to panel" the Workspace Switcher at the bottom. Right click the Workspace Switcher and change preferences: columns to 4 and rows to 1. You should have your cube now.

If you have problems in Classic as well, just launch the workspace launcher and do the same :)

---

### Post by 2uRcJQ34G1 on 2011-05-07
> **libreleaks said:**
> Not sure if you guys found a way to fix the cube in Unity. Launch a terminal and type gnome-panel

Then, you should be able to right click the panel and "add to panel" the Workspace Switcher at the bottom. Right click the Workspace Switcher and change preferences: columns to 4 and rows to 1. You should have your cube now.

If you have problems in Classic as well, just launch the workspace launcher and do the same :)

:KS**Thanks a million!** This worked like a charm. I now have my cube back!:KS

---

