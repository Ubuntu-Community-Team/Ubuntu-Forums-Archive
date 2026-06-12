---
title: "Gksuexec gives &quot;Wrong password&quot; error"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by Teddy-O on 2005-04-10
When I use Gksuexec to open, for example gedit, I get an Error dialog:

"Failed to run gedit: Wrong password." Same type of error for Nautilus. Of course, the password I use is correct.

When I use sudo in a terminal window I get:

"(gedit:26672): GnomeUI-Warning **:While connecting to session manager: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed."

but then gedit opens with root privileges anyway.

My search on line doesn't find anyone else reporting this problem. Am I missing something here?

---

### Post by jdong on 2005-04-10
You should use "gksudo COMMAND" to launch COMMAND with root priveleges. Gksuexec is designed for systems with a root account, and the Ubuntu system (by default ) does not have a root user.

---

### Post by Teddy-O on 2005-04-11
That's interesting, considering that no root account is the default ubuntu configuration, and the gksuexec is the command being called by the "Run as different user" menu item on the Applications>System Tools menu path.

Is that a design bug that should be reported via bugzilla?

---

### Post by jdong on 2005-04-11
Yeah, you definitely should file a bug report for that.

---

### Post by Teddy-O on 2005-04-12
This issue is being addressed via Bugzilla #5623. I guess in the future I'll check Bugzilla first.

---

