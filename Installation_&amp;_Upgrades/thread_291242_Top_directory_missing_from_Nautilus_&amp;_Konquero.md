---
title: "Top directory missing from Nautilus &amp; Konqueror"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by BobBlum on 2006-11-02
After upgrading from Dapper to Edgy (final release), the Nautilus file browser will not show the top directory ("/") unless I click on "Show Hidden Files."  This is also true in Konqueror when I use the KDE desktop.  In both cases, the side panel of the file manager will not show the full directory tree.  I constantly use the file managers and this problem greatly hampers my flexibility.  Can anyone help?  Thank you in advance.

---

### Post by Zeroangel on 2006-11-03
That's because all of the files in the top directory are hidden by the .hidden file in the top folder. You can get around that permanently by renaming that file:```
sudo mv /.hidden /.hidden-bak
```

---

### Post by BobBlum on 2006-11-04
Many thanks.  That solved the problem perfectly.

---

