---
title: "Let non-root users install apps"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by sanderd17 on 2011-04-07
Hi,

I'm going to set up an Ubuntu computer for my family. They asked for it, I didn't push them. But I know that they don't like passwords.

So my plan is to make an admin account which is in the sudoers group and then make induvidual accounts for the users. But I also want them to be able to install apps. 

So I wonder if it is possible to set the computer so that they can use the software center. What is the best method to do this? The apps mustn't be installed system-wide.

---

### Post by ~Plue on 2011-04-07
edited-reread your post
> 
The apps mustn't be installed system-wide.otherwise, you could add to sudoers,
```

username ALL=(ALL) NOPASSWD: /usr/bin/software-center
```and add *gksu* to the software center entry in the menu

-good luck

---

### Post by searchfgold6789 on 2011-04-07
It's not really possible to have apps -not- installed system-wide. There are a few reasons for this.

[LIST]
[*]Many apps need to access system files.
[*]Problems would be caused if two users decided to install the same program.
[/LIST]
This could possibly be bypassed if you use source code to install programs, depending on the program.

---

### Post by sanderd17 on 2011-04-09
> **~Plue said:**
> edited-reread your post
otherwise, you could add to sudoers,
```

username ALL=(ALL) NOPASSWD: /usr/bin/software-center
```and add *gksu* to the software center entry in the menu

-good luck

I added

```

sander ALL=(ALL) NOPASSWD: /usr/bin/mintinstall

```

to the /etc/sudoers file

(it's my own user to test it)

but wether I use the "gksu /usr/bin/mintinstall" or just "mintinstall", I always have to give my password. In the first case I have to give it when I launch the program, in the second case when I click "install".

---

### Post by ~Plue on 2011-04-09
> **sanderd17 said:**
> 
but wether I use the "gksu /usr/bin/mintinstall" ....... I have to give it when I launch the program,
well.. i couldn't come up with any reasons why sudo (and in turn, gksu) would require a password when the NOPASSWD tag is used..
could you recheck it?

also, you shouldn't edit the  /etc/sudoers file directly since there might be syntax errors that could prevent you from using sudo at all. 
*visudo *would lock the file > save changes to a temporary file > check it and then make changes

---

