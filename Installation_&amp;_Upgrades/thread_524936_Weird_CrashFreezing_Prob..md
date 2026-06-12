---
title: "Weird Crash/Freezing Prob."
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by Corbin on 2007-08-13
Hey, im trying to figure out this weird freezing/Crashing problem i have.

It happens when i (TRY) to open Synaptic Package Manage. The freezing/Crashing will happen maybe ever other or every other other time. 

What happens is. I go to open Synaptic and it ask me to enter my password (so i do) and then it "start to load" But the whole screen just dims down (i think its one of my Compix effects). And then i am unable to do anything. I can move the mouse but nothing else will work. SO to get out of it i will have to Ctrl+Alt+Backspace It and then it all goes back to normal and loads right up...

Any help would be SWEET

-Cheers

Edit: I know it may not be the BEST section for posting this.... But i figured since it had something to do with Synaptic it might fit into the (upgrades) part of this section... If i was wrong i apologize.

---

### Post by Ryzol on 2007-08-13
I don't specifically know if this will work, but when other apps have repeatedly frozen like that I found that killing their .appname file in my home folder generally does the trick. I would recommend backing up/renaming that folder first just in case this has unintended side affects and you need to revert. 

Oh and you probably don't have to restart X to get of a frozen program. I've always found this to work:

press ctrl+alt+f1 through f6 to switch to a tty.
login.
type "ps -e | less"
type "/UNRESPONSIVE_PROGRAMNAME" / is the command in less for searching
press n to cycle through matches until you find the one you want
memorize the number to the left of it and press q to exit less
type "kill memorized_number"
press ctrl+alt+f7 to switch back to your gui
if it is still frozen switch back to tty1-6 and type "kill -9 memorized_number"

I'm sure this is more confusing if you aren't familiar with the commandline than ctrl+alt+backspace to simply restart X, *but* it is faster, and you do not lose work open in other programs.

---

### Post by Corbin on 2007-08-15
^^^^ahh Thanks^^


BUt the more time goes on,  the more and more it keeps happening and even with different types of programs...

Anyone got anything??

---

### Post by Corbin on 2007-08-16
Any suggestions are welcome..

---

