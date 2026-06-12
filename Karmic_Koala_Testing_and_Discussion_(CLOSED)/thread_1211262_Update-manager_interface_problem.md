---
title: "Update-manager interface problem"
date: 2009-07-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Wise Ferret on 2009-07-12
After last update to update-manager, a problem arose. Downloading package information works fine; but after reading the package information downloaded it refuses to release the mouse cursor (it keeps spinning forever). If updates were found they are shown in the window, but they are grayed out so I cannot browse them, read descriptions etc. The buttons (Install Updates, Settings, Close) are active and can be pressed, even though the cursor tells me to wait.
The workaround is to use update manager to download package information, close it down, and then restart it in order to review the updates before installing them.

Is there anybody else with this problem?

---

### Post by morryis on 2009-07-12
Confirmed!

---

### Post by ranch hand on 2009-07-12
I find this post really interesting.

I am on 9.10A2-64 clean install updated daily from the time of release.  The only update-manager related thing installed is update-manager-core.

How did you get this?

---

### Post by morryis on 2009-07-12
Since [this update]("https://lists.ubuntu.com/archives/karmic-changes/2009-July/003645.html") 4 days ago:
update-manager (1:0.124.1) to 1:0.124.2
update-manager-core (1:0.124.1) to 1:0.124.2

---

### Post by deathsshadow77 on 2009-07-12
I have it too

---

### Post by meeples on 2009-07-12
i get a op up saying update-manager closed unexpectedly. but the window stays openand everything is grayed out.

---

### Post by Wise Ferret on 2009-07-12
Bug reported: [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/398532](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/398532)

Comments confirming the bug are welcome.

---

### Post by ghindo on 2009-07-12
> **Wise Ferret said:**
> Comments confirming the bug are welcome.Instead of creating a ["me-too storm"]("http://www2.bryceharrington.org:8080/drupal/me-too-storms") by commenting, it's preferable to click "This bug doesn't affect me (change)." :popcorn:

---

### Post by Wise Ferret on 2009-07-12
That is also true O:)

---

### Post by wayne_cat on 2009-07-12
Me too :biggrin:

a little python problem???

```
root@macbook:/$ update-manager 
/usr/lib/python2.6/dist-packages/UpdateManager/SimpleGtkbuilderApp.py:36: RuntimeWarning: missing handler 'on_button_fetch_cancel_clicked'
  self.builder.connect_signals(self)
/usr/lib/python2.6/dist-packages/UpdateManager/SimpleGtkbuilderApp.py:36: RuntimeWarning: missing handler 'on_expander_details_activate'
  self.builder.connect_signals(self)
/usr/lib/python2.6/dist-packages/DistUpgrade/DistUpgradeCache.py:120: DeprecationWarning: Accessed deprecated property Package.candidateDownloadable, please see the Version class for alternatives.
  if (not pkg.candidateDownloadable and
/usr/lib/python2.6/dist-packages/UpdateManager/Core/UpdateList.py:82: DeprecationWarning: Accessed deprecated property Package.candidateOrigin, please see the Version class for alternatives.
  if pkg.candidateOrigin == None:
/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py:757: DeprecationWarning: Accessed deprecated property Package.summary, please see the Version class for alternatives.
  summary = xml.sax.saxutils.escape(pkg.summary)
/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py:760: DeprecationWarning: Accessed deprecated property Package.packageSize, please see the Version class for alternatives.
  size = _("(Size: %s)") % humanize_size(pkg.packageSize)
/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py:761: DeprecationWarning: Accessed deprecated property Package.installedVersion, please see the Version class for alternatives.
  if pkg.installedVersion != None:
/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py:763: DeprecationWarning: Accessed deprecated property Package.installedVersion, please see the Version class for alternatives.
  {"old_version" : pkg.installedVersion,
/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py:764: DeprecationWarning: Accessed deprecated property Package.candidateVersion, please see the Version class for alternatives.
  "new_version" : pkg.candidateVersion}

```

---

### Post by JohnJackson on 2009-07-13
Just close update manager, and open it again. That works for me anyway.

---

### Post by zika on 2009-07-14
Aptitude stopped cleaning behind itself. I have option that packages should be erased after install but they stay in folder /var/cache/apt/archives ...

---

### Post by ronacc on 2009-07-14
> **JohnJackson said:**
> Just close update manager, and open it again. That works for me anyway.

it works for me too .

---

