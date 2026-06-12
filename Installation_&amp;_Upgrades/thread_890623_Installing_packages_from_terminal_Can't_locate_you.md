---
title: "Installing packages from terminal: Can't locate your X11 installation"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by Thee_Baron_ on 2008-08-15
Hello, I'm wanting to start install packages from the terminal as it allows me to use up to date applications. After getting the C compiler to work I'm now getting an error saying:
> checking for X... no
configure: error: Can't locate your X11 installation
I've looked through the repositories searching for x11 but there to much things with x11 in the title to get the one I need.

Thanks!

---

### Post by iaculallad on 2008-08-15
> **Thee_Baron_ said:**
> Hello, I'm wanting to start install packages from the terminal as it allows me to use up to date applications. After getting the C compiler to work I'm now getting an error saying:

I've looked through the repositories searching for x11 but there to much things with x11 in the title to get the one I need.

Thanks!

On your terminal, install the xlibs-dev package:

```
sudo apt-get xlibs-dev
```

---

### Post by HarryG123 on 2012-04-13
I'm running xubuntu 11.10 and have the same problem.  I need to install Fontforge, which I used to run under cygwin in Windows. 

But the above command does not work.

What do I do now, other than

[INDENT][I]When in trouble, fear or doubt,
Run in circles, scream and shout.[/I]  


[/INDENT]

---

### Post by oldos2er on 2012-04-13
Closed, necromancy. Please start a new thread.

---

