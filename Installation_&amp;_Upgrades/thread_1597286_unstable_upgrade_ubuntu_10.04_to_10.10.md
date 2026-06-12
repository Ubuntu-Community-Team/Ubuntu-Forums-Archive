---
title: "unstable upgrade ubuntu 10.04 to 10.10"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by Lars_bylund on 2010-10-15
ok, so my update manager tells me 10.10 upgrade is available, 
I klick, and it says:

"= Welcome to the Ubuntu 'Maverick Meerkat' development release =

*** 
This is still a RELEASE-CANDIDATE release.
[COLOR=Red]Do not install it on production machines.  [/COLOR]
***"

I thought that the STABLE version should be out by 2010-10-10?

I tried to change the server from sweden to main, but same unstable 10.10

Please help.

---

### Post by sanderd17 on 2010-10-15
can you run

```

sudo aptitude update

```

and post the output if you have any errors.

If you don't have errors, try the update manager again.

---

### Post by Lars_bylund on 2010-10-15
That DID help, thanks, please tell me why, I'm new to linux....

---

### Post by sanderd17 on 2010-10-15
Ok, I'll explain the complete command:

```

sudo

```
short for "super user do ..." or "switch user do...". This has to be called for every *important* change, something that can break the system like installing software.

```

aptitude

```
This is a tool to install packages. Aptitude has better automated solutions than the older apt-get (you might have seen apt-get before). The purpose of aptitude is the same as apt-get but some enhancements are brought in to it:
[http://www.andrewault.net/2010/05/03/aptitude-vs-apt-get-comparison-2/]("http://www.andrewault.net/2010/05/03/aptitude-vs-apt-get-comparison-2/")

```

update

```
you give this argument to the aptitude tool, this asks the aptitude tool to update all repository databases. only the databases of availiable software, not the software itself. It seemed you had an old database (still the RC version) so updating the database helped.


If you want to learn the basics of the command line, see this tutorial:
[http://linuxcommand.org/learning_the_shell.php]("http://linuxcommand.org/learning_the_shell.php")

This guides you to the main usages of the command line, if you've read it and you want to do something new with the CLI, you just need to find the right tool and you'll probably see it operates like other CLI programs.

---

