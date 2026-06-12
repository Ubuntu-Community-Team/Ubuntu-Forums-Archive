---
title: "Getting Error when attempting to perform Updates"
date: 2022-01-10
forum: Installation &amp; Upgrades
---

### Post by brian.modlin on 2022-01-10
Hello All!  I am new to Ubuntu and will never go back to Windows!!  I am getting this error when attempting to update via cli or gui.  Can someone please help?  See attached screenshot.

Thank you so much!

---

### Post by MAFoElffen on 2022-01-11
If you temporarily go to Activities, type "Software and Updates". Select it. "Other Software" Tab, uncheck the checkbox for winehq.org... then close...
```

sudo apt update
sudo apt upgrade

```
That should disable the third party sources for Wine, and upgrade everything except that repo...

After successfully upgrading everything else, go back and re-add WineHQ back to the sources, by going back and rechecking that checkbox...

The try to refresh your keys from winehq via
```

wget -O - https://dl.winehq.org/wine-builds/winehq.key | sudo apt-key add 

```
Try to do 
```

sudo apt update

```
if it still says the keys are invalid, try again to refresh your keys in a couple days... The repo keys have an expiration date on them. Sometimes it takes a few days for them to figure that out. But that shouldn;t prevent you from upgrading everything else, with the fix I gave you above...

---

