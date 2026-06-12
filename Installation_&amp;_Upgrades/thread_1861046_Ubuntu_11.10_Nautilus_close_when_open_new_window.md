---
title: "Ubuntu 11.10 Nautilus close when open new window"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by rolodoom on 2011-10-15
I just installed Ubuntu 11.10 AMD64 and Nautilus closes whenever I trie to open a new window.

Any clue?? I have absolutly no idea.

Thanks

---

### Post by rolodoom on 2011-10-15
OK. Solved. Found a solution here:

[http://askubuntu.com/questions/65443/nautilus-on-ubuntu-11-10-keeps-crashing]("http://askubuntu.com/questions/65443/nautilus-on-ubuntu-11-10-keeps-crashing")

It was an incompatibility with this command "nautilus-open-terminal". Proceeded to remove it and everything came back to normal.

```
sudo apt-get --purge remove nautilus-open-terminal
```

---

### Post by Jeepty on 2011-10-15
Thanks for this, my windows would close randomly after double clicking a folder icon and this fixed it.

---

### Post by Didge on 2011-10-19
Many thanks. Solved it for me too.

---

### Post by raja.genupula on 2011-10-19
please mark the thread as solved from thread tools and its helpful to us look unsolved threads.

---

### Post by Bao2 on 2011-10-19
What is now the quick way of launching a terminal inside a folder if we can't use nautilus-open-terminal ???

I wonder if ubuntu developpers use ubuntu as it comes from a fresh installation. Because man, I spend hours to make it workable. Give some prize for example to the genious that get rid of synaptic. I bet 100% people first thing that do now is installing back synaptic. And like that a lot of esential things. My guess is developpers of ubuntu use fedora or debian or something...

---

