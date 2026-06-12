---
title: "firefox fails silently"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ffi on 2010-03-30
Firefox won't run at all. Deleting my profile allows me to run it once but after it will fail again. I found some similar threads which said advised to uninstall certain extensions but I have none of those installed

---

### Post by Aearenda on 2010-03-30
Happening for me too. It will start in safe mode (Alt/F2, type firefox -safe-mode<enter>), and then it will start in normal mode after that.

---

### Post by lovinglinux on 2010-03-30
Try to remove Prism if you have it and delete compatibility.ini file from FF profile.

---

### Post by Aearenda on 2010-03-30
I found that I still had the Google Gears extension installed, after trying and failing to get Google Calendar to work offline. With that extension disabled, Firefox starts normally.

For the record, I don't have Prism installed, though I probably tried that too in the past.

---

### Post by ffi on 2010-03-30
I don't have any extensions nor prism installed, I tried running in safe mode but will crash and nor restart, I tried deleting compatibility.ini

---

### Post by lovinglinux on 2010-03-30
> **ffi said:**
> I don't have any extensions nor prism installed

Then reinstall xulrunner.

Also check [COLOR="Sienna"]**Troubleshooting**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by ffi on 2010-03-30
I deleted my .mozilla already it works once

---

### Post by ffi on 2010-03-31
no one have any clues?

---

### Post by Aearenda on 2010-03-31
Did you do what lovinglinux suggested in post 6?
> Then reinstall xulrunner.

Also check Troubleshooting section of Firefox optimization and troubleshooting thread.

---

### Post by mdurham on 2010-03-31
post #10 from [here]("http://ubuntuforums.org/showthread.php?t=1407753") fixed it for me.

---

