---
title: "Adept Installer not connecting to Repository"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by ndefontenay on 2007-02-13
Good morning,

I've installed kubuntu on a Dell box at office.
Everything is going smoothly.
My only problem left is that adept manager is not connecting to the repository.
Is there something to setup somewhere to specify proxy connection or is there some port to unlock on firewall?

Those are the only 2 things I've identified that could be a potential problem.

If yes, how can I do that?

Thanks for your help.

---

### Post by ndefontenay on 2007-02-14
Hello,

problem is solved.

The solution is as follow:

```
export http_proxy=http://[proxy_address]:[port]
```

then 

```
apt-get update
apt-get upgrade
```

For some reason during that time adept started working correctly.

---

