---
title: "lamp big problem"
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by ubuser_cse on 2008-08-09
Hi all
I was having my desktop Ubuntu 8.04 running ok, but I wanted to install lamp bundle so as to develop PHP on Ubuntu.
I did by the aid of the tasksel.
But O0ops removing removing removing .. and most of applications and software on the upbuntu were removed and lost. Even when I rebooted to Ubuntu it could not open in the GUI mode.
Can any one help me retrieving my system state or undo the damage occured?
thanks in advance

---

### Post by jimv on 2008-08-09
Boot into the command line and type

sudo apt-get install ubuntu-desktop

---

### Post by ubuser_cse on 2008-08-09
Thanks for your reply.
I followed your advice but it seemed not to be working.
"unable to fetch some archives"
After I had known that Ubuntu has no a feature like rolling back began to catch up with the fact that I have to install a fresh one and build my world from zero again :( 
Am I right or there still is a hope?

---

### Post by jimv on 2008-08-09
That means your internet isn't working...is it wired internet or wireless on that machine?

---

### Post by ubuser_cse on 2008-08-09
No it is working I'm running a desktop with a wired internet connection adn internet is ok from windows xp, and it was ok on ubuntu 8.04 before the crash

---

### Post by jimv on 2008-08-10
Does "sudo apt-get update" give an error?

---

### Post by ubuser_cse on 2008-08-11
It gives an error on updating a certain package

---

