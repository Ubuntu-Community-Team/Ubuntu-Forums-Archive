---
title: "Can't log in"
date: 2005-06-21
forum: Installation &amp; Upgrades
---

### Post by livingword26 on 2005-06-21
I just installed ubuntu. It asked for user then password. It accepted them and says I have mail, but I still have a black screen with white letters. Is there something else I need to type in to get to the desk top?

---

### Post by bored2k on 2005-06-21
[QUOTE=livingword26]I just installed ubuntu. It asked for user then password. It accepted them and says I have mail, but I still have a black screen with white letters. Is there something else I need to type in to get to the desk top?[/QUOTE]
 Did you install the server or the normal install  ? You should have gotten greeted with the cute brown login manager. Try running startx . If nothing happens, try the command sudo apt-get install ubuntu-desktop. If nothing happens after that... you an X problem (for now let's hope that is not it).

---

### Post by livingword26 on 2005-06-24
Thank you. The "sudo apt-get install ubuntu-desktop" did the job.

---

### Post by bored2k on 2005-06-24
[QUOTE=livingword26]Thank you. The "sudo apt-get install ubuntu-desktop" did the job.[/QUOTE]
 Rock /on.
It's still a mistery to me why sometimes the packages do not get installed :S .

---

