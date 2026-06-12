---
title: "SOLVED Recent update has changed Alt-F2 when you drop to command line"
date: 2021-06-19
forum: Installation &amp; Upgrades
---

### Post by david503 on 2021-06-19
Ubuntu 18.04.5

When my session froze I press ctr-alt-F3 to drop out of shell into raw CLI.  (I know you can do other F's I just use F3 for whatever reason).

And then I would "sudo killall chrome" and then Alt-F2 to come back to gnome.  

But that's changed recently.  If I alt-f2  now it  just switches to a different terminal.  (As if I had  done ctrl-alt-f2.)

How do I get back to gnome now?

(And I'm curious about the logic of changing this.) 

thanks

---

### Post by TheFu on 2021-06-19
Usually, there are multiple pseudo-ttys.  F1-F10.  Try them all.  F7 is historically the "GUI" session.
BTW, it is possible that Wayland changes this, so I don't know what happens in that situation.

Also, there are multiple programs that could be in the process table with "chrome" in the name, not just google-chrome, so I would encourage you to get the exact name of the program and kill that.  I won't install google software on my systems, so cannot check for the exact name.

---

### Post by MAFoElffen on 2021-06-19
The reason... TTY7 "used" to be where the Linux Graphics Layer came up (consistently) and lived, no matter which which branch of Linux, or which flavor (Distro). That was true up to through the time of Ubuntu 17.04. 

The Virtual Terminal Sessions (TTY) are in the layer below the stack of a graphical Desktop Manager and Graphical Desktop. Linux has 7 default TTY virtual sessions on top of it's console. You can increase the number of TTY sessions to 63 in Linux Kernel. I don't think you need to know the when and why of TTY's, because that came from UNIX times, previous to Linux, so skipping back...

Somewhere in time (upstream changes in kernel), between Ubuntu versions 17.04 and 17.10, that changed Linux-wide to start the graphical layer in whichever was the first available virtual terminal (TTY) session. That is just how is has been since then.

So no, this was not a recent change. That change happened 4 years ago, and since, an X session, or any other form of graphics session, is not locked to a "specific" TTY virtual session. It now goes to whatever session was available, when the graphics layer came up. Which since 4 years ago, now can be somewhat random.

The reason it now usually comes up in TTY2, is that TTY1 is usually displaying console messages when the graphics layer boots...

---

### Post by TheFu on 2021-06-19
All I know is <c>-<a>-F7 gets me to the GUI on this 18.04 system. All the others end up on consoles.  
The same happens on a 20.04 install here. It was a fresh install, not an upgrade.  c-a-F7.

I do remember at least 1 system where the GUI seemed to be on F1. May have been 17.10 when Canonical pushed Wayland too hard.  Wayland still breaks many of my workflows, so I've been ensuring Wayland doesn't get used as soon as that breakage happens.

I don't use Gnome3 or the login manager it installs.  Could that be the difference?

---

### Post by tea for one on 2021-06-19
Just to add some more confusion, here are the results using Ubuntu 20.04 & gdm3 Display Manager

Ctrl Alt F1 > Login Page
Ctrl Alt F2 > GUI Desktop
Ctrl Alt F3 > TTY3
Ctrl Alt F4 > TTY4
Ctrl Alt F5 > TTY5
Ctrl Alt F6 > TTY6

Alt F2 > Run a Command (Esc to close)

---

### Post by MAFoElffen on 2021-06-19
@TheFu - I'll PM you so we don't muddy this up here. LOL

---

### Post by david503 on 2021-06-21
@MAFoElffen  Well I mean it *is* a change when all of a sudden I can't get back to the GUI oh no.  But I know what you mean. In the broader sense... 

Thanks to all of you I'll follow up here next time I crash and tell if your suggestion(s) worked.

---

### Post by MAFoElffen on 2021-06-21
LOL. Yup.

FYI: Just remember that when all else fails graphics wise, the DM (Graphical Logon Manager) starts, and has hooks into the next layer to the DE (Desktop Environment) so If you ever have to Kill X, go to a free TTY and kill the DM itself (by the process ID). Everything in the Graphics Layer will unload. That will drop everything to the TTY virtual sessions, 1 through 7, without any Graphics Layer at all.

Then restart the DM and DE via startx.

Just another way, if disaster strikes, or you need to run something where X can't be loaded during what you need to do... That is also a good way to debug and fix things in the graphics layer without having to reboot.

---

### Post by david503 on 2021-06-29
> **MAFoElffen said:**
> The reason... TTY7 "used" to be where the Linux Graphics Layer came up (consistently) and lived, no matter which which branch of Linux, or which flavor (Distro). That was true up to through the time of Ubuntu 17.04. 
....
Somewhere in time (upstream changes in kernel), between Ubuntu versions 17.04 and 17.10, that changed Linux-wide to start the graphical layer in whichever was the first available virtual terminal (TTY) session. That is just how is has been since then.

So no, this was not a recent change. That change happened 4 years ago, and since, an X session, or any other form of graphics session, is not locked to a "specific" TTY virtual session. It now goes to whatever session was available, when the graphics layer came up. Which since 4 years ago, now can be somewhat random..

I have 18.04, MAFoElffen.

$ lsb_release -aNo LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.5 LTS
Release:    18.04
Codename:    bionic


Alt-F7 worked up until about last month or so.  So yes, this is a recent change.

> **MAFoElffen said:**
> LOL. Yup.

FYI: Just remember that when all else fails graphics wise, the DM (Graphical Logon Manager) starts, and has hooks into the next layer to the DE (Desktop Environment) so If you ever have to Kill X, go to a free TTY and kill the DM itself (by the process ID). Everything in the Graphics Layer will unload. That will drop everything to the TTY virtual sessions, 1 through 7, without any Graphics Layer at all.

Then restart the DM and DE via startx.

Just another way, if disaster strikes, or you need to run something where X can't be loaded during what you need to do... That is also a good way to debug and fix things in the graphics layer without having to reboot.

Yea I'm not trying to avoid rebooting, I want to get back to my session with chrome dead but everything else still there.

---

### Post by david503 on 2021-06-29
> **tea for one said:**
> Just to add some more confusion, here are the results using Ubuntu 20.04 & gdm3 Display Manager

Ctrl Alt F1 > Login Page
Ctrl Alt F2 > GUI Desktop
Ctrl Alt F3 > TTY3
Ctrl Alt F4 > TTY4
Ctrl Alt F5 > TTY5
Ctrl Alt F6 > TTY6

Alt F2 > Run a Command (Esc to close)

Yea this is totally different in 18.04. Interesting. 

Anyway update for anyone with my problem, yesterday I froze and dropped out of shell to terminal and crtl alt f2 didn't get me back to GUI. Thanks nonetheless.  Interesting how different 20.04 is than 18.04.

---

### Post by MAFoElffen on 2021-06-29
Look in /etc/default/grub... in the GRUB_CMDLINE_LINUX DEFAULT line, if you add "vt.handoff=7" to the kernel boot options (updating grub to pick that change up)... That will pin the graphics session back to TTY7. Not normal now, but if you want it back there...

---

### Post by tea for one on 2021-06-30
@david503 - I was looking on the internet to try and help and I came across your previous thread, now closed.

[https://ubuntuforums.org/showthread.php?t=2434205](https://ubuntuforums.org/showthread.php?t=2434205)

Has this been going on for 18 months?

---

### Post by david503 on 2021-06-30
> **tea for one said:**
> @david503 - I was looking on the internet to try and help and I came across your previous thread, now closed.

[https://ubuntuforums.org/showthread.php?t=2434205](https://ubuntuforums.org/showthread.php?t=2434205)

Has this been going on for 18 months?

No no that's where I learned Alt-F7, which used to work until this month.

---

### Post by david503 on 2021-06-30
OK update, I just froze and did the following:

Ctrl-alt-F3 to get to terminal,
then logged in,
then killed chrome,
then tried Alt-F7 again just to make sure I'm not crazy that it no longer works. Does nothing.
Then tried Ctrl-alt-F2 as suggested above. No dice. I guess that's a ubuntu 20.x thing.
I tried all the function keys, none of them got me back.
I tried Ctrl-alt-F4 and it has the same (correct) predictable behavior of opening a new terminal (and then I can ctrl-alt-F3 to get back where I was as expected).

This doesn't seem like a complicated problem.  How do I get back into gnome. Not a new session; not startx. No, gnome is still running.  Again I've don't this a million times, it's possible, it's just that the key combination changed.

---

### Post by tea for one on 2021-06-30
Using Ubuntu 20.04 with Gnome 3.36.9

Ctrl Alt F3 opens tty3
Alt F2 returns to logged in user's desktop.

This is the same as reported for 18.04 here [https://askubuntu.com/questions/1033206/switch-to-console-in-ubuntu-18-04-how-to-leave-gui](https://askubuntu.com/questions/1033206/switch-to-console-in-ubuntu-18-04-how-to-leave-gui)

If it doesn't work for you, then it begs the question:-

Have you changed anything in Keyboard layout?
Or added extensions, which may affect the key combination?
Non-functioning Alt key?

Out of curiosity, why not boot up a live session of 18.04 and test?
Or set up a new user?

---

### Post by david503 on 2021-07-01
Woo! Yes that has the answer: 
Alt-F1.
That url that @tea for one provided also says Alt-F2 will work but I didn't try it yet.  [https://askubuntu.com/a/1053220](https://askubuntu.com/a/1053220)

I knew this was something simple; they just changed it from F7 to F1 (well or potentially F2) 

thanks, I'll add SOLVED in the title. 
d

---

### Post by tea for one on 2021-07-01
That's good news.

Thread tools has the option to mark as solved.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by david503 on 2021-07-01
Oh thanks. Yea I get my tech forums confused, one of them just says I should change the title. 

thanks again

---

