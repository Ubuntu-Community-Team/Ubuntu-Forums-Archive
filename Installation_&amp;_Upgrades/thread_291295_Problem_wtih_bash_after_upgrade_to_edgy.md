---
title: "Problem wtih bash after upgrade to edgy"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by wijet on 2006-11-02
I have update my kubuntu to 6.10 (apt-get dist-upgrade)
Now when I run new colsole I get this message

```

bash: enable: bash: not a shell builtin
bash: enable: completion: not a shell builtin
bash: enable: in: not a shell builtin
bash: enable: interactive: not a shell builtin
bash: enable: shells: not a shell builtin

```

How I can fix this?

---

### Post by seatea on 2006-11-02
If you can open Synaptic,I don't use KDE so use the equivalent program for  your  setup, try to reinstall bash.

---

### Post by Brian_X7 on 2006-11-02
I don't have that problem, but when I try and compile software, the configure scripts usually use #!/bin/sh  and when a function is declared in the script, it croaks.  If I change the line to #!/bin/bash  everything works.  There is something in /bin/sh but I don't know what the problem is.

Brian

---

### Post by jeremytaylor on 2006-11-02
The problem is that /bin/sh is now linked to dash instead of bash. This causes all sorts of problems as dash is a much simper shell than bash. You can either keep changing your shell scripts to point to /bin/bash or change the link for /bin/sh.I've done the latter and have yet to notice any unpleasant side effects but I'm no expert.

Jeremy

---

### Post by wijet on 2006-11-02
I found! When I replace  /etc/bash.bashrc with /etc/bash.bashrc.dpkg-old everything back to normal. :D

---

### Post by wsams on 2008-03-17
Check your /etc/bash.bashrc file for a line that begins with "enable" and is not preceded by a pound sign.

For some reason that happened to me. It was next to the bash completion portion. Just add a pound sign at the beginning to comment it out.

---

