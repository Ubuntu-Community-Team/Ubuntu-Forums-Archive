---
title: "Trying to fix  Gutsy freeze on nvidia and firefox"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by Weyoun on 2007-11-05
What the hell is wrong with gutsy. Constant sudden freezes. probably Firefox and nvidia drivers.
I played GTA San Andreas on feisty perfect, now I can not play it more than, lets say 40 minutes, because of system freeze. 
streaming videos and ''movement'' stuff on the web with firefox just freeze the whole system.  All I can do is restart on the button, and I didn't have to do that since using Windows!
I really think gutsy came too early.
And also gutsy don't have visual volume control, the on screen slide bar when changing volume on the keyboard. 
I am using Kubuntu and I know its not good as gnome gutsy but these stuff worked on feisty so  what is wrong with 7.10.
Come on, I am open for any kind of experimentation. Lets try ANYTHING!
THANKS A LOT!

---

### Post by Weyoun on 2007-11-06
Its definitely nvidia and firefox. I think on forcing the card, like playing games, system freezes. Also using the firefox has to do something with drivers that freezes the system even faster.

---

### Post by bulldog on 2007-11-06
> **Weyoun said:**
> Its definitely nvidia and firefox. I think on forcing the card, like playing games, system freezes. Also using the firefox has to do something with drivers that freezes the system even faster.

Well I have a nVidia 8800GTS 640MB and  Gutsy and I run firefox and I have to say there's nothing wrong with it.
So it can be anything in your system what makes the difference,but this isn't helping very much I'm afraid :(

---

### Post by PmDematagoda on 2007-11-06
I cannot offer much help but I can tell you a better way of restarting Ubuntu when it freezes, just press Alt+Print Screen(Hold the two together through the sequence) and then RSEIUB in that order. This will make sure that all the drives are unmounted before it does the restarts which means you have a lesser chance of corrupting your hard drives.

And the nvidia driver is not the reason you are having those freezes, if it was then you most probably cannot use the GUI using the driver at all.

---

### Post by timcredible on 2007-11-06
i have an old nvidia mx4000 card, works fine, compiz works fine, videos, firefox, flash, etc.  i'm assuming you're running gta in wine?  maybe try not running wine and see if you have the problems with firefox.

---

### Post by Weyoun on 2007-11-06
Thanks people! I hope we'll think of something eventually because I see many people have those problems. They are really pain. 
Thanks again!

---

### Post by gabba on 2007-11-08
> **Weyoun said:**
> What the hell is wrong with gutsy. Constant sudden freezes. probably Firefox and nvidia drivers.
I played GTA San Andreas on feisty perfect, now I can not play it more than, lets say 40 minutes, because of system freeze. 
streaming videos and ''movement'' stuff on the web with firefox just freeze the whole system.  All I can do is restart on the button, and I didn't have to do that since using Windows!
I really think gutsy came too early.
And also gutsy don't have visual volume control, the on screen slide bar when changing volume on the keyboard. 
I am using Kubuntu and I know its not good as gnome gutsy but these stuff worked on feisty so  what is wrong with 7.10.
Come on, I am open for any kind of experimentation. Lets try ANYTHING!
THANKS A LOT!

I have the **absolute**, **exact same** problem. With stock Ubuntu, not Kubuntu. I recently upgraded to Gutsy. Pentium IV 2.4GHz, Nvidia 7800 GS here.
Gutsy freezes after some time after doing the following for a while:
- using Firefox
- using Compiz (Desktop effects)
- playing an OpenGL game (this was actually a windows OpenGL game under wine)

It is a *_complete kernel freeze_*, not just a Xorg freeze, because even the Alt+SysRq keys don't work (I tested them before to make sure I know how to use them).

I didn't have that problem under feisty with Firefox and OpenGL games; I didn't use compiz.

Did anyone submit a bug report about this? I searched the bugs recently but couldn't find exactly this one (others had just Xorg freezing, that's another story).

---

### Post by pekka72 on 2007-11-10
Same here. I have an old Toshiba Satellite 5100. More and more often it would start flickering and then freeze completely. The only thing I can do is switch off. Outch! Now it's after 1 minute that I start having troubles. 
It's not an X problem. I can see the flickering in terminal mode if I use less for instance. But it doesn't freeze then. I am really stuck. None of the files in /var/logs gets any message when the flickering occurs. Can I downgrade the nvidia driver to the feisty version? (Maybe that's a stupid question, I actually didn't check if it has been upgraded at all...)

---

### Post by pekka72 on 2007-11-10
... found other threads suggesting to remove nvidia-glx-new. Will try.

---

### Post by chorca on 2007-11-10
I'm having this same problem, but i'm on ATI. I have a Radeon X800XT with the 'ati' driver. Everything works fine, but i have random freezes. This is what i've noticed:

[LIST]
[*]Freezes usually occur with FireFox using Flash, or with RhythmBox
[*]During the freeze, all keys cease functioning. No key combinations will work, the mouse may or may not still be functional.
[*]This is not a kernel freeze. I installed the OpenSSH server, and i'm able to remain SSHed into the box when it's frozen, executing programs and getting normal responsiveness.
[*]It does not seem to be audio-driver related, as i switched from onboard (sigmatel audio) to an Audigy and disabled the onboard, and am still having the issue
[*]It appears to not be only with audio, as i have had no issues playing hour long 720p videos with VideoLAN, without fail.
[/LIST]

I'm not sure what to try next. I looked around for threads and while there's a ton of posts in the x86-64 forum there, i'm not sure that our problems are that different. Usually the issue occurs when clicking a box or opening something. I'm going to disable desktop effects and see if it shows any difference.
Since my box remains responsive to SSH, is there any thing someone can have me do to help determine the cause? Syslogs and all other logs appear to show no signs of errors. I'm going to try and kill off GDM and X to see if i can bring the X back, but failing that, i'd like to try to find out what's going on here.

*****UPDATE*****
I ran top on SSH, it shows Xorg going to 100% CPU and staying there. This is most likely why only the desktop is locking up.
I am unable to kill the Xorg process. I have tried multiple kill commands, kill -9 and top's kill, the process remains at 100% CPU.

---

### Post by Weyoun on 2007-11-11
I think I fixed it!
Remove in adept/synaptic manager all nvidia stuff. Download drivers from the nvidia site. Ctrl+alt+F2, then  login (if needed). Stop KDM (kubuntu) or GDM (ubuntu) ''sudo /etc/init.d/kdm stop'' (for ubuntu gdm instead of kdm), and now sudo sh /location of download folder/NVIDIA-Linux-x86-100.14.09-pkg1.run (or if not like this just remember the exact name of the file you've downloaded, it is case sensitive). Follow the instructions and when finished ''sudo /etc/init.d/kdm start'' (for ubuntu gdm instead of kdm). 
Works for me, hope will for you too!!!:popcorn:

---

### Post by DFinley on 2007-11-23
I experience the Gutsy/Firefox freeze almost daily. I also use the special desktop settings and a new Nvidia card. Does the black, white. and brown striped rectangle on the frozen screen tell anyone anything?

---

