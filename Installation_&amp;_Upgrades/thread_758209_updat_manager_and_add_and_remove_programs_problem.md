---
title: "updat manager and add and remove programs problem"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by alushon on 2008-04-17
hey everyone,i'm a total beginner with linux and i've been working with windows all my life,so i know very little about linux.I just installed a fresh version of Ubuntu gutsy(7.10) and everything seems to work fine,but when i try to launch the add and remove programs application and the update manager,the programs close in just about a second.any suggestions would be greatly appreciated.

---

### Post by oldos2er on 2008-04-17
Can you type "sudo synaptic" in a terminal, and post any error msgs that show up?

---

### Post by alushon on 2008-04-17
this is the output  i get when i type that:
(synaptic:6983): Gtk-WARNING **: cannot open display:

---

### Post by zirjacks on 2008-04-17
I am having the same problem. 
The error I get is
sudo: /etc/sudoers is mode 0446, should be 0440

What does this mean?

---

### Post by alushon on 2008-04-17
who knows........

---

### Post by oldos2er on 2008-04-18
> **zirjacks said:**
> I am having the same problem. 
The error I get is
sudo: /etc/sudoers is mode 0446, should be 0440

What does this mean?

 It mean permissions on /etc/sudoers are screwed up.

---

### Post by oldos2er on 2008-04-18
> **alushon said:**
> this is the output  i get when i type that:
(synaptic:6983): Gtk-WARNING **: cannot open display:

 In a terminal, run this command: sudo aptitude update && sudo aptitude upgrade

 That will at least get you updated. After it's finished, try running Synaptic again.

---

