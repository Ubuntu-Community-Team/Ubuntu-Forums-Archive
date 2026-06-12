---
title: "update-alternatives --config question"
date: 2014-10-31
forum: Installation &amp; Upgrades
---

### Post by jr223 on 2014-10-31
Hi Everyone!

Just a question I have gotten back to configuriing my system and came accorss an earlier post for update-alternatives --config.
Can somone tell me what this does beyong the obivuous of letting you configure app through terminal?
I have looked for infromation on the command but have not come up with anything, even a man page.
If you have further insight into how I can use this command please let me know.

Can I use it to configure other items?

Thanks
Cheers
Happy Haloween!

---

### Post by egeezer on 2014-10-31
I just checked, and the man page for update-alternatives shows up in 14.04.1 and 12.04.5.  Check for typos - I often screw up that way!

---

### Post by Dennis N on 2014-10-31
> **jr223 said:**
> Hi Everyone!

Just a question I have gotten back to configuriing my system and came accorss an earlier post for update-alternatives --config.
Can somone tell me what this does beyong the obivuous of letting you configure app through terminal?
I have looked for infromation on the command but have not come up with anything, even a man page.
If you have further insight into how I can use this command please let me know.


It's purpose is to define default choices and a set of prioritized alternatives to them. They are not all applications - for example, you can define the system wide default mouse cursor.

"Alternatives" is short for Debian Alternatives. Read more here:
[https://www.debian-administration.org/article/91/Using_the_Debian_alternatives_system](https://www.debian-administration.org/article/91/Using_the_Debian_alternatives_system)

They are all found in the **/etc/alternatives** folder.

---

### Post by birkopf on 2014-11-01
Yeah, this is pretty much it. From the practical point of view you can use it to set the cursor theme of your choice, default browser and so on. Maybe in ububtu this can be done via application in your 'start menu' but on other flavors of Linux you need to first set it in.the preferences and update alternatives to actually see the effect.

---

