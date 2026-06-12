---
title: "No tab completion in terminal"
date: 2009-02-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by maverick340 on 2009-02-27
I installed Ubuntu 9.04 Alpha4 and upgraded it to Alpha5 (ran upgrade -d)
TO begin with , my terminal shows on a $ instead of username@hostname. Also tab completion is not working, it simply moves ahead whitespaces. and up/down arrow keys for recent commands not working?
Is it only me ?

---

### Post by smani on 2009-02-27
Do the .bash_history, .bashrc, .profile etc files exist in your home directory? You may want to try to create a new user and look if the issue persists.

---

### Post by maverick340 on 2009-02-28
Hmm yeah. I did create the user with the simple ```
adduesr -m <username>
``` option. I had to add my uname to sudoers list after that. What if those files dont exit in my /home ?

---

