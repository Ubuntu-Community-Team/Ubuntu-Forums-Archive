---
title: "Add/Remove Applications: Problems"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by spdorsey on 2007-11-21
Hello.

  I have a new install of Ubuntu on an IBM Thinkpad T41. It installed fine, and I am able to connect to the interweb via FF. 

  When I try to add an app using the "Add/Remove Applications" app, I click a checkbox next to (for example) "Ubuntu Themes for Firefox", and the app asks for an admin password. After I input the password, the app tells me "The List of Applications is not Available". I click the "Refresh" button, the app tries to download 6 files, and nothing at all happens.

  What am I doing wrong here?

Thanks

---------------------S

---

### Post by mouseboyx on 2007-11-21
post the contents of your /etc/apt/sources.list file

press alt f2 and type gksu gedit /etc/apt/sources.list

copy and paste everything into here

---

### Post by zvacet on 2007-11-21
system>administration>software sources>chek all boxes in first tab and in updates tab<reload

---

### Post by Crowenor on 2007-12-27
Thanks:guitar:

---

