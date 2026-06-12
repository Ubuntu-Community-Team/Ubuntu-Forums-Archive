---
title: "Uninstall Snap Opera?"
date: 2020-03-31
forum: Installation &amp; Upgrades
---

### Post by Daveski17 on 2020-03-31
Hello,

How do I uninstall the snap version of Opera using the Terminal (Ubuntu 16.04 LTS)?

Thanks

---

### Post by deadflowr on 2020-03-31
```
snap remove snap-package-name
```
replace the snap-package-name with the name of the snap.

If unclear what the snap name is use 
```
snap list
```
to see.
```
snap help
```
for more.

Snap command line doesn't require sudo to run, It's built with the ability to run elevated when required.
A password dialog box should show when you want to make changes like install or remove.
If you run the remove command as posted above and no password box shows, you can run the command with sudo.
But running with sudo is only a quick fix fallback, as it should open the dialog box automatically.

And if you want a full removal you might want to remove the folder created by the snap package inside your home folder's snap folder.
This is the user's configuration folder for snap packages.

---

### Post by Daveski17 on 2020-03-31
> **deadflowr said:**
> ```
snap remove snap-package-name
```
replace the snap-package-name with the name of the snap.

If unclear what the snap name is use 
```
snap list
```
to see.
```
snap help
```
for more.

Snap command line doesn't require sudo to run, It's built with the ability to run elevated when required.
A password dialog box should show when you want to make changes like install or remove.
If you run the remove command as posted above and no password box shows, you can run the command with sudo.
But running with sudo is only a quick fix fallback, as it should open the dialog box automatically.

And if you want a full removal you might want to remove the folder created by the snap package inside your home folder's snap folder.
This is the user's configuration folder for snap packages.


OK, great thanks.

---

