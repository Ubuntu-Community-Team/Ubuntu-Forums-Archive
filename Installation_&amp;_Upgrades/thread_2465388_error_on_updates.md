---
title: "error on updates"
date: 2021-07-31
forum: Installation &amp; Upgrades
---

### Post by sparky3332 on 2021-07-31
I'm running 18.04. When I click on Software Updater, I get this error:

**Failed to download repository information.**
Check your internet connection.

There is nothing wrong with my internet and when I click OK, the download
and install of the updates happen normally.

Any ideas?

---

### Post by TheFu on 2021-07-31
If you wait 3 minutes after login, does the same issue happen?
What is your network setup. Is it for the entire system or does it wait until a user logs in and a user-session is created?
Wifi or wired connection?

---

### Post by Impavidus on 2021-07-31
It failed to check at least one repository. Other repositories may be OK.

What do you get from```
sudo apt update
```?

---

### Post by sparky3332 on 2021-07-31
"3 minutes after login"  
Login where?
Network is for entire system.
Wired connection (from a router)

---

### Post by QIII on 2021-07-31
Please see Impavidus' post and post the results.  You may have a PPA that has not been updated, a PPA may have been removed by the maintainer, the mirror you are using may be in the process of being updated, or any number of things.

---

### Post by sparky3332 on 2021-07-31
sudo apt upgrade showed 
1 package can be upgraded. Run 'apt list --upgradable' to see it.

Ran apt list --upgradable  and it showed 3 drivers could be upgraded:
ubuntu-drivers-common

Ran sudo apt update ubuntu-drivers-common
and it upgraded the drivers.

Still get the error when I run Software Updater though...

---

### Post by QIII on 2021-07-31
Would you please include the output -- verbatim and in its entirety -- between code tags?

---

### Post by sparky3332 on 2021-07-31
Sorry Qlll....
I'm not sure what code tags are.

---

### Post by QIII on 2021-07-31
1. If you are using the "Reply to Thread" button, please type or paste your text, highlight the text and use the # button in the text box header. Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

This will preserve the formatting and make your post easier to read.

---

### Post by sparky3332 on 2021-07-31
Well...the output from the sudo apt upgrade command is totally different now.

Same with the apt list --upgradable -a command.

It just says Listing... Done

This is getting way over my head.  I think I'll just live with the error.

Much thanks for trying to help!!

---

### Post by sparky3332 on 2021-07-31
**Problem Fixed!**

In the Software & Updates window, under Other Software, I unchecked the two ppa.launchpad.net...grub-customizer
boxes and the repo.skype.com box and the Updater runs fine now...no error.

Not sure why these were checked, because I don't do dual boot or use skype.

How can I close this thread?

-tom

---

### Post by QIII on 2021-07-31
Upper right Thread Tools > Mark this thread as solved.

By the way, had you copied the entirety of the output rather than just a line or two, we'd have seen a message indicating what you found.  Using the command line and its output provides a great deal of information that might not be exposed using a DE.  It also works whatever the DE.  For reasons such as these, we often ask users to help us diagnose issues by using the command line.  And *all* the information displayed is important.

---

