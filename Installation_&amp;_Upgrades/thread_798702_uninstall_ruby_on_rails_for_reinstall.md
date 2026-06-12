---
title: "uninstall ruby on rails for reinstall"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by jethroalias97 on 2008-05-18
Hey, so i installed ruby on rails, but i encountered some problems so i tried to uninstall it by removing individual file, i ended up removing the executables ruby and gem, this turned out to be a bad idea because every install attempt beleives that those already exist so won't reinstall them. can anyone help me as to how to unistall/reinstall ruby on rails, Thanks.

---

### Post by jethroalias97 on 2008-05-23
I think it has something to do with the path or something. the system seems to beleive that everything is still in tact which is a bummer, i don't know how to convey to the computer that i want it to install it all again, I've tried yelling and swearing at it, but that rarely works. Anyway if anyone has any ideas they should feel free to post them on this thread :)

---

### Post by jethroalias97 on 2008-05-23
I don't understand why ubuntu wont let me perform an install, it shouldn't matter whether or not my computer thinks something is already installed, i say install it should install. gaaaa frustrating.

---

### Post by mamboze on 2008-05-25
Hi,
I don't know whether I can be of much help to u as I'm a ubuntu/ruby on rails noob. But here goes. Did you use synaptic or apt-get to uninstall. I've found synaptic to work flawlessly removing and reinstalling when I have any problems with apps. 

Sorry that I can't be more specific here. But I'm interested in any problems people have with the ruby/rails combo (and ubuntu too).

Hope this helps a little

---

### Post by jethroalias97 on 2008-05-29
hey, thanks for responding, i have tried apt-get to uninstall, the trouble is that it uninstalls pieces of it, but when i try to reinstall it still assumes other parts (like the gem executable file) are already installed : (. im hoping that i don't have to reinstall to get this to work *sigh*

---

### Post by jethroalias97 on 2008-10-21
<a href="http://septosoft.com/rankmaniac">rankmaniac</a>

---

### Post by jethroalias97 on 2008-10-21
dbunker is rankmaniac (you gotta be kidding me)

---

### Post by xtek0 on 2010-09-23
> **mamboze said:**
> Hi,
I don't know whether I can be of much help to u as I'm a ubuntu/ruby on rails noob. But here goes. Did you use synaptic or apt-get to uninstall. I've found synaptic to work flawlessly removing and reinstalling when I have any problems with apps. 

Sorry that I can't be more specific here. But I'm interested in any problems people have with the ruby/rails combo (and ubuntu too).

Hope this helps a little

Okay me being a semi-noob to linux, I have used it much more frequently in the past than i do now. I want to help you out.

Go to System >> Administration >> Synaptic Package Manager >> Search: "Ruby" to remove all packages associated with ruby. Then go ahead and do a fresh install. that should cover it.

---

