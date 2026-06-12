---
title: "unity dash search window unresponsive"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by rtimai on 2011-06-19
In the Unity desktop pressing the Super/Win key or clicking on the Unbuntu logo at the top-left corner of the screen opens the Dash, where you search for applications that are not graphically listed. Starting today, I can no longer enter any text in the Unity Dash search dialog window, effectively disabling a quick search.

I have seen a bug report for this 

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/769279](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/769279)

but it's listed as low priority. Now I am trying to give Unity an honest effort to adapt to it, and I don't think this broken feature is a low priority, since it's one of the immediate methods for locating tools that are not displayed. I would prefer to see full menus by default, and not have my selection dumbed-down or pretty-fied for me. A broken search makes Unity even harder to adjust to.

Is anyone else having this symptom or know a fix? Don't suggest alternate ways to find my tools. I know what they are. The Dash quick search is supposed to be the "convenient" method. Yeah, and I know I can always revert to "Unbuntu Classic." But that will go away with Oneiric, so I'm trying to get used to Unity.

---

### Post by Larkspur on 2011-06-19
Does the run window (Alt+F2) work? Try opening that and typing "gnome-panel". If it works, you get the old panel back with the old menu as a temporary workaround, and you can add a symptom to the Bug thread.  

As far as a solution, I have none.  Hopefully someone else will.  Meanwhile, if you don't mind losing any custom Compiz settings, try "compiz --reset" and see if that helps.

---

### Post by rtimai on 2011-06-19
Larkspur,

Thanks for the suggestion. This is weird. The Alt-F2 Run Command dialog now seems to be functioning as a search window. I started entering, "find..." and launchers began to appear beneath the dialog. That's not what I remember the Alt-F2 window behavior to be (not sure.) The Unity "Run Command" tool is not the same as the old Run dialog, I remember now...

Did you mean try "unity --reset" ? I think compiz accepts the --replace command. The reset appeared to freeze, where I killed it. Should I have waited several minutes? 

rtimai@rtimai-HP-dv6-3012he:~$ unity --reset &
[1] 4118
rtimai@rtimai-HP-dv6-3012he:~$ Traceback (most recent call last):
  File "/usr/bin/unity", line 198, in <module>
    reset_unity_compiz_profile ()
  File "/usr/bin/unity", line 83, in reset_unity_compiz_profile
    if current_profile_gconfvalue.get_string() == 'unity':
AttributeError: 'str' object has no attribute 'get_string'
^C
[1]+  Exit 1                  unity --reset
rtimai@rtimai-HP-dv6-3012he:~$

---

### Post by rtimai on 2011-06-19
Just opened Ctrl-Alt-T Terminal and ran "compiz --replace &" and the screen reset with windows missing all the controls, including the top panel, and the launcher side bar gone. Had to Ctrl-Alt-Bkspc (restarts Xorg?)

Well. THAT was a bust. Do I have some kind of underlying config problem, I wonder? Yes, I upgraded, not a clean install.

---

### Post by rtimai on 2011-06-19
After restarting I was able to enter text in the Dash search box. Don't know what caused the earlier failure, but it seems to be working now after restarting.

---

### Post by Larkspur on 2011-06-19
> **rtimai said:**
> Yes, I upgraded, not a clean install.

That might be the culprit.  A lot of people are having trouble with upgrades, as you've no doubt seen.  If you still can, open a guest session and see if the dash works in that.  If so, we'll be a bit further along.

In answer to your question, yes, I did mean "compiz --reset": it works like "compiz --replace", but instead of simply restarting, it restores the default settings.  I thought that maybe one of your compiz settings had caused some conflict that led to this dash problem.  Did you use ccsm much in your previous install?

EDIT: Glad you got it sorted out!

---

### Post by rtimai on 2011-06-21
Larkspur,

Not only is my scenario an upgrade, but I installed Gnome 3, then discovered that it overwrote some critical settings in the Unity configuration. I had the missing taskbar and launcher syndrome. Removing Gnome 3 didn't reverse the symptoms. But, happily, all that gradually got fixed by the incremental updates that followed in the weeks after.

I THINK my only remaining issues have to do with Compiz (or Unity, however you want to look at it) becoming unresponsive when I attempt to reset/replace it, as I described above. Also, when I run Compizconfig Settings Manager the top panel often gets corrupted. Actually, the buttons are all still there, and I can "feel around" for them by right-clicking usually, and reboot. BTW I don't like simply restarting the display manager (Alt-Ctrl-Bksp) any more because it moves the display to tty8 (and increments to the next tty on each restart.)

---

### Post by rtimai on 2011-06-21
Larkspur,

Wanted to finish answering your questions. I only used CCSM after upgrading to 11.04. I only ran Metacity before that. Also, I ran a guest session, and Dash search works normally. As for "compiz --restart" I'm a little hesitant to run it, since everything appears to be working. Ah, but could be, eventually curiosity will get the better of me...

---

