---
title: "can't get ubuntu"
date: 2008-04-10
forum: Installation &amp; Upgrades
---

### Post by jaws31415 on 2008-04-10
sudo apt-get install ubuntu-desktop

I kept getting the same message:

reading package lists...done
building dependecy tree
reading state information...done
E: couldn't find package ubuntu-desktop

[/QUOTE]

how do I get around this?:confused:

---

### Post by Pumalite on 2008-04-10
Your sources list need to be enabled.
System>Administration>Software Sources. Make sure they are all enabled.

---

### Post by jaws31415 on 2008-04-10
I have no desktop, do you know how to do this through a terminal?

---

### Post by Pumalite on 2008-04-10
How did you get to have no Desktop?

---

### Post by oldos2er on 2008-04-10
"sudo nano /etc/apt/sources.list"

 Remove the # comment mark from lines beginning with deb and deb-src, except for the backports section. Hit Ctrl-X when you're done; you'll be prompted to save the file. Save it, then run

"sudo aptitude update && sudo aptitude install ubuntu-desktop"

---

### Post by jaws31415 on 2008-04-10
the synaptic package manager deleted it

---

### Post by Pumalite on 2008-04-10
Fix your sources.list, then run:
sudo aptitude update
sudo aptitude install ubuntu-desktop

---

### Post by jaws31415 on 2008-04-10
> **oldos2er said:**
> "sudo nano /etc/apt/sources.list"

 Remove the # comment mark from lines beginning with deb and deb-src, except for the backports section. Hit Ctrl-X when you're done; you'll be prompted to save the file. Save it, then run

"sudo aptitude update && sudo aptitude install ubuntu-desktop"
I'm tryng this but it has no response to 'ctrl x'  it seems rather frozen now

---

### Post by Pumalite on 2008-04-10
Try this:
gksudo gedit /etc/apt/sources.list
Comment out (remove the #) in front of the 'deb' lines
Save, exit.
sudo aptitude update
sudo aptitude install ubuntu-desktop

---

### Post by jaws31415 on 2008-04-10
'sudo aptitude update && sudo aptitude install ubuntu-desktop'

with this I get a bunch of 'could not resolve: archive ubuntu.com

---

### Post by jaws31415 on 2008-04-10
this almost seemed to work, but I still got a bunch of 'could not resolve 'archive.ubuntu.com'  anybody have any ideas

---

### Post by oldos2er on 2008-04-11
Are you connected to the internet when you run the command?

---

### Post by oldos2er on 2008-04-11
> **jaws31415 said:**
> the synaptic package manager deleted it

 Deleted what?

---

### Post by jaws31415 on 2008-04-13
all the programs and now I can't open the desktop

---

