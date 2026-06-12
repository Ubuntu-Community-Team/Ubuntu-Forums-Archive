---
title: "Howto create a new GROUP/USER pair?"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by cookdav on 2007-11-06
What tool or cmd would I use when I want to ADD a new GROUP and USER pair, to
my Kubuntu (7.10) system?

As one example, the 'mythtv' application wants a new user added, but NOT to the
existing group 'kubuntu', but rather to create both a GROUP named 'mythtv' and
a then a new user within that group, also named 'mythtv'.

TIA...

Dave

---

### Post by osx on 2008-06-27
When you add a user account, Ubuntu automatically creates a group by that same username. So, if you add a user called "mythtv" it will also create a group called "mythtv" and the user will be part of that group.

Here's the command I would use to do this:

```
sudo adduser mythtv
```

Upon executing this command, you will be prompted for information such as what you want the password for the user to be, their full name, etc. Fill in the details that you want and then confirm them at the end when it prompts you for confirmation.

---

