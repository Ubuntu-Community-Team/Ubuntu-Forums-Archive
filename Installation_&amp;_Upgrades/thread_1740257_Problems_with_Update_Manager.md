---
title: "Problems with Update Manager"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by vankrazy on 2011-04-26
Hello there, I am very new to Ubuntu, but everyday I like it more and more! 
I'd like to ask a question concerning  my installation. It is Macbuntu 10.10.
I installed VirtualBox to then install WinXp for a program that I don't find a replacement. 
After installation I have this error in the update manager

[I]**Could not initialize the package information**

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'usage:' is not known on line 60 in source list /etc/apt/sources.list'[/I]

I will be very thankful for any help you can provide me.

---

### Post by mörgæs on 2011-04-26
Hi, welcome to the fora.

For Ubuntu, bugs are reported in Launchpad:
launchpad.net/ubuntu

It would be great if you could report it.

---

### Post by matt_symes on 2011-04-26
Hi

Might as well have a look at your sources file as well. From the terminal post the output of

```
cat /etc/apt/sources.list
```

Kind regards

---

