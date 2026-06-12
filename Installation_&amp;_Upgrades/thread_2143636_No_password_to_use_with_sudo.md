---
title: "No password to use with sudo"
date: 2013-05-09
forum: Installation &amp; Upgrades
---

### Post by acronym54 on 2013-05-09
I have installed and have Ubuntu running fine. I now need to add some software with the terminal. sudo asked for a password that I never had a chance to set during setup.
How do I set or find that password?

---

### Post by arsenic23 on 2013-05-09
When you entered your user name you didn't enter a password?  If so, I think, the password for sudo should just be blank.  
If not ::
Using the terminal: [http://manpages.ubuntu.com/manpages/hardy/man1/passwd.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/passwd.1.html)
I think that the gui for it is in the Users setting windows; I'm not sure how you get to that in Unity though, and I assume you are using Unity.

---

### Post by WTF_Shelley on 2013-05-09
the password will be the same password you set for the first user.

---

### Post by acronym54 on 2013-05-09
Actually, I'm trying to use su, not sudo. Sorry about that. I need administrator status to add stuff.

---

### Post by arpanaut on 2013-05-09
not the way it is done with Ubuntu:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by cibalo on 2013-05-10
Hi,
> **acronym54 said:**
> Actually, I'm trying to use su, not sudo.

Set up root password. Then run su.
```
sudo passwd root
```

---

### Post by oldos2er on 2013-05-10
> **cibalo said:**
> Hi,


Set up root password. Then run su.
```
sudo passwd root
```

We ask that new users not setup the root account because it subverts Ubuntu's security model, in addition to there being no need to do so. ```
sudo -i
``` will give a persistent root terminal, if desired.

---

