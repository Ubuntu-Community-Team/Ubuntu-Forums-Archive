---
title: "emacs window changes size after upgrade to kubuntu 10.4"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by eugenz on 2010-06-02
Hello,

After I have upgraded to KUbuntu 10.4, my GNU Emacs has the following very strange behavior:
whenever the text in mini-buffer changes (for instance by running a command) also the size of the Emacs window changes! Actually it shrinks towards the top of the screen. Hence every now and then, depending on the number of commands I execute, I have to manually resize my Emacs window to its initial size, which is of course annoying.

Does anyone have any suggestion in order to repair this?

My Emacs version is:
GNU Emacs 23.1.1 (x86_64-pc-linux-gnu, GTK+ Version 2.20.0)
of 2010-03-29 on yellow, modified by Debian

Thanks,
Eugen

PS. Is this the right forum to ask this question?

---

### Post by fodon on 2010-06-04
I noticed the same problem. I'd like to hear about this if there is a fix too.

---

### Post by paulrosee on 2010-07-25
I also had this behaviour. An Upgrade to Emacs 23.2.1 fixed it for me. I hope this helps you.

---

### Post by eugenz on 2010-08-09
It seems that using the emacs-snapshot package (which currently provides version 23.1.50 of emacs) also fixes the problem.

---

