---
title: "ksh doesn't works after upgrade from Ubuntu 18 to Ubuntu 20"
date: 2022-09-01
forum: Installation &amp; Upgrades
---

### Post by Hans_van_Leeuwen on 2022-09-01
With Ubuntu 18, a running ksh and VISUAL=vi I could repeat the former command with Esc k
After the upgrade to Ubuntu 20, a running ksh and VISUAL=vi the Esc k doesn't give me the former command.

How can I get that useful functionality of ksh back?

---

### Post by &amp;KyT$0P# on 2022-09-01
It works for me in 22.04.  Are you able to upgrade to 22.04?

---

### Post by Hans_van_Leeuwen on 2022-09-02
My $HOME/.sh_history file has a size of 83498 bytes.
The last command in the $HOME/.sh_history file was "do-release-update". So the upgrade from Ubuntu18 to Ubuntu 20.
The ksh doesn't update the $HOME/.sh_history file anymore.
I removed the $HOME/.sh_history file and the ksh created a new and empty $HOME/.sh_history file.
Now the ksh update again the $HOME/.sh_history file, the ESC k works again.
The problem is solved.
But I don't understand the logic of the problem and solution.

---

