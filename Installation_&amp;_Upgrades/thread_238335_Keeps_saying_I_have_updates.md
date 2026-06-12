---
title: "Keeps saying I have updates"
date: 2006-08-17
forum: Installation &amp; Upgrades
---

### Post by Tamerz on 2006-08-17
In the toolbar it keeps saying I have 5 updates available. If I click it, it asks for my password as usual, then doesn't do anything.

I ran a "sudo apt-get update" to see if that would solve the problem. It didn't find anything to update and finished.

---

### Post by taurus on 2006-08-17
I bet you it's about the new kernel!!!  Open a terminal (Application -> Accessories -> Terminal) and try these...

```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by Tamerz on 2006-08-17
Ahh... I didn't do the "upgrade" just the "update"

It found: imagemagick krb5-user libkadm55 libkrb53 libmagick9

Thanks for the help.

---

