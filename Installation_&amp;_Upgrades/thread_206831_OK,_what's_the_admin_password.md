---
title: "OK, what's the admin password?"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by MDesigner on 2006-06-30
I installed Ubuntu, and I have no clue what the admin password is.  It's not the password it asked me for when I installed..that's how I log into my account.  But when I use sudo to do things, it asks me for an admin password.  What the heck?

---

### Post by taurus on 2006-06-30
If you use sudo to execute a command, use your own password that you use to log in!!!  It's the SAME password...

---

### Post by christhemonkey on 2006-06-30
It *should* be the password you setup whilst installing...


Is this on a default install of ubuntu (not with vmware or something)?
You havent done any thing like sudo passwd root?
(I suppose that would recuire the sudo password... :p)

You can boot into recovery mode, and then login and type
```
passwd root 
```

(To get into recovery mode, press 'esc' whilst booting and showing the grub countdown, then go down and select recovory mode.)


The password you then type will be your root password.

---

### Post by user1397 on 2006-06-30
also, just so you know, ubuntu disables the root account by default, that is, the "admin password" like you said.  this makes things a little safer.  for more info, read: [http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

### Post by MDesigner on 2006-06-30
Weird..yes, the password I chose at install (e.g. xyz123) is what I typed when prompted by sudo.. it didn't work.  Oh well.  I'll do the recovery mode thing then. Thanks

---

### Post by taurus on 2006-06-30
Do you belong to groups adm & admin?  At the prompt, see if you are with this command.
```

id

```

---

