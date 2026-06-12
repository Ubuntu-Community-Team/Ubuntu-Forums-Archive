---
title: "Can't login after upgrade"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by ralnar on 2008-04-25
I upgraded my 7.10 to 8.04 using update-manager. Everything seemed to work OK, but after restarting I can't login anymore.

In 7.10 the login screen displayed the names of the three accounts I created, I clicked on my name and entered my password.

Now I get to a login screen with just a blank username field. If I fill that in with my name(what I used to click on) I get a password prompt. If I enter my old password, I get error "wrong password".

I see two possibilities from my newbie perspective:
* My username is something else than my Firstname Lastname
* My accounts have been overwritten

Anyone who knows?

---

### Post by dsiembab on 2008-04-25
You could probably start the computer in recovery mode by hitting escape after the bios loads you will be logged in as root  and the "cd /home" adn the type dir and it =should show you the directory names which I would think are you account names.

---

### Post by ralnar on 2008-04-25
Thank you. Solved the problem.

---

### Post by dsiembab on 2008-04-25
glad I could help

---

