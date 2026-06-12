---
title: "How can I see where an app is installed?"
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by dontfeedthegoat on 2008-09-25
There have been a few times recently when I wanted to see where a package was installed to. Is there any way to see this info?

---

### Post by Elfy on 2008-09-25
They usually go to /usr/bin but whereis will work 

```
whereis *program*
```

---

### Post by crwmike on 2008-09-25
The program binaries are usually found in **/usr/bin**, most application files are found in **/usr/share**, global config files in **/etc**, and user config files in your home folder in the form of *.program*.

EDIT:

In the terminal, type the following to find them. 
```
sudo find / -name *program*
```

---

### Post by DJ_Peng on 2008-09-25
Thanks for that code. I usually fire up Synaptic and check the Installed Files tab but this is even easier.

---

### Post by Yannick Le Saint kyncani on 2008-09-25
> **DJ_Peng said:**
> Thanks for that code. I usually fire up Synaptic and check the Installed Files tab but this is even easier.

Yep, that would have been my answer, check the installed files in synaptic. Or do it in command line (dpkg -L packagename).

Edit: And don't forget to check the package dependencies if you have to.

---

