---
title: "No load of Software Center or Synaptic"
date: 2012-12-08
forum: Installation &amp; Upgrades
---

### Post by Unterseeboot_234 on 2012-12-08
I run Oneric Ocelot and modified to the Gnome desktop. When I added Synaptic Manager my Software Center never would load after the installation. That was OK. I prefer Synaptic. Now I do not have Synaptic Manager (with the GUI) nor can I invoke synaptic from terminal with sudo synaptic [password]. I get the gui for like 1 second and the program disappears.

Any help?

---

### Post by Unterseeboot_234 on 2012-12-08
What was happening I could see the problem when using Terminal. An echo line would print: "reading package list" and stop at 0% and silently fail.

```
sudo apt-get update
```

fixed the problem. I got my synaptic back.

---

