---
title: "Source code installation triggers"
date: 2015-08-16
forum: Installation &amp; Upgrades
---

### Post by kyle-kuhn on 2015-08-16
In Ubuntu 12.04.5, I used the Code::Blocks IDE source code to install it (rather than from the repositories, since it's out of date for 12.04), I managed to get it working, however, there is a small problem.

I looked for Code::Blocks in the Unity Shell, however, it's not showing up. Code::Blocks works just fine from terminal, but having that consistently in the background would be unnerving. I suspect that this is due to not having run the post installation triggers similar to what dpkg does when it installs a package. Is there any method for running these triggers and convince it to show up in Unity, or would I have to uninstall and reinstall it in a different manner?

---

### Post by dino99 on 2015-08-16
maybe glance to that qa

[http://askubuntu.com/questions/198442/how-to-install-code-block](http://askubuntu.com/questions/198442/how-to-install-code-block)

---

### Post by kyle-kuhn on 2015-08-16
> **dino99 said:**
> maybe glance to that qa

[http://askubuntu.com/questions/198442/how-to-install-code-block](http://askubuntu.com/questions/198442/how-to-install-code-block)

Thank you, I found Jen's repository to be useful and much less troublesome than from installing from the source.

---

