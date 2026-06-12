---
title: "how to reinstall ubuntu from within ubuntu"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by Mikey Teh Zombe on 2010-03-25
my friend gave me this mini dell with ubuntu and told me its password protected and cant use wifi and forgot the password and i can only use ethernet, also the start button is gone somehow so i decided to just reinstall ubuntu but i dont know if i can, any ideas how?
btw, there is no cd drive or flashdrive so i need to know if i can reinstall within ubuntu

---

### Post by mikewhatever on 2010-03-25
You can easily clear the keyring password using the following command, and the start button wasn't there in the first place.
```
rm ~/.gnome2/keyrings/default.keyring
```

If you do want to reinstall, just follow the regular installation procedure, as if Ubuntu wasn't already installed.

---

### Post by Mikey Teh Zombe on 2010-03-25
im brand new to ubuntu i dont know regular procedures and i dont know how to use that code i dont see a menu for access to programs anywhere on the desktop

---

### Post by new_tolinux on 2010-03-25
Alt+F2 should give you a box to run a command.
Type in: ```
gnome-terminal
```Then you should see something like:
```
username@pcname:~$
```After that you should be able to type in the command given (and press enter):
```
rm ~/.gnome2/keyrings/default.keyring
```

Maybe gnome-terminal is not really needed, but that way you can see and read the output (which is none if everything is OK ;))

---

### Post by Mikey Teh Zombe on 2010-03-25
i have a minidell.... no f keys...

---

### Post by new_tolinux on 2010-03-25
Sorry, I didn't know that.

Guess I'm out of options then, as I'm not really an experienced linux-user myself.

---

### Post by mikewhatever on 2010-03-25
> **Mikey Teh Zombe said:**
> im brand new to ubuntu i dont know regular procedures and i dont know how to use that code i dont see a menu for access to programs anywhere on the desktop

Here is a very good installation guide.
[http://www.ubuntumini.com/2009/11/installing-ubuntu-910-karmic-koala.html](http://www.ubuntumini.com/2009/11/installing-ubuntu-910-karmic-koala.html)

---

### Post by Mikey Teh Zombe on 2010-03-25
i found a way into terminal :D
but the password reest thing the one guy gave me got me this
rm: cannot remove `/home/brendon/.gnome2/keyrings/default.keyring': No such file or directory


any ideas?

---

### Post by mikewhatever on 2010-03-25
Perhaps there is no password set, and keyring was simply asking you to provide it? You don't have to, just click ok leaving the password field blank.

---

### Post by d3v1150m471c on 2010-03-25
Why not just download a live cd and then reinstall it? The guy put ubuntu on it somehow so I'd ask him, and if not, check your boot options. Either way Ubuntu wasn't magically installed from thin air so by default there must be a way for you to do a default installation.

---

### Post by Mikey Teh Zombe on 2010-03-25
**_I have a dell mini_**
there are no disk drives.
there is a pass which restricts me from doing practically anything in the terminal, i cant mount the ubuntu iso to reinstall it (if that would even work) i don't think i have any more options.

please help

---

### Post by mikewhatever on 2010-03-25
Sure you do. Countless Ubuntu users got it installed on their netbooks using USB sticks. Have you looked at the link I posted on the previous page?

---

### Post by d3v1150m471c on 2010-03-26
> **Mikey Teh Zombe said:**
> **_I have a dell mini_**
there are no disk drives.
there is a pass which restricts me from doing practically anything in the terminal, i cant mount the ubuntu iso to reinstall it (if that would even work) i don't think i have any more options.

please help

The live cd is a bit misleading. It's simply an iso image. Again, check your bios boot options and write the .iso file properly to the device you will be booting from. Your friend put Ubuntu on the computer so you can also.

---

