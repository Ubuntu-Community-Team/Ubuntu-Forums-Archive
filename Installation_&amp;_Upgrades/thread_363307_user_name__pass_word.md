---
title: "user name / pass word"
date: 2007-02-16
forum: Installation &amp; Upgrades
---

### Post by PigPopper on 2007-02-16
omg im going slowly mad. 

hi all, i've just dared to give Linux a try and downloaded and installed ubuntu 6.10 onto my toshiba P100 laptop, with marginal success. I have partitioned repartitioned / installed and reinstalled, shaken not stirred but i am still getting stuck. 

The problem is i cant log in at the log in screen, i did not stipultate a user name, ubuntu was the only name that came up and i left it as the defualt, i did add a password and even wrote it down, BUT adding these details just displays the [COLOR="Red"]Incorrect username or password message[/COLOR]. 

Please help me im growing really tired of this and feel like a complete noob :(

---

### Post by Kateikyoushi on 2007-02-16
There is an option to login as root something like recovery mode.

Then use the useradd command to create a user and try to login with that user.

---

### Post by PigPopper on 2007-02-17
could you be more specific about running commands for me please? i typed useradd and got a list of letters with some discriptions but dont know how to use them.

---

### Post by Kateikyoushi on 2007-02-17
Man useradd should explain the syntaxis of the command. Here is a [link]("http://www.linuxcommand.org/man_pages/useradd8.html").

I would try this
```
useradd -D -m -p PASSWORD LOGIN
```

---

### Post by mcduck on 2007-02-17
I suppose you did the OEM install? That's not really any use for normal users, it only makes the install more complex. (it's for pre-installing Ubuntu on machines that are to be sold).

Anyway, in that case the user name is 'oem', use that to log in, and the run  'sudo oem-config-prepare' to complete the installation, restart the machine and then Ubuntu will ask you all info needed to create the real userfor the system.

---

### Post by Kateikyoushi on 2007-02-17
I never heard about this OEM install, I take a look at it as I remember I saw someone reinstalling several times this week because could not log in. Thanks for pointing out mcduck.

---

### Post by PigPopper on 2007-02-17
Thanks mcduck, that did it :)

and thanks for the link Kateikyoushi, i've found somewhere to study stuff :)

---

### Post by LazyTownRocks on 2007-02-17
You might have tried this ... if not then try leaving the username blank and hitting return then putting your password in at the password screen?

---

