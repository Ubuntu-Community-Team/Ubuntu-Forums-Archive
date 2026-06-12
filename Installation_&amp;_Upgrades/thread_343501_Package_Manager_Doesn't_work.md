---
title: "Package Manager Doesn't work"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by jourman17 on 2007-01-21
Hey Everyone

A couple of days ago my update notificator in **edgy** was flashing for some updates. I installed the updates but one of them with name **_wpasupplicant_** wasn't  installed and it gave out this message: 
[PHP]E: /var/cache/apt/archives/wpasupplicant_0.5.7+3v1ubuntu4_i386.deb:
 subprocess new post-removal script returned error exit status 10[/PHP] 

and it has been therer ever since now.

Any one know how to solve this problem.

Thanks

---

### Post by jourman17 on 2007-01-21
And by the way I can't use my apt-get or other package managers too.

Thanks again

---

### Post by garyinok on 2007-01-21
Hi,
Try this link for a solution.

[http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html)

Hope this helps.

---

### Post by jourman17 on 2007-01-21
Thanks Garyinok but that page is about another error.

And When I run:
[PHP]sudo apt-get -f install [/PHP]

or try to install anything from apt or synaptic I get this:

[PHP]
E: The package wpasupplicant needs to be reinstalled, but I can't find an archive for it.[/PHP]

I have no idea how to solve this problem does anyone?

---

### Post by billybag on 2007-01-22
hey man, i am having the same exact problem. i came across this just now. i have not tried it yet, but figured i would pass it along

[http://ubuntuforums.org/showthread.php?t=337691&highlight=wpasupplicant](http://ubuntuforums.org/showthread.php?t=337691&highlight=wpasupplicant)

and i found this.
[http://ubuntuforums.org/showthread.php?t=337529&highlight=wpasupplicant](http://ubuntuforums.org/showthread.php?t=337529&highlight=wpasupplicant)

hope this helps[hope it helps me as well]

-b

---

### Post by billybag on 2007-01-22
i just tried that second link. it worked

---

### Post by jourman17 on 2007-01-22
Thanks a lot billybag.

---

