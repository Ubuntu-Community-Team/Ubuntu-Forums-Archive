---
title: "Can no longer access synaptic. Asks for Root password ?"
date: 2006-03-20
forum: Installation &amp; Upgrades
---

### Post by weasel fierce on 2006-03-20
After the most recent updates, that popped up, if I try to access Synaptic through the GUI, rather than the terminal, the password box is a bit different, and now asks for my root password. 
Typing in my regular password makes it reject it.

What gives ?

---

### Post by encompass on 2006-03-20
sounds like somehow you have lost rights to it or created a root account.  Check your user's rights in users and group settings.  Happened to me once and got me really confused.

---

### Post by weasel fierce on 2006-03-20
My user profile still has the full privileges. How do I check regarding a root account ?

---

### Post by weasel fierce on 2006-03-21
As a further note, I figured out how to set my root password. Now, synaptic doesnt even prompt me for a password, period, though if I try to just use apt-get through the terminal, it still refuses, unless I sudo

---

### Post by petri on 2006-03-21
Did you check your group settings? 
I belonged to sudo-group and didn't have to use password with terminal-sudo or synaptic. How did that happen, I don't know.

---

