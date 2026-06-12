---
title: "Login Failed"
date: 2005-05-28
forum: Installation &amp; Upgrades
---

### Post by Battlestar on 2005-05-28
Hi, i am new to ubuntu and linux in genral.

I am trying to login as root, but I do not know the password. I have installed it twice now, and it does not ask me for one. It also does not accept the password i created for my one and only user login.

Am i missing something here?
or whats going on?

Thanks in advance for any help.

---

### Post by Russellkhan on 2005-05-29
Ubuntu doesn't use root. Use sudo to do anything you might need root for. Example:

```
sudo updatedb
```

The system will ask for you a password, type in your own.

For more info, man sudo.

---

### Post by bored2k on 2005-05-29
[QUOTE=Russellkhan]Ubuntu doesn't use root. Use sudo to do anything you might need root for. Example:

```
sudo updatedb
```

The system will ask for you a password, type in your own.

For more info, man sudo.[/QUOTE]
 For more information, check the Ubuntu wiki regarding sudo:
[http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

---

### Post by Battlestar on 2005-05-29
thnx for info bro, but actually when I try to log in..There's a eeror I encountered like " you have mail blah blah" I can't log in :(

---

### Post by Battlestar on 2005-05-29
Update: Before I log in theres a message that display it can't configure the xserver-xorg (I think this is the videocard modes) then return to DOS MODE and login..I log my username and password and the rest error message is posted aboved. Somebody Help me please..:(..Sorry for being noob I really want to switch in Ubuntu now.

Again, Thanks for Replies...u

---

