---
title: "Gnome-Commander"
date: 2007-07-18
forum: Installation &amp; Upgrades
---

### Post by sasanf on 2007-07-18
I am experimenting with being able to use Ubuntu Linux as my desktop OS replacement.  I am a network admin and so far the test has gone really well.  I love Total Commander.  I can't live without it.  I am trying to install, from source, Gnome Commander 1.2.4.  In the readme are listed the libs I need to install before I begin compiling.  When I try to intall the libs via apt-get install, I get the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgnomeui-2

or

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnome-vfs-2

or

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libexif

or

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libid3

or

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgsf

What do I need to do to get these libs installed.

---

### Post by NumberOne on 2007-07-18
I like "Krusader" better than Windows Commander.  It can be installed thru synaptic.  No muss no fuss.

---

### Post by Steveway on 2007-07-18
Gnome-commander is in the repos.
Make sure you have Universe and Multiverse enabled.

---

### Post by rbmorse on 2007-07-18
Or, there's always the good ole Midnight Commander (MC).  It's already installed. 

from a term window:

mc

or sudo mc for mc with root permissions.

---

### Post by sasanf on 2007-07-18
I've already got Gnome Commander 1.2.3 installed.  I wanted to stay true to Gnome.  I didn't want to use a KDE centric program.  I've installed Krusader; apparently, I didn't have a lot of third party apps installed for it to run at full functionality.  I'll install it to see if I can get it to run with full functionality.  I still need some info on how to get Gnome Commander 1.2.4 installed from source.  I really want to learn how to do this so I can start building deb packages for the repos.

---

### Post by willdex on 2007-08-04
Hey, do you guys know how to remove that annoying **glass-breaking** sound in Krusader?

---

### Post by kuda on 2007-08-11
hi all, i cant also live without tcmd .... about that: sudo apt-get gnome-commander (universe or multiverse avaliable!) .. take a care about each letter ... it has to work!8)

---

### Post by oldos2er on 2007-08-11
Don't know if you ever got this going or not, but you need to go into Synaptic Package Manager, and search for each of those lib* names (libgsf, libid3, etc.), then mark them for installation. Hopefully that's enough to get you started.
 Might want to check these too: [https://help.ubuntu.com/community/CompilingEasyHowTo?highlight=%28compiling%29](https://help.ubuntu.com/community/CompilingEasyHowTo?highlight=%28compiling%29)
[https://help.ubuntu.com/community/CompilingSoftware?highlight=%28compiling%29](https://help.ubuntu.com/community/CompilingSoftware?highlight=%28compiling%29)

---

### Post by louieb on 2007-08-11
> **oldos2er said:**
> Don't know if you ever got this going or not, but you need to go into Synaptic Package Manager, and search for each of those lib* names (libgsf, libid3, etc.), then mark them for installation....
He is exactly right. Thats what I found out when I installed Pidgin on Dapper. The install script said i was missing this and I'd install it through Synaptic . Went round like that 3-4 times. And Pidgin finally installed and worked.

---

### Post by willdex on 2007-08-19
Sorry if it's a double post, but still...does anybody know how to eliminate any sound in Krusader?

---

### Post by willdex on 2007-11-01
Hi! Does anybody still remember how to remove that sound in Krusader? It plays every time you remove something [folder or file].

---

### Post by sasanf on 2007-11-01
Thank you everyone for your replies.  It has been a while since I looked at this thread.

---

