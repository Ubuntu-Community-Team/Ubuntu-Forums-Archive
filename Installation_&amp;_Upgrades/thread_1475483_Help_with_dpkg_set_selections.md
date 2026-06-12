---
title: "Help with dpkg set selections"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by JayPeters on 2010-05-06
I was having problems with the upgrade from 9.10 to 10.4--mainly that Ubuntu would not shut down properly.  The only way I could shutdown was to press the power button.

I thought I'd try a clean install and use dpkg to get the list of installed apps on my system before attempting the clean installation of 10.4.

I used ```
sudo dpkg --get--selections > installed_apps
``` to backup the list of installed applications.  I saved the list and emailed it to myself.

The clean install went fine, and my system now shuts down properly; however, I can't update my installed application list with the dpkg command.

When I run 

```
sudo dpkg --set-selections < installed_apps
```I get the following error message:

```
dpkg: unexpected data after package and selection at line 1
```Can anyone help me to load my list of applications from my previous installation?

Thank you.

---

### Post by smitty825 on 2010-05-09
I'm not an expert in this, however, I think you need to clear the selections before you set them:

```
sudo dpkg --clear-selections
sudo dpkg --set-selections < packages
```

(Though, I'm assuming you didn't accidentally make the same mistake on your computer that you made on the first line (--get--selections instead of --get-selections)  

Good luck!

---

