---
title: "Skype security risk?"
date: 2006-10-07
forum: Installation &amp; Upgrades
---

### Post by jis on 2006-10-07
I have added repository "deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free" as suggested in [http://www.skype.com/download/skype/linux/repositories.html](http://www.skype.com/download/skype/linux/repositories.html). Now that I am going to upgrade (or should I say update), Software Updates warns me that Skype can't be authenticated, and installing the software "could allow a malicious individual to damage or take control of your system". Could I restrict Skype's permissions so that it wouldn't have such power or should I consider some other software?

---

### Post by pay on 2006-10-07
The message you are recieving it concerning the repository. Because the repository isn't an official repository you get that message. To stop having apt warn you about that repository you have to import it's keys usually found  at the repository's home page. If you don't trust the repository however then don't use it.

---

### Post by jis on 2006-10-07
I wish there were some restricted sandbox for closed source software so that you would not have to trust the author so much, if you use the software.

I think I'll try WengoPhone from universe, instead.
See [http://fossvoip.blogspot.com/2005/12/why-thou-shall-not-use-skype.html](http://fossvoip.blogspot.com/2005/12/why-thou-shall-not-use-skype.html) for more reasons to avoid Skype.

---

### Post by aysiu on 2006-10-07
Ubuntu has its own repositories for Opera and Skype: ```
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

---

### Post by jis on 2006-10-07
> **aysiu said:**
> Ubuntu has its own repositories for Opera and Skype: ```
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

I have Opera in Synaptic even though all the repositories I have now are form *.ubuntu.com.

---

