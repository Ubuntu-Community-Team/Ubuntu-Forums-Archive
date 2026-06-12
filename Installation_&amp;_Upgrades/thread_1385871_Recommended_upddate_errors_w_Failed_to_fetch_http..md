---
title: "Recommended upddate errors: w: Failed to fetch http://.."
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by Stoneface on 2010-01-20
Update manager indicated I could update several Firefox and Firefox related items. I started the update and got these errors:

```
W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox-3.5-branding_3.5.6+nobinonly-0ubuntu0.9.10.1_i386.deb
  404  Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.1/xulrunner-1.9.1-gnome-support_1.9.1.6+nobinonly-0ubuntu0.9.10.1_i386.deb
  404  Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.1/xulrunner-1.9.1_1.9.1.6+nobinonly-0ubuntu0.9.10.1_i386.deb
  404  Not Found


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox-3.5-gnome-support_3.5.6+nobinonly-0ubuntu0.9.10.1_i386.deb
  404  Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox-3.5_3.5.6+nobinonly-0ubuntu0.9.10.1_i386.deb
  404  Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox_3.5.6+nobinonly-0ubuntu0.9.10.1_all.deb
  404  Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox-gnome-support_3.5.6+nobinonly-0ubuntu0.9.10.1_all.deb
  404  Not Found

```
Are my update sources outdated or is the site down?

---

### Post by Stoneface on 2010-01-20
Never mind. Had to update the repositories by doing a check in the update manager. Downloading updates now :-)

---

### Post by dshimer on 2010-02-27
> **Stoneface said:**
> Never mind. Had to update the repositories by doing a check in the update manager. Downloading updates now :-)

Could you explain this procedure?

---

### Post by Stoneface on 2010-02-28
Just clicking on check button - next the install updates button -  in the update manager screen even though updates were listed already refreshed the update list with paths to the latest download urls. Et voila a new list of updatable items was fetched which I could download and this time all urls to the new packages were correct. Hope this helps

---

