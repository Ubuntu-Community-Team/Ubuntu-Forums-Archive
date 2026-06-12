---
title: "can't upgrade to gutsy"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by tyggna1 on 2007-10-28
Every time I use the upgrade button from my feisty fawn install, it says that I'm not authenticated.   I know I've had problems with aptitude in the past--my sources.list got deleted for some strange reason.   I think I don't have the public key that I need to use the Ubuntu server.  Anyone know where I can get it?

---

### Post by mlind on 2007-10-28
Does your apt keyring have Ubuntu archive gpg keys?
```

sudo apt-key list

```

I think you should have at least these two:
Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>


if you dont, then you need to import the archive keyfile
```

sudo apt-key add  /usr/share/keyrings/ubuntu-archive-keyring.gpg

```

the file may also be /usr/share/apt/ubuntu-archive.gpg

---

### Post by tyggna1 on 2007-10-28
Hmm, I have both those keys (got them by restoring defaults in software sources on the authentication tab).   I still can't upgrade, can't be authenticated.

Any ideas?

---

### Post by mlind on 2007-10-29
Could you post the full error message update-manager pops out?

---

### Post by tyggna1 on 2007-10-29
> Authentication failed

Authenticating the upgrade failed. There may be a problem with the network or with the server. 

I've been able to upgrade two other computers on this same network, though.  It does all the periodic updates just fine--but won't take Gutsy.

---

### Post by tyggna1 on 2007-10-30
bump

---

### Post by tyggna1 on 2007-10-31
Well, I'm guessing here-but the live gutsy CD won't work on that computer either.  It only has 256MB of RAM, so I think that the RAM is just too low to support the upgrade--and the Ubuntu server knew that.

---

