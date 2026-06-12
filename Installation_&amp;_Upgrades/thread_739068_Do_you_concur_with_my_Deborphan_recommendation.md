---
title: "Do you concur with my Deborphan recommendation?"
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by luvit on 2008-03-29
As I learn Ubuntu I would like to keep it clean. I do know Deborphan can give false positives.
Recently i installed a few media players trying to troubleshoot their failure points. My problem could have been resolved without installing more players.
[LIST]
[*]Deborphan lists these two packages:[LIST]
[*]gstreamer0.10-pitfdll (252KB)[/LIST][LIST]
[*] libdb4.3 (972KB)[/LIST]
[*]Do you concur? ;)[/LIST]

---

### Post by bwhite82 on 2008-03-29
Deborphan simply removes packages that have no packages depending on them. That does not mean that these libraries may not be of some use to some already existing packages. With that said, the only way to find out is to let it remove them and note errors if found. Another tool that you may find useful is:

localepurge

-Cheers

---

