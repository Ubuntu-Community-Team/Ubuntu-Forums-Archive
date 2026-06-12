---
title: "Blank/black screen again, but im almost there..."
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by Maluminas on 2007-12-09
Hi all!

Im trying to install ubuntu 7.10 64bit on my new computer (with vista). Like so many people i hit the blank screen problem, so i came here in search of a solution. I compiled a list of all fixes i could find in this forum and tried them all. Yes i managed to cure the "blank" screen (monitor receives no signal and goes to sleep right after i select "run or install" on the liveCD), but i ended up with a  "black" screen (receiving signal but the image is black, explained below).

The fix i tried that gave the most positive results is the following (don't ask me what I'm doing I'm just blindly typing what others recommended lol):

-Highlight safemode
-Hit F6
-Erase "quiet splash--" and add "nosplash noapic irqpoll noirqdebug"
-Hit enter

Now lots of text scrolls up on my screen (yay its not blank! :P). I see my USB mouse and keyboard's lights are on and text zooming by hinting about a "gaming keyboard" being detected, which is good news. Then the text stops scrolling and i get that at the bottom of my screen:

"*Running local boot scripts (/etc/rc.local) _"

Now the screen flashes black 3 times and then becomes black permanently (but the monitor is still receiving a signal). After a few seconds the CD stops turning. I move my mouse and hit spacebar like some recommended, still nothing. All i can do is reset the comp.

I also tried exactly the same procedure described above but not in safe mode. The only difference is that when i get at "*Running local boot scripts (/etc/rc.local) _", the screen doesn't flash black and the text stays on. I can hit enter and it just adds "ubuntu@ubuntu:~$" every time i hit it.

So i got that far, i feel like i'm getting closer lol. Anyone knows what i have to do to get farther and maybe finally succeed and install it? :)

Thanks!

---

### Post by Maluminas on 2007-12-09
Bump?

---

### Post by uidb4056 on 2007-12-09
When you reach "ubuntu@ubuntu:~$" can you try to run startx to see if gnome windows manager starts?

---

### Post by Maluminas on 2008-01-12
Hi sorry for the delay, i finally have more time to lose on my foolish open source projects lol

I tried what you said uidb4056, but it didnt help. Heres exactly what happened...

-i highlight safemode
-i hit F6
-i change the end of the line "quiet splash --" to "quiet nosplash noapic --"
-i hit enter
-i wait for all the text to scroll by
-screen flashes black
-text stops scrolling at "*Running local boot scripts (/etc/rc.local) _"
-CD stops turning
-i wait
-nothing happens
-i just type "startx" right there, it appears on-screen, good... lol
-i hit enter
-screen goes black (as in receiving a signal but no image, monitors does not go in standby mode)
-CD resumes turning and turns for a few minutes
-CD stops turning, screen still black
-i wait
-nothing
-i press spacebar, move the mouse, nothing
-i wait
-nothing
-i press the reset button...

Any ideas?

EDIT: I looked around and the fact that i have two 8800GT cards in my system seems to be important...

---

### Post by tklinge on 2008-01-12
I have the same problem.  I can boot to the CD, but after clicking start/install it loads for a while then goes to a "black" screen.  It's not "blank" and my monitor is not in sleep mode, it's just black.  I've hunted through almost every page of every thread that talks about this problem, but most of them are for fixing the "blank" screen instead of my own problem.

---

### Post by Maluminas on 2008-01-12
Exactly! Im now sure it has to do with the Nvidia 8800GT graphics card. Ubuntu doesnt support it, its too recent. My guess is that the live CD boots alright but we just dont get any image since theres a problem with the VGA+ubuntu.

I guess we'll have to wait until Hardy Heron in late april and hope to god they fixed it :(

---

### Post by wilsonone on 2008-01-12
Try adding the following boot parameter.  no-hlt

Here is my post regarding this issue.
[http://ubuntuforums.org/showthread.php?t=652905](http://ubuntuforums.org/showthread.php?t=652905)

Good Luck

---

