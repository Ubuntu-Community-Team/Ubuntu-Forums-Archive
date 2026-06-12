---
title: "help me!"
date: 2005-07-10
forum: Installation &amp; Upgrades
---

### Post by cccpfal on 2005-07-10
i just installed ubuntu but i can't use it really..the installation program told me to use the 'sudo' command to boot my user as root but it doesnt work..how can i initialize mi adsl connection?

---

### Post by llamakc on 2005-07-10
type:

sudo [nameofyourcommand and arguments] 

and hit enter, you'll get a password prompt. Put your password in here. The command gets executed.

For example:

sudo /etc/init.d/networking restart

and I will get a prompt. I put my username's password in and voila!

---

