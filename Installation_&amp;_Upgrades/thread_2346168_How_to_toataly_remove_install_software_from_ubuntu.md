---
title: "How to toataly remove install software from ubuntu?"
date: 2016-12-12
forum: Installation &amp; Upgrades
---

### Post by 1ritesh on 2016-12-12
Hello,
I am facing problem for uninstalling software from ubuntu?
what is procedure for removing it?

---

### Post by howefield on 2016-12-12
Are we talking about removing software that has been installed via the Ubuntu repositories ?

Usually it would be a matter of running the Ubuntu Software package, searching for the software and remove from there, alternatively you can use the command line with apt remove or apt purge (apt-get for older releases than 16.04) eg,

```
sudo apt remove packagename
```

See [http://manpages.ubuntu.com/manpages/wily/man8/apt-get.8.html](http://manpages.ubuntu.com/manpages/wily/man8/apt-get.8.html) & [http://manpages.ubuntu.com/manpages/xenial/man8/apt.8.html](http://manpages.ubuntu.com/manpages/xenial/man8/apt.8.html) for more detail.

If you are talking about software installed via another method, please be a bit more specific.

---

### Post by 1ritesh on 2016-12-13
not working[ATTACH=CONFIG]272688[/ATTACH]

---

### Post by howefield on 2016-12-13
So that looks like something you downloaded from a third party site ?

Perhaps you could give some more details as to what it is and in future it would help if you copy/pasted the terminal output and posted it back here between [noparse]```

```[/noparse] tags for better readability.

---

### Post by vasa1 on 2016-12-13
[http://www.microchip.com/forums/m889018.aspx](http://www.microchip.com/forums/m889018.aspx)

---

