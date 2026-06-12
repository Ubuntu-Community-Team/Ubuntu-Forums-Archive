---
title: "No upgrade option in upgrade manager"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by kudos1uk on 2007-11-05
When I open upgrade manager its does not give me an option to upgrade to 7.10, I'm currently on 7.04.

I click "check" it asks my password, but I get no option to upgrade to 7.10.

Many thanks for any tips.

---

### Post by Pumalite on 2007-11-05
You might want to try this:

sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list

sudo apt-get update

sudo apt-get dist-upgrade

(I have to tell you that, personally, I'm in favor of a clean install)

---

### Post by kudos1uk on 2007-11-05
Thanks, no joy though.

I get "downloading package information" this stops at 42 of 57 so have to press cancel.

I then get a list of failed repo indexes.

Then I just get update manager building a tree and saying I'm updted?

---

### Post by Pumalite on 2007-11-06
[http://ubuntuforums.org/showthread.php?t=600485](http://ubuntuforums.org/showthread.php?t=600485)

---

