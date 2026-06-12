---
title: "Handy shortcuts for &quot;sudo apt-get install&quot; etc."
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by kwilliam on 2007-08-14
This is for those of you who, like me, find finding and installing programs with apt-get easier and faster than using any GUI. I used "apt-cache search" and "sudo apt-get install" daily.  Eventually, I decided to save myself a little time by aliasing the commands with shell scripts.  I thought others might also find them useful.  Here they are:

/usr/local/bin/appgrep
```
#!/bin/sh
apt-cache search $@

```

/usr/local/bin/appget
```
#!/bin/sh
sudo apt-get install $@
```

/usr/local/bin/appgone
```
#!/bin/sh
sudo apt-get remove $@
```

Don't forget to chmod +x them.

---

### Post by kidders on 2007-08-15
Hi there,

Since they're all one-liners, this sort of thing can also be easily done with shell aliases ... perhaps a slightly easier approach.

---

### Post by kwilliam on 2007-08-24
> **kidders said:**
> Hi there,

Since they're all one-liners, this sort of thing can also be easily done with shell aliases ... perhaps a slightly easier approach.

Yes, you could do that too.  I'm just in a habit of using shell scripts, because I can easily modify them (and make them more than one line if I wanted to), and they are easy to track down. Aliases can be defined in so many places, and are specific to each user.

---

### Post by schmappel on 2007-10-26
> **kidders said:**
> Hi there,

Since they're all one-liners, this sort of thing can also be easily done with shell aliases ... perhaps a slightly easier approach.

Just for the record, how would the same thing be done with shell aliases?

---

### Post by kidders on 2007-10-26
Just add something like **alias appgone="sudo apt-get remove"** to any shell login script.

---

### Post by vinces1979 on 2008-07-17
Heres my apt aliases:

alias aptget='sudo apt-get install'
alias aptgrep='sudo apt-cache search'
alias aptupdate='sudo apt-get update'
alias aptupgrade='sudo apt-get upgrade'
alias aptup='aptupdate ; aptupgrade'

---

