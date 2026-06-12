---
title: "Home directory already exists"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by eks on 2008-05-25
Hello!

I just re-installed Ubuntu 8.04 over a formated / partition where 7.10 was. I had another partition just for /home, where I had an account for me and my wife.

During the installation I added my account. Now, after the system is completely installed, I am trying to add her user account, with the same username as before, and I get this error:

```

Home directory already exists
Please enter a different home directory path.

```

I'm sure I did this before, but I can't remember how. Any ideas?

Is it ok if I rename her home folder to something else, create the user, and rename back the original folder?


Thanks for any help!
eks

---

### Post by mbaker824 on 2008-05-25
> **eks said:**
> Hello!

I just re-installed Ubuntu 8.04 over a formated / partition where 7.10 was. I had another partition just for /home, where I had an account for me and my wife.

During the installation I added my account. Now, after the system is completely installed, I am trying to add her user account, with the same username as before, and I get this error:

```

Home directory already exists
Please enter a different home directory path.

```

I'm sure I did this before, but I can't remember how. Any ideas?

Is it ok if I rename her home folder to something else, create the user, and rename back the original folder?


Thanks for any help!
eks

I assume you're using System->Administration->Users and Groups to create the account - for whatever reason, that's what it does; it won't create the account if the home directory already exists.

You can do this, however, using the 'useradd' command from a terminal:
```
useradd --home /home/*username* --shell /bin/bash *username*
```

This will create an account named *username* and an initial login group by the same name.  You can then go back to the Users and Groups applet and set her password, real name (if desired), and User Privileges.

Good luck,
Mark

---

### Post by eks on 2008-05-25
That was exactly the case! :D


Thanks a lot!!
eks

---

