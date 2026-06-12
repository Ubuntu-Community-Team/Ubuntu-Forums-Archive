---
title: "Missing &quot;Passwords &amp; Encryption Keys&quot; in Accessories menu"
date: 2013-07-01
forum: Installation &amp; Upgrades
---

### Post by Scooby-2 on 2013-07-01
Ubuntu One had stopped connecting on my PC which ran Xubu 10.04 and Xfce - I just upgraded to 12.04 and it now crashes every time I try to start it. I want to try to uninstall and reinstall it and I'm following [this]("https://answers.launchpad.net/ubuntuone-client/+faq/778") procedure but I don't have a Passwords & Encryption Keys entry under accessories.

This is only one of many problems that I now have, as the upgrade itself introduced more.

[ATTACH=CONFIG]244299[/ATTACH] 

Is it possible to re-add the missing menu item (which was missing under 10.04 too), or to perform step 6 of the procedure another way?

Incidentally I am running Xubu 12.04 with gnome desktop on a laptop with Ubuntu One - with no problems. However, it too is missing the Passwords and Encryption Keys menu item!

---

### Post by Scooby-2 on 2013-07-02
With thanks to [**Irihapeti**]("http://ubuntuforums.org/member.php?u=346442") who advised that seahorse is the program that's missing. A quick

```
sudo apt-get install seahorse
```

and it can now be found under the Settings menu.

This solves this particular problem so I am closing this thread.

---

