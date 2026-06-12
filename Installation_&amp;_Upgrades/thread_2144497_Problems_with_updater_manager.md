---
title: "Problems with updater manager"
date: 2013-05-12
forum: Installation &amp; Upgrades
---

### Post by philis on 2013-05-12
Hello everybody,

I have Ubuntu 12.10 in my laptop. A few days ago, I got the following message:

"An unresolvable problem occurred while initializing the package information. Please, report this bug against the "update-manager" package and include the following error message: E:Malformed line 56 in source list /etc/apt/sources.list(dist parse)"

Since then I have not been able to install new software in my laptop.

Any tip on how to solve this problem is greatly appreciated.

thanks

---

### Post by Toz on 2013-05-12
Hello and welcome to the forums.

Can we have a look at your /etc/apt/sources.list file? Something is wrong on line 56.

---

### Post by ibjsb4 on 2013-05-12
Just incase your wondering how to do that :)

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
cat -n /etc/apt/sources.list
```

And post the output of that command using code tags.

[ATTACH=CONFIG]242528[/ATTACH]

---

