---
title: "ssh no longer stores key passphrase in gnome keyring"
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by beo on 2010-04-24
Hello all,
I've just installed the 10.4 RC and it works almost fine (I had to use nomodeset to get the display working) except for the situation with ssh described in the subject. Whenever I connect to a service which use ssh key to authenticate (e.g. a subversion repository using the svn+ssh scheme), ssh always asks for the private key passphrase - it used to be stored in the keyring once and then taken from there ever after. Anyone experiencing the same behavior? Any idea what might be causing it and how to fix it? Thanks in advance guys.

---

### Post by Aearenda on 2010-04-24
One reason might be if you have auto-login enabled, the keyring isn't unlocked.

Does it prompt you EVERY time, or only the first time you use ssh per login?

Edit: Adding the public key corresponding to the private key into .ssh seems to help.

Edit2: Make sure you have checked the box to save the password hidden behind the 'Details' part of the GUI key prompt that appears if the keyring is unlocked.

---

### Post by beo on 2010-04-26
> **Aearenda said:**
> One reason might be if you have auto-login enabled, the keyring isn't unlocked.

Does it prompt you EVERY time, or only the first time you use ssh per login?

Edit: Adding the public key corresponding to the private key into .ssh seems to help.

Edit2: Make sure you have checked the box to save the password hidden behind the 'Details' part of the GUI key prompt that appears if the keyring is unlocked.

I don't have auto-login enabled. It prompts me every time I use ssh, .ssh has both private and public key present (it's been there for the past ~10 years in fact :D). As for the last part - the thing is, the GUI prompt to unlock the keyring has never appeared, which might be an indication to the actual problem.

---

### Post by beo on 2010-04-26
I've just noticed that ssh-add -l reports my ssh keys as represented by the current agent, but instead of using them, the agent keeps adding the same dsa/rsa keys to the collection (each time it asks for the password it adds one entry)

---

### Post by LKjell on 2010-04-26
10 years? Might expired? You could always to delete and create new with ssh-keygen and ssh-copy-id

---

### Post by beo on 2010-04-26
> **LKjell said:**
> 10 years? Might expired? You could always to delete and create new with ssh-keygen and ssh-copy-id
No, it's not expired :) The same keys work fine on Jaunty or any other Gnome-based distro - it's some issue with either the keyring or the ssh-agent, but there are no clues (no errors in ~/.xsession-errors, no segfaults, nothing out of order in the logs) as to what it might be.

---

### Post by Aearenda on 2010-04-26
Maybe you could kill the existing agent, run another with -d for debug, and then see whether it gives you any more clues. See 'man ssh-agent' for details.

---

