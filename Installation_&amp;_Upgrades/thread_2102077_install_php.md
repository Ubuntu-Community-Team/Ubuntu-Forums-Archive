---
title: "install php"
date: 2013-01-06
forum: Installation &amp; Upgrades
---

### Post by Lagbehind on 2013-01-06
How do I install php to work on a single pc?

---

### Post by rreyes3713 on 2013-01-06
I'm not an expert in this field but did you install Apache? If you haven't, install it and while you are at it install MySQL.

I have those two installed in my two old 10.04 laptops it was not difficult but I did install in the Terminal Window not GUI. 

Read up on Ubuntu documentation "How to install Apache"

I'll chime in again when I get Apache / MySQL on my new laptop (12.10 / Window 8).

Yeah, I know, not much help. Bumping your post and hope others chime in.

---

### Post by Lagbehind on 2013-01-07
Many thanks, of course Apache is what I need, I really should have known better.  I will read the "How to install documentation" and as usual much of it I won't understand, but it will take me a step or two closer.  If later you have anything else to add please do.  Many thanks

---

### Post by steeldriver on 2013-01-07
I used the very easy instructions from Cheesemill here 

[http://ubuntuforums.org/showthread.php?t=2038021](http://ubuntuforums.org/showthread.php?t=2038021)

It installs a whole 'LAMP stack' (i.e. mysql as well as apache) but that's probably not a bad thing

---

### Post by tgalati4 on 2013-01-07
It could be as simple as:

```
sudo apt-get install php5
```

But depending on what you want to do:

```
apt-cache search php
```

If you simply want to run a web server, then install the LAMP stack.  There are several tutorials on how to do that.

One of my favorites is to use Task Select (tasksel).  It runs in a terminal and it will install the LAMP stack with a few keystrokes.

```
sudo apt-get install tasksel
sudo tasksel
```

Follow the instructions.

---

### Post by na5h on 2013-01-08
If you only need PHP for testing purposes, you might want to take a look at [XAMPP]("http://www.apachefriends.org/en/xampp.html").

---

### Post by Lagbehind on 2013-01-08
Thanks, though I am a little nervous won't Lamp "mess-up" the existing Mysql and workbench installation" ?

Everything is new in Ubuntu. Including the new file structures, I haven't go my head around those yet.

---

### Post by tgalati4 on 2013-01-08
That depends on what version of mysql you are using.  If it is exactly the same as in the LAMP package, then the configuration will detect the existing database and ask you for your mysql admin password so it can populate the database.  It will add tables to your existing data--which you may or may not be happy with.  Then mysql will server data for both the web server and any other application that uses mysql, except the databases will be different and kept separate.

Install:  phpmyadmin - MySQL web administration tool

And run it in a webpage so you can see all the databases/tables that are currently in use.

---

