---
title: "How do I make a standard configuration?"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by pauwl on 2007-02-05
Could someone point me to what I need to read up on to get a standard install done?

Let me explain a little: I keep re-installing my machine, and I then go to the Add/Remove to remove some apps, and add others.

Is there any way I can create a script to run, or make a config file that the Add/Remove app will see and install/remove as required?

Do I need to use apt-get install..... or can I suffice with a config?

thanks,

Pauwl

---

### Post by lucia_engel on 2007-02-05
I did a search and I think this should work.

[http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html]("http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html")

This will get you a list of all the installed applications and output it to a file call **installed** in the current directory.
```
dpkg --get-selections > installed
```

This will read from the file **installed** and mark everything listed for installation.
```
dpkg --set-selections < installed
```

---

### Post by pauwl on 2007-02-05
Aah..
excellent, thanks.

Follow up with a 'sudo dselect install' and all is well..


many thanks.

---

