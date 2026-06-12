---
title: "Ubuntu repositories question!!!"
date: 2006-04-27
forum: Installation &amp; Upgrades
---

### Post by lifeartist on 2006-04-27
Can anyone tell me how to add "ubuntu.packages.com" in the update repositories, since i need lot of packages listed there, and it's not in my repositories list?? :rolleyes:

---

### Post by aysiu on 2006-04-27
You mean [http://packages.ubuntu.com](http://packages.ubuntu.com) ?

That's not a repository. It's a list of what's in each set of repositories.

Try this:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by lifeartist on 2006-04-27
I already did that(the link u gave me), but still cannot acces some packages via apt-get that i find on [http://packages.ubuntu.com](http://packages.ubuntu.com). Whut's the problem, i upadted the repositories:

apt-get update

---

### Post by aysiu on 2006-04-27
[QUOTE=lifeartist]I already did that(the link u gave me), but still cannot acces some packages via apt-get that i find on [http://packages.ubuntu.com](http://packages.ubuntu.com). Whut's the problem, i upadted the repositories:

apt-get update[/QUOTE] What package, for example?

---

### Post by lifeartist on 2006-04-27
Well... for an example, Gnome-Commander and all packages that is related to it. Maybe I'm doing somrhting wrong?!!

---

### Post by aysiu on 2006-04-27
Can you post the *exact* output of all of these commands? ```
cat /etc/apt/sources.list
sudo apt-get update
apt-cache search --names-only gnome-commander
sudo apt-get install gnome-commander
```

---

### Post by lifeartist on 2006-04-27
It won't have any sense, since i already downlaoded mannualy, so output of last two commands wont be the same,and /etc/apt/sources.list is sam as original, only with uncommented lines whit the repositories.

---

### Post by Jagot on 2006-04-27
gnome-commander is in the universe repository.  Are you sure you have that enabled?  aysiu's last 2 commands will tell us if your sources.list gives you access to it.

You may want to run through this to make sure you have all the repositories enabled:

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

