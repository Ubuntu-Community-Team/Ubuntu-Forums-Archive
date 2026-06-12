---
title: "Software &amp; Updates doesn't see a source when fixing a deprecated key"
date: 2022-08-14
forum: Installation &amp; Upgrades
---

### Post by Paddy Landau on 2022-08-14
When installing SpiderOakONE, its key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), which gives a warning on apt update.

Following [this solution]("https://askubuntu.com/a/1398346/2088"), it all works nicely. However, once the signed-by option is added to the sources file (step 3 in the linked solution), that item disappears from the GUI app Software & Updates (software-properties-gtk) > Other Software.

**Screenshot before step 3:**
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290864&stc=1[/IMG]

**Screenshot after step 3:**
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290863&stc=1[/IMG]

Fortunately, sudo apt update and sudo apt upgrade still work.

What is the problem with software-properties-gtk in this case? Is this a bug that needs to be reported, or is it something that I can fix?

I'm using **Ubuntu 22.04**.

Thank you

---

### Post by &amp;KyT$0P# on 2022-08-14
> **Paddy Landau said:**
>  once the signed-by option is added to the sources file (step 3 in the linked solution), that item disappears from the GUI app Software & Updates (software-properties-gtk) > Other Software.


Same behavior here under Xubuntu 22.04, I have three sources with specified [FONT=Courier New]signed-by[/FONT] (two enabled) and none of them show in software-properties-gtk at all.  I would say try reporting this as a bug.

---

### Post by Paddy Landau on 2022-08-15
Thank you. I have [filed a bug report]("https://bugs.launchpad.net/ubuntu/+bug/1986513").

If you agree with it, please upvote it (the green writing at the top left when you are logged in).

---

