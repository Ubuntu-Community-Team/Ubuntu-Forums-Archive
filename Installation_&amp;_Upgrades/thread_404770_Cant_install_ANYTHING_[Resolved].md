---
title: "Cant install ANYTHING [Resolved]"
date: 2007-04-08
forum: Installation &amp; Upgrades
---

### Post by ErusGuleilmus on 2007-04-08
Whenever I try to download and install any updates or programs, I get this error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

I then proceed to run this in the terminal. But it then states that I need to have superuser status to do that. Could any one help? I dont even know what superuser is!

---

### Post by picpak on 2007-04-08
To run a command as superuser, put **sudo** in front.

Example:

```
sudo dpkg --configure -a
```

---

### Post by aysiu on 2007-04-08
Try ```
sudo dpkg --configure -a
``` Then read this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ErusGuleilmus on 2007-04-08
Thank you, that worked liked a charm.

---

### Post by ErusGuleilmus on 2007-04-08
Actually, I spoke too soon. I do exactly as you say, but it then asks for my password. I push space and begin to enter my password, but it doesnt even give me a chance to finish it and it says that I have entered the wrong password!

---

### Post by aysiu on 2007-04-08
Don't push space. Just enter your password.

---

### Post by ErusGuleilmus on 2007-04-08
Thats exactly the problem. I cant type anything when the courser is right next to the "Password:" cue. I have to push enter or else I cant type anything in.

---

### Post by aysiu on 2007-04-08
This is [a bug with the terminal that the developers refuse to fix](http://ubuntuforums.org/showthread.php?t=214393), as it is a traditional part of *nix (a stupid part, if you ask me)--there is no visual feedback when you enter your password in the terminal. No flashing cursor. No asterisks appear. **Your password is still being accepted**. Just type the password and hit *Enter*. You won't see anything, but you should still just type it.

---

### Post by ErusGuleilmus on 2007-04-09
Hey, wow, now *that* worked. I love this OS, there are so many people willing to help. Thank you.

---

### Post by garyedwardjohnston on 2007-04-09
THANKS THIS WORKED FOR ME TOO!

Man; I love the feeling of not using pirated software.

:)

---

