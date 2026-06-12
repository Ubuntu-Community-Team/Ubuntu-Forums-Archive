---
title: "help on running an installed program (matlab)"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by a_satari on 2007-11-09
hi, I've installed matlab R14 but I don't know how to get it to run.

 Its not under Applications.

I installed it under /home/ali/Matlab when I go to that folder I can't find a file to make it run. 

I skipped a section of the installation instructions:

Step 10: Specify Location of Symbolic Links
Specify where you want to put symbolic links to the matlab and mex scripts in
the Installation Data dialog box. Choose a directory such as /usr/local/bin
that is common to all your users’ paths. Click OK to continue with the
installation.

I forgot where I put the directory for this but I didn't use /usr/local/bin as suggested in the instructions. 

I'm sure the answer is simple but i can't figure it out. If you need more specifics just ask. 

Thank you.

---

### Post by bulldog on 2007-11-09
Try and just type matlab in your terminal.
 You can do a search in terminal locate matlab

---

### Post by a_satari on 2007-11-09
thanks.

I typed in matlab and it said: command not found.

I don't know how to do a search in the terminal to find matlab. However I know how to search using  the "search for file" program under Places.

Any other ideas?

---

### Post by lxop on 2007-11-14
Go to where you say you installed Matlab, and open the file simply called 'matlab'.  It might be in a folder called bin.   This should open it (does for me). Once you can get it to run, you just need to make a link to the file, in one of the folders the shell searches for commands, eg /usr/bin.  To do this, open a terminal, cd to /usr/bin, then type  "sudo ln -s /home/ali/Matlab/bin/matlab" without the quotes.  Hopefully, you will now be able to just type matlab into the terminal and get the program to start.  If you want a link in the menu, go to Sytem>Preferences>Main menu, choose a category you want to put Matlab in, and click <New Item>.  Give it a name ("Matlab" maybe?), for the command, put "matlab", and you should be good to go.

---

