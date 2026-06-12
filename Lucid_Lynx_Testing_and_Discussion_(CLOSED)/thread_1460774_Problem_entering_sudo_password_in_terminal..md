---
title: "Problem entering sudo password in terminal."
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mrpinchy on 2010-04-23
I've realized I have a problem.  When I open a terminal and enter a command where I need to enter my sudo password my keyboard crashes.

To be specific, I can't type anything (numbers, letters or symbols), until I hit enter three times and terminal asks for a new command.

Any ideas?

I should probably file a bug report no?

Thanks,
Joe.

---

### Post by VMC on 2010-04-23
> **mrpinchy said:**
> I've realized I have a problem.  When I open a terminal and enter a command where I need to enter my sudo password my keyboard crashes.

To be specific, I can't type anything (numbers, letters or symbols), until I hit enter three times and terminal asks for a new command.

Any ideas?

I should probably file a bug report no?

Thanks,
Joe.

Does the keyboard work when you enter password for using Synaptic?

---

### Post by mrpinchy on 2010-04-23
Yes.

---

### Post by florus on 2010-04-23
You do know that your password does not appear as you type in Terminal, don't you? Just type your password and hit enter. Sorry if I am stating the obvious.

---

### Post by dannyboy79 on 2010-04-23
does it crash when having to authenticate using sudo for everything within a terminal? maybe you have a bad gnome-terminal installed (if using gnome) why don't you install xterm or another terminal emulator and try using it there. like 
sudo apt-get update

or even go to tty1 (by hitting ctrl-alt-F1) then login to the text environment using username and password, and try 
sudo apt-get update there. does tty1 crash? I doubt it. I am guessing it's a problem with gnome-terminal if password auth works within a gui password prompt like synaptic.

not sure how to help you unfortunately.

---

### Post by Longinus00 on 2010-04-23
> **florus said:**
> You do know that your password does not appear as you type in Terminal, don't you? Just type your password and hit enter. Sorry if I am stating the obvious.

The 'hit enter three times to continue' bit leads me to believe that this is the correct answer.

---

### Post by mrpinchy on 2010-04-23
I'm at work so I don't have my computer handy, but I thought I did that. Typing my password and hitting enter.  I'll try it again later.

Thanks for the replies.
Joe.

---

### Post by mrpinchy on 2010-04-23
So it would seem someone spiked my coffee with some extract of idiot root this morning.

I thought I tried typing my password and pressing enter...   ...but I guess I just thought about it.

Thanks gang,
Joe.

---

