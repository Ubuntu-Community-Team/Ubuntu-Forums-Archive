---
title: "Need Help with Ubuntu 10.10"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by abhjos on 2010-10-11
Hello Friends,
 
The new Ubuntu 10.10 is out and I would like to upgrade from 10.4 to 10.10. When I go to my Update Manager I cannot find 10.10 for Upgrade, how can I update to the new and latest version, please help me out with this regards.
 
Thank you,
abhay

---

### Post by lechien73 on 2010-10-11
Try going to **System > Administration > Update Manager**. Click on **Settings**, and under the **Release Upgrade** heading, make sure that it is set to **Normal releases**, rather than **Long term support releases only**.

When you have changed this, close the Settings window and click the **Check** button again. You should now be prompted for the upgrade.

On one of my machines Update Manager didn't show the available upgrade so, after confirming the above settings, I opened a terminal window and typed:

```
sudo do-release-upgrade -d
```

This worked fine also.

---

### Post by abhjos on 2010-10-11
great, so I will the get the complete software withoug any Bugs and full support from Ubuntu right.

---

### Post by abhjos on 2010-10-11
Any more help please. how is the new 10.10 heard that there are lots of Bugs and system is freezing also.

---

### Post by lechien73 on 2010-10-11
Well...you'll get the complete upgrade to 10.10, performed the recommended way.

Bugs may become evident, depending on what other packages you have installed. The cleanest way would be to back up your home folder and installed package lists, and then do a completely clean install. Even then, there are no guarantees as to bug-free operation. These forums probably wouldn't exist if there were no bugs ;)

As for support, if you mean updates and so on, then yes. Otherwise, technical support is available from the usual places: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)

---

### Post by abhjos on 2010-10-11
If I install this way will I get the regular updates?

---

