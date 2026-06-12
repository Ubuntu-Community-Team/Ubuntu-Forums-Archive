---
title: "Wubi install from 8.10 to 9.04?"
date: 2008-11-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dakkar9999 on 2008-11-23
I tried to upgrade a Wubi install to 9.04.  The whole process went as usual, but at reboot, it is still 8.10 that is loaded.

Any suggestion?

---

### Post by MaX on 2008-11-23
Wait until 9.04 is released?

---

### Post by Eclipse. on 2008-11-23
> **MaX said:**
> Wait until 9.04 is released?

Answering a question with a question lol.

I have known people who have upgradded wubi from 7.10 to 8.04 so it must be possible.

Try the old debian method for upgrading (replace the intrepid to jaunty in your sources.list file) then run "sudo apt-get update" "sudo apt-get upgrade"

---

### Post by Gina on 2008-11-23
A bit later I shall be looking to test Wubi 9.04 development.  I believe 8.10 had testing available before the Ubuntu 8.10 release.

---

### Post by dakkar9999 on 2008-11-23
Yes, it is possible.  I have upgraded the 8.04 to 8.10 wubi install.  And the whole install process for 9.04 goes correctly, it is just that at reboot, it does not show up.

---

### Post by dakkar9999 on 2008-11-23
Well, upon checking in the /etc/lsb-release file, it shows version 9.04, so I guess i'm ok.  It's just that at boot it still shows the kernel for 8.10.

Oh well,  I guess it's alright!

Thanks!

---

### Post by jnw222 on 2008-12-06
is there currently a wubio installer for (9.04)
wanting to test it

---

### Post by ShirishAg75 on 2008-12-06
what do you mean it doesn't show up, can you be a bit more specific? Where it doesn't show up, at the boot menu or somewhere else? Give more info. please.

---

