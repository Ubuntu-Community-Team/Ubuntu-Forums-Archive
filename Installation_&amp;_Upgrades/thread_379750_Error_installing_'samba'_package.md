---
title: "Error installing 'samba' package"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by rudyryk on 2007-03-08
Hello, suport! I got an error trying install 'samba' package. I suppose it's just a small bug, log information is below:

> 
# sudo apt-get install samba
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  samba: Depends: samba-common (= 3.0.22-1ubuntu4) but 3.0.22-1ubuntu4.1 is to be installed
E: Broken packages


Hope, you'll fix it soon :) Thank you for your job! :)

---

### Post by lhtown on 2007-03-08
Way to go on your first post. Just insult all of us.

We are not paid support. We are volunteers and fellow computer users. There are a few employees of Ubuntu on these forums, but they exist mostly just to monitor things and keep things rolling.

Happily, paid support is available from Canonical.

If you really want to use these forums, I would suggest that you peruse the following work:
[http://catb.org/~esr/faqs/smart-questions.html](http://catb.org/~esr/faqs/smart-questions.html)

In answer to your question, I would suggest trying the following:

sudo apt-get update

and then:

sudo apt-get dist-upgrade

Let us know how it works out.

---

### Post by rudyryk on 2007-03-12
hey, relax! :)

may be, something wrong with my English and I'm saying not exactly what I mean :)))

> 
In answer to your question, I would suggest trying the following:

sudo apt-get update

and then:

sudo apt-get dist-upgrade


Yes, I tried it in different ways - using adept and from shell.

Problem was solved by removing  samba-common (3.0.22-1ubuntu4) and reinstalling.

---

