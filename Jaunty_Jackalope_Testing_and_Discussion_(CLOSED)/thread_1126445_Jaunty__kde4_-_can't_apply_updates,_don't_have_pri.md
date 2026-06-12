---
title: "Jaunty / kde4 - can't apply updates, don't have privileges"
date: 2009-04-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Pablo Pablovski on 2009-04-15
I updated to Jaunty last week, and have worked my way through a number of issues. However, I have one to do with software updates I can't seem to fix.

Whenever I click on the update notifier icon in the task bar, it loads up a new kde control centre app, showing the updates and alowing me to apply them.. However, that doesn't ask me to authenticate myself, which means the update fails. The attached screeny shows the issue.

Updates work fine using apt-get or Synaptic - can I change the action initiated by update-notifier to Synaptic?

Weirdly, I'm having the same problem installing .deb files - which fail with a similar privilege type error.

Help!

---

### Post by Pablo Pablovski on 2009-04-17
Sahmeful, red faced bump... Anyone?

---

### Post by Asraniel on 2009-04-17
did this just appear like this? probably a policy kit problem, in system settings you should find a policy kit section, look around there if you find something strange with the rights...

until then you can update with the console:
sudo apt-get update && sudo apt-get upgrade

---

