---
title: "Just updated and now Firefox won't run anymore."
date: 2010-03-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Mike_IronFist on 2010-03-26
I just installed the Lucid beta and got the latest updates. Now Firefox will not run at all. It spends a little while trying to open when I select it from the menu, then it just doesn't open at all. No process appears in the system monitor either.

What do I do to get Firefox up and running again? I still have backup browsers like Midori, but I'd prefer to be using Firefox while testing Lucid.

---

### Post by dino99 on 2010-03-26
Is it a clean install ? If not, remove all the plugins first.
You still have logs to find errors, but into console:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

sudo dpkg-reconfigure firefox

if errors are still there, watch logs. In case you can remove/purge firefox then reinstall it.

---

### Post by Mike_IronFist on 2010-03-26
> **dino99 said:**
> Is it a clean install ? If not, remove all the plugins first.
You still have logs to find errors, but into console:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

sudo dpkg-reconfigure firefox

if errors are still there, watch logs. In case you can remove/purge firefox then reinstall it.

I just deleted my settings folder and now everything is working smoothly. Thanks for your help!

---

### Post by Mike_IronFist on 2010-03-26
> **dino99 said:**
> Is it a clean install ? If not, remove all the plugins first.
You still have logs to find errors, but into console:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

sudo dpkg-reconfigure firefox

if errors are still there, watch logs. In case you can remove/purge firefox then reinstall it.

Ugh.. Now no matter what, I can open Firefox ONCE after deleting its config files from ~/.mozilla ,  but once I close it, it won't open again until I do this once more! I'm switching to chromium until this gets patched up.

---

### Post by Nickedynick on 2010-03-26
I had the [same problem]("http://ubuntuforums.org/showthread.php?t=1437106") - eventually someone posted that removing Prism fixes it (if you have it installed).

---

### Post by Mike_IronFist on 2010-03-26
> **Nickedynick said:**
> I had the [same problem]("http://ubuntuforums.org/showthread.php?t=1437106") - eventually someone posted that removing Prism fixes it (if you have it installed).

Wow. That's frustrating. So Prism interferes with Firefox... I love Prism (especially when combined with AllTray.. I use it for stuff like Grooveshark) but I guess it has to go until this bug is fixed.

Thanks for your help! It worked flawlessly!

---

### Post by Nickedynick on 2010-03-26
No worries :) There is a Prism add-on for Firefox that seems to work identically available. Think I posted the link in the other thread.

---

