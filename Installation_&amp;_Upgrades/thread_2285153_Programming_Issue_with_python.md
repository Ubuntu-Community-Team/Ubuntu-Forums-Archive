---
title: "Programming Issue with python"
date: 2015-07-03
forum: Installation &amp; Upgrades
---

### Post by jorge23 on 2015-07-03
I'm trying to run a python program using ipython notebook on Ubuntu 14.04.

I found an older thread here that seems to have the solution that I'm looking for, however its a solution for Ubuntu 12.04.

Here's the link: [http://ubuntuforums.org/showthread.php?t=2138623](http://ubuntuforums.org/showthread.php?t=2138623)

I downloaded the library that I needed and extracted it in my downloads but when I type in this command "./configure --prefix=usr/local/libpng" into the terminal, the terminal outputs: "configure: error: expected an absolute directory name for --prefix: usr/local/libpng".

Is it that the specific command that I'm telling the terminal has changed over the versions?

Or is it that the library that I downloaded doesn't contain what ever I told the terminal to look for?

I'm fairly new to Ubuntu, so explain like I'm five please.

---

### Post by steeldriver on 2015-07-03
Hello and welcome to the forums

Not sure what you're trying to install, however the command probably needs to be

```

./configure --prefix=[COLOR=#0000ff]**/**[/COLOR]usr/local/libpng

```
(note the leading [COLOR=#0000ff]**/**[/COLOR] on the file path)

---

### Post by jorge23 on 2015-07-04
Yes you were correct, it did need that "/"!

Thank you very much!

---

