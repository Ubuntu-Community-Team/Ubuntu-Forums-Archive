---
title: "&quot;Successfully&quot; installed 16.04, but sort of buggy"
date: 2017-06-11
forum: Installation &amp; Upgrades
---

### Post by Franknj229 on 2017-06-11
I recently installed Ubuntu 16.04 on my desktop computer, completely converting from Windows (not dual boot, VM, alongside, etc.), and initially it seemed to work perfectly.  I made some very, very minor changes, such as changing the desktop wallpaper, auto-hid the launcher, and turned off the password requirement after lock screen.  That was day one.

Now, on day two, when I booted up, the wallpaper is back to the default, the launcher won't auto-hide, and most concerning is that the system won't let me turn off the password requirement or even turn off the lock screen option.  The system also seems to be a bit sluggish.  The screen scrolling lags slightly behind my scroll wheel scrolling.

Are there updates I'm supposed to run after installing?  Anything else you would do after installing to optimize the system?

Edit: When I type sudo apt-get update in terminal, I get "unable to change to root gid: Operation not permitted".

Thank you!

-Frank

---

### Post by Franknj229 on 2017-06-11
Hmm.... I clicked the shutdown icon in the top right corner of my desktop, and under "Lock", it shows "Guest Session" and "Frank".  It was on Guest Session, so I clicked "Frank", and it's back to what I was using yesterday.  Not sure why it defaulted to Guest Session today, or if I inadvertently switched to the Guest Session.

The Guest Session isn't a VM, is it?  It's just a way to let a literal guest use my computer?

---

### Post by howefield on 2017-06-11
> **Franknj229 said:**
> Are there updates I'm supposed to run after installing?  Anything else you would do after installing to optimize the system?

First thing would generally be to run updates and make sure that your installed packages are all up to date either with the Software Updater or via the terminal with..

```
sudo apt update
```
and 
```
sudo apt upgrade
```

> **Franknj229 said:**
> The Guest Session isn't a VM, is it?  It's just a way to let a literal guest use my computer?

That's correct, it is a temporary account that a guest could use on your computer, and is reset after logging out. Something as simple as inadvertently pressing the down arrow key and pressing enter from the login screen would put you into the guest account.

---

