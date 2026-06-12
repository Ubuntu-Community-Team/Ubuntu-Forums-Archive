---
title: "Oneiric Ocelot Python 3,1"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by jdcb92 on 2011-10-23
Hello Ubuntu Community. I recently migrated to Ubuntu and I'm definitely loving it. The only issue I'm having so far is not being able to install Python 3.1 on 11.10. First, I looked for it in Ubuntu Software Center, but it wasn't available there. Then I tried to install it from the terminal but it prompted me that it was unable to locate package. I really need this version of Python for college assignments, but I can't find anywhere help for this matter.

Thanks in advance.

---

### Post by oldfred on 2011-10-23
Welcome to the forums. 

I thought, since they do not install synaptic everything would be available in the Software Center.

Try installing synaptic and then run it. You can do a search on python3 and it will give you the current version it has in the repository. That may or may not be the version you want or need.

Whatever you do, do not uninstall the current version of python as the system depends on that version.  It used to be a reinstall to fix if you uninstall python and it still is major repairs.

```
sudo apt-get install synaptic
```

Did you try running 
sudo apt-get install python3

the python3 usually links to the available version.

---

### Post by jdcb92 on 2011-10-24
I installed Synaptic and looked for python 3.1 IDLE, but it wasn't available, so I installed "python3 all" hoping that it was included, but it wasn't. 

Yes, I already tried sudo apt-get python3, but it returned that the latest version was already installed and if I look for python in search it doesn't appear IDLE for 3.1, just 3.2.

---

### Post by dniMretsaM on 2011-10-24
Python 3.1 isn't available in the Oneiric repos. Just 3.2.2 (and 2.7.x). You can either compile it or just use 3.2.

---

### Post by jdcb92 on 2011-10-25
Excuse me for my ignorance, but how do I compile it?

---

### Post by dniMretsaM on 2011-10-25
Read [this guide]("https://help.ubuntu.com/community/CompilingEasyHowTo") and if you have any questions, feel free to ask. And I'm curious as to why you want to use 3.1 instead of 3.2.x.

---

### Post by jdcb92 on 2011-10-25
Thanks, I'll check on it and if I have any doubts I'll ask here.

Because of college. They check for my homeworks and stuff on 3.1, so if there is son kind of syntax error or something doesn't run because it was made in another version; I get a 0.

---

