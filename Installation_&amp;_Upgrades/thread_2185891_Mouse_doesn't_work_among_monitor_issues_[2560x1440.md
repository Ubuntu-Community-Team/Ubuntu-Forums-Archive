---
title: "Mouse doesn't work among monitor issues [2560x1440]"
date: 2013-11-04
forum: Installation &amp; Upgrades
---

### Post by sheaty32 on 2013-11-04
Hello, 

I'm new to Ubuntu and I'm trying to get this working on my system but I'm having a hilarious amount of problems that prevent me from doing any sort of troubleshooting. (I'm posting this on my laptop)

1) How do you install NVIDIA drivers? I believe that if I can just properly install the drivers, all of my problems will be gone. I just need a step-by-step walkthrough.

The BinaryDriverHowTo/NVIDIA help website does not help me. I am not getting any "additional drivers" 



[Ignore below this line; this information may be relevant to my solution that's why I kept it]

1) I just installed Ubuntu 13.1 on my SSD. Right now, I have two monitors. One is a Crossover with 2560x1440 resolution connected via DVI-D to my GTX 680. If I boot into Ubuntu, everything works fine. Though, if I do CTRL+ALT+F1, the terminal shows, and if I press CTRL+ALT+F7 to switch back, my main monitor just goes to a black screen and a hard-reset is required to fix the issue. (Pressing CTRL+ALT+F1 does not work. My secondary monitor goes black which means the terminal is on my Crossover, but it just doesn't turn on)

During my own research, I have found various conflicting answers on how to handle this issue. Some say Ubuntu doesn't need the proprietary NVIDIA drivers. Other people are saying that it does. Some people suggest editing some config file in /etc/DX11/ which doesn't even exist for me. I don't know where to get started.

[SOLVED - Seems to happen because of problem 1]) The most annoying issue is that my mouse doesn't seem to work if I do anything outside of the Unity Launcher. I can open apps, click on things when I press my Windows key and search for things. I can also click on the top bar that has time/mail/context menu for rebooting, shutdown, etc. Though, I cannot click *anywhere* else. No desktop. No programs. No browser. Nothing.

I can still navigate though using tab and shift tab on my keyboard.

Ubuntu has nothing listed under additional drivers so, according to what I'm reading online, that means no further action is required.

Any solutions? Been using Windows all my life and I'd like to see what the hustle and bustle is about this OS.

Thank you for any help

EDIT: Some additional debugging: Looks like I can now cause the mouse to fail. When I open "APPEARANCES" to adjust my secondary display from landscape mode to portrait mode, that's when I lose the ability to click. Luckily, there was an error message that popped up saying "Sorry Ubuntu 13.10 has experienced an error" The path of the executable that this happened with was /user/bin/XORG

So, it looks like once I fix these monitor problems, everything will be good to go. 

EDIT: EDIT: I am starting to get the idea that because my configuration is rather unique (two monitors; one at 2650x1440 & the other at 1920x1080), I'm going to need the NVIDIA drivers.

---

