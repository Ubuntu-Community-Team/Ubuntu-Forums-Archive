---
title: "Release signed by unknown key"
date: 2015-06-19
forum: Installation &amp; Upgrades
---

### Post by john163 on 2015-06-19
[FONT=Lucida Grande, Trebuchet MS, Verdana, Helvetica, Arial, sans-serif][COLOR=#333333]I created a standalone local repo and signed the release file with my GPG key.  I'm getting an error about "Release signed by unknown key".  I tried [/COLOR][/FONT][COLOR=#333333][FONT=Lucida Grande]'sudo apt-key add ~/.gnupg/pubring.gpg' (I guessed, adding other keys didn't work, and that gave me an "OK") but that didn't work.[/FONT][/COLOR]

---

### Post by NoWayWin8 on 2015-06-19
```
$ gpg -a --export KEYID | sudo apt-key add -
``` (change "KEYID" to the your key's ID)

---

### Post by john163 on 2015-06-24
> **NoWayWin8 said:**
> ```
$ gpg -a --export KEYID | sudo apt-key add -
``` (change "KEYID" to the your key's ID)

That worked for apt, but xen-tools is still complaining about an unknown key.

---

