---
title: "Severe priveldge problems- HELP!"
date: 2005-09-13
forum: Installation &amp; Upgrades
---

### Post by leezer3 on 2005-09-13
Hi all,
I've just installed 5.04 clean on a new HDD. The install went reasonably, although it refused to load several modules beginning with IDE.
Now, I have a working Gnome desktop, but the priveledges are totally fubared, and I would appreciate some help. This is what happens at the mo:
1. Log on with user & password.
2. Attempt to run something requiring root priveledges- Prompts for password; So far so good.
3. I enter the password I just used to logon with- Nothing happens.
4. Try to launch the app I was trying to run from a terminal ie. Synaptic- Tells me that the password is wrong, without even allowing me to re-enter it.
5. Try to launch the app through sudo- Again tells me that the passoword is wrong (I'm certain its not :rolleyes: ), and throws me out after three attempts, then telling me that I am not in the sudoers file, & that the incident will be reported.

If I could actually get into the users control panel, I would probably be enabling root, & creating another user to try and sort out this mess. As you can see though, I can't.

Thanks

-Leezer-

---

### Post by leezer3 on 2005-09-14
<BUMP!>
Small update on the problem- By doing CTRL+ALT+F1, I can login to root & killall GDM before restarting the X-Server to give me a working system, but nothing I've managed to do at the mo has got the standard user root priveldges (and sudo) working, up to & including the creation of an entirely new user. It also doesn't want to let me enable standard root login.

Summats fubared.

Cheers

-Leezer-

---

