---
title: "add/remove and gkdebi don't work but synapti does.."
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by hammer v2 on 2007-12-15
I think I've killed something somewhere..

I keep getting this error when using add/remove programs and gtkdebi


[I]Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
[/I]


I've done what it says and according to the terminal everything is fine. I can even apt-get install anything from the terminal. 

My sources.list is correct and when I apt-get install -f I don't get any errors....

I'm confused... anyone got any ideas?

---

### Post by hammer v2 on 2007-12-15
Hey guys, after a bit of research, I'm prettysure that it has something to do with python-apt...


Not sure exactly what it is but I'm pretty sure that that is where the problem lies? Any uber ubuntu masters wanna help me out here?

H.

---

### Post by Sef on 2007-12-15
> check the file permissions and correctness of the file '/etc/apt/sources.list'

Have you checked your source list?

If not, then ```
cat /etc/apt/sources.list
```

Then post it here.

---

### Post by hammer v2 on 2007-12-16
I source-o-matic'd the sources list and it's working fine...

Here's another clue....
If I type 

sudo gnome-app install

It Works!!!
But if I use it from my user account it doesn't work... hmmmmm

Any ideas?
synaptic and apt-get both work fine

---

### Post by Sef on 2007-12-17
Add/Remove and gkdebi are both guis.   It looks like you did something to the gui frontend while leaving the backend alone.  That's why those two don't work.   Do you have any ideas specifically what you did?

---

