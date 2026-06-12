---
title: "Gen Installation help for the Newbie"
date: 2005-08-03
forum: Installation &amp; Upgrades
---

### Post by axman1971 on 2005-08-03
I'm sure I should lurk around the forum a bit before I post this... but just in case... I'm not the only one with this problem... I've had a general problem just installing anything on my own...
My roommate is a lil more advance in Linux than I and installed KDE for me with out a prob... 
Yet I try to do the same or get an ap somewhere and I stumble round and get frustrated... does anyone have some words of advice? I've several things I'd love to install and not a clue on how to actually install them.

---

### Post by adwait on 2005-08-03
You really need to be more specific.....installing what?

---

### Post by axman1971 on 2005-08-08
Your right I should have been more specific, thanks 
I’ve used synaptic over the weekend and that worked, I think unlike windows Icons don't appear on your desktop. I’ve even had some headway using get apt from a terminal but like the above unless I can "See" where the ap is I don't know if it's installed. This sound silly even as I type it but… coming from a windows environment I’m way too used to double clicking on a .zip or an .exe to launch and install… I’ve downloaded RPM’s and Tar files quickly found that doesn’t really work that way, or should it? I’ve a program on my desktop now… that instructs me to:
Su(do) root
Run ./install.sh

First of all I can't sudo…I get some odd password error 
so I just “su” and it works, I'm in as root...right?
no matter what directory I’m in, typing different permutations of run ./install.sh does nothing.
Since I’m not in front of my desktop at the moment I don’t have the name of this program… but it’s just an example of what happens when I try to install ….well, anything the problem here is the instructions because I’m just not getting it

---

### Post by adwait on 2005-08-08
The command ./<whatever> executes a bash script, and often this is used to install a programs. Now, for sudo, if you are the first user created on this system, you should be able to sudo. Use your own password when it asks for the password in sudo....If you can't do this, post the exact error it gives.

---

### Post by axman1971 on 2005-08-09
The Ap I'm trying to install is called iPodder-linux
I entered: 

sudo root
Password:
sudo: root:  command not found

---

### Post by axman1971 on 2005-08-09
Oops Never mind.
I simply needed to cd in to the Ipodder folder to run ./install as root..
so the solution here was: just to 
su
cd (folder)
./install.sh


Thanks for the help

---

