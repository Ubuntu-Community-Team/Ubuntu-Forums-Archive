---
title: "problems with hardy"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by rob1984 on 2008-06-08
help!

i've just upgraded to hardy and it hasn't gone well, pretty much nothing works.

but before i give up and do a fresh install, i'd like to have a go at fixing it. as far as i can tell, this is what has gone wrong...

when i upgraded i got a message asking me to enable some repositories, i edited my sources.list and still got the message. like a fool, i went ahead anyway.  
now i'm hoping that installing the updates will make everything ok but i get an error "not all updates can be installed...run a partial upgrade" when i click partial upgrade, nothing happens.

also i keep getting messages such as "sudo: unable to resolve host laptop" laptop being the name of my box

i've attached my sources.list

can anyone help me out?

---

### Post by Pumalite on 2008-06-08
Try removing the Gutsy repo.
Check /etc/hostname or /etc/hosts

---

### Post by Kralizec on 2008-06-08
Have you tried doing the upgrade via terminal?
```
sudo do-release-upgrade
```

When I was trying to upgrade from feisty to gutsy, I had to do that; the graphical app kept throwing errors.

---

### Post by Pumalite on 2008-06-08
You might want to try this too:

sudo sed -i 's/gutsy/hardy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

---

### Post by rob1984 on 2008-06-08
thanks for the help!

it seems removing/replacing the gutsy repos has done some good and i've managed to get a dist-upgrade going.

i'll let you know the score when it's finished.

---

### Post by Pumalite on 2008-06-08
Good luck.

---

### Post by rob1984 on 2008-06-08
worked a treat!

almost back to normal now. just the package manager won't work.

it crashes when i press "install package"

any ideas?

---

### Post by Pumalite on 2008-06-08
sudo dpkg --configure -a
Post the output.

---

### Post by rob1984 on 2008-06-08
i don't get any output.  all i get is the "unable to resolve host laptop" message.

my "/etc/hostname" says "laptop".

---

### Post by Pumalite on 2008-06-08
Check /etc/hosts:

[http://ubuntuforums.org/showthread.php?t=784111](http://ubuntuforums.org/showthread.php?t=784111)

---

### Post by rob1984 on 2008-06-08
cheers!

i edited /etc/hosts and now i have no problems!  add/remove, synaptic and apt are all working fine.

thanks!

---

### Post by Pumalite on 2008-06-08
You are welcome. Good luck.

---

