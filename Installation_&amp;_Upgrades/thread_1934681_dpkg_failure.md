---
title: "dpkg failure"
date: 2012-03-02
forum: Installation &amp; Upgrades
---

### Post by prudhvi on 2012-03-02
one of the commands in the post install script is putting in the package in a bad state. That is not so critical task. Is there a way I can just run that command and no matter what happens the dpkg do not fail? In other words, the failure of that command should not put the package in a bad state.

Can somebody please help me with this?

---

### Post by Lasall on 2012-03-02
Hi prudhvi,

do I understand you correctly: You are writing a postinst script and you do not want it break with an error (but have "set -e" enabled)?

Please show your postinst (and say where error occurs).


Kind regards

Lasall

---

