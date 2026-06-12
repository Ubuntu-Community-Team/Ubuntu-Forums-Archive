---
title: "xubuntu alternate CD didn't ask me for a username !!!"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by davodavo on 2006-12-06
hi there, 

i have installed xubuntu alternate CD OEM installation twice on my laptop, and i am 200% sure that it did NOT ask me for a username, only asked me for a password, after asking me for the computer name that it will appear in a network !!

so now i cannot log in after the installation >_<////

i have tried all sorts of possible username i can think of.....including the computer name, root ...etc   BUT all these usernames failed as expected !

any ideas?  plz help !

thank you very much in advance !!

cheers

David

---

### Post by wpshooter on 2006-12-06
You are probably choosing to do OEM installation and sounds like to me that that is NOT what you are wanting.  It's been a while since I installed from the ALTERNATE, so I forget what the other choices are but you need to choose the one that will give you a regular workstation setup and NOT OEM.

Good luck.

---

### Post by davodavo on 2006-12-06
ok, i just found out the username for my case is "oem" !!  phew....


thx guys

cheers

---

### Post by taurus on 2006-12-06
Login with username oem and the password that you created during the setup.  Then at the prompt, run

```
sudo oem-config-prepare
```
to create a new user and remove the oem account.

---

### Post by emarkay on 2006-12-20
Someone needs to make that clearer in the install - I remember seeing this but didn'y know why!

Also to let us clueless masses know that we are called "OEM" until then!!!

---

### Post by andrea70 on 2008-01-31
> **taurus said:**
> Login with username oem and the password that you created during the setup.  Then at the prompt, run

```
sudo oem-config-prepare
```
to create a new user and remove the oem account.

I log with oem and my pwd (which I am sure about) but it keeps saying it is uncorrect. any idea?

---

### Post by andrea70 on 2008-01-31
solved!

I reinstalled everything in text mode and the whoel thing worked properly.

Obviously this is a shortcut, but I just wanted ubuntu to work, I do not care whetehr with text mode or oem.

---

