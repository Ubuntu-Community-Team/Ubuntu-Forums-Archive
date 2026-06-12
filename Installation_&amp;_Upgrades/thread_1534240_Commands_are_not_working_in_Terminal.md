---
title: "Commands are not working in Terminal"
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by minal on 2010-07-19
Hi all,

I am working on Ubuntu 9.10.
Since last two days there is issue while working with Terminal.
Whenever I type a command and press enter it doesnt do anything. command is not executed. I guess its in loop. when I press Ctrl+C then it comes out of loop. this happens with all commands and I am not sure what is the problem.
I have reinstalled Terminal but it did not worked.

Can anybody help me here

Thanks in advance 
Minal

---

### Post by nothingspecial on 2010-07-19
What commands are you typing?

Unless there is an option (usually -v) that lets you know what`s going on, the terminal will just sit there until it`s done what you told it to do.

If it`s happening for cd, ls, etc then there is a problem.

---

### Post by minal on 2010-07-19
yes it is happening for all commands.
even with ls,exit cd 
all commands.. not a single command is executing

---

### Post by nothingspecial on 2010-07-19
You`ve not messed about with your .bashrc or anything like that?

---

### Post by minal on 2010-07-19
I have to check that.. 
is there any parameter which will cause such issue?
I initially thought enter command is not working with terminal.
But did not get any help or clue regarding that.

---

### Post by nothingspecial on 2010-07-19
The easiest way to check would be to move your current .bashrc to a backup, I guess you`ll have to do it with nautilus, then copy the default one from /etc/skel to your home folder and restart bash.

Don`t forget to make sure you have the correct permissions, for the default bashrc once you have copied it.

I got to go now, check back later.

---

### Post by minal on 2010-07-19
it didnt work.. 
is reinstalling only option?

---

### Post by nothingspecial on 2010-07-19
Try creating a new user, does the problem persist?

If you can still operate synaptic, then look for zsh and install it.

Then see if you can login to a root recovery mode.
```

nano /etc/passwd
```

change the end of the line that applies to your user from /bin/bash to /bin/zsh

Ctrl O to save, Enter then Ctrl X to exit

Log out and back in again, can you issue simple commands?

---

### Post by blur xc on 2010-07-19
I had that happend while logged into my desktop pc via ssh, and I just hit enter a 2nd time and the command executed.  Dunno why it needed me to hit enter twice...  It's been a while since I've tried it, so dunno if it's still doing it.  While sitting at the machine it works just fine.

BM

---

