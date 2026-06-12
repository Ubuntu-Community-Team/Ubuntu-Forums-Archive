---
title: "Update Manager hangs on 'Updating cache'"
date: 2009-09-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by JCoster on 2009-09-26
Recently when I run gksu update-manager and check for updates on Karmic it pops-up saying 'Updating cache.  Waiting for other software manager...'  It stays like this until I press 'Cancel' at which point it tells me that it 'Failed to download repository information.  Check your Internet connection.'

However, I can still run 'sudo apt-get update', 'sudo apt-get upgrade' fine and I'm connected to the internet...

What's going on?

---

### Post by nhasian on 2009-09-26
my update-manager hasnt worked since it was updated.  It downloads the list of new updates, but does nothing when i tell it to install the updates.  i've just been using apt-get upgrade.

---

### Post by zekopeko on 2009-09-26
> **JCoster said:**
> Recently when I run gksu update-manager and check for updates on Karmic it pops-up saying 'Updating cache.  Waiting for other software manager...'  It stays like this until I press 'Cancel' at which point it tells me that it 'Failed to download repository information.  Check your Internet connection.'

However, I can still run 'sudo apt-get update', 'sudo apt-get upgrade' fine and I'm connected to the internet...

What's going on?

Update-manager was ported to use aptdaemon and by extension policykit. Don't run it with gksudo. Just run it as a normal user since you can now check for new updates without inputing password.
If you click install only then will you be prompted for password.

---

### Post by philinux on 2009-09-26
The aptdaemon has a few bugs outstanding.

[https://bugs.launchpad.net/bugs/+bugs?field.searchtext=aptdaemon&search=Search+Bug+Reports&field.scope=all&field.scope.target=](https://bugs.launchpad.net/bugs/+bugs?field.searchtext=aptdaemon&search=Search+Bug+Reports&field.scope=all&field.scope.target=)

---

### Post by JCoster on 2009-09-26
> **zekopeko said:**
> Update-manager was ported to use aptdaemon and by extension policykit. Don't run it with gksudo. Just run it as a normal user since you can now check for new updates without inputing password.
If you click install only then will you be prompted for password.

Brilliant, thanks.  That solved it!

---

