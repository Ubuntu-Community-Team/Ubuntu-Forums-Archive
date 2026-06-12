---
title: "E:ERROR please help !"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by Rob2008 on 2008-04-09
I get the following error when i go to use the update :(


E: ERROR: could not create configuration directory /home/root/.synaptic - mkdir (2 No such file or directory)

Rob

---

### Post by kellemes on 2008-04-09
try the following from terminal..
```
sudo usermod -d /root root
```

---

### Post by Rob2008 on 2008-04-09
> **kellemes said:**
> try the following from terminal..
```
sudo usermod -d /root root
```

That worked ! thanks but why? I'm completely new to Ubuntu & Linux can you explain why i need to use that ?

regards

Rob

---

### Post by kellemes on 2008-04-09
> **Rob2008 said:**
> That worked ! thanks but why? I'm completely new to Ubuntu & Linux can you explain why i need to use that ?

regards

Rob

Probably you enabled your root-account? Not recommended these days, but still possible and it should be possible without issues like this.. Not sure if this is reported as a bug actually.
Anyway, for some reason your root home-directory is set to /root/home. It should be /root.

"usermod -d /root root" set's your root home-directory back to /root.

Edit: for more info on usermod see.. [http://linux.die.net/man/8/usermod]("http://linux.die.net/man/8/usermod")

---

