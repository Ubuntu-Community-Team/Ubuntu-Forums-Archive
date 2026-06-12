---
title: "After Hardy upgrade, svn problems."
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by pdaoust on 2008-05-05
Hi there. I'm using a local SVN setup for version control for a program I'm writing. After upgrade to Hoary, my working directory doesn't seem to be managed by SVN anymore:

```
svn: Commit failed (details follow):
svn: '/var/www/localmotive/market/calculateStars.php' is not under version control
```

I can see a .svn directory under /var/www/localmotive/market, and the main repository still exists in ~/svn, where I set it up... so what could the problem be? I did notice that the upgrade uninstalled svn, so I had to reinstall it, but that wouldn't have deleted my repository or .svn directories, would it?

---

### Post by lemming465 on 2008-05-10
I wouldn't expect a reinstall to affect a repository or working copy, no.  However, access to the repository might be an issue, depending on how you are serving it.

What does *svn info* say about the working copy, and what does *svn ls* do with the repository URL?

---

