---
title: "Update Manager isn't working?"
date: 2012-01-14
forum: Installation &amp; Upgrades
---

### Post by BlueSunshine on 2012-01-14
This came up after trying to install updates through Update Manager, and when it asked for a password, I just pressed "enter". Any help?

---

### Post by bluexrider on 2012-01-14
Something killed the Daemon. Log out or better yet restart the computer and try again.

If you are unable to utilize the software manager at that time please post back the result of this:

Using the terminal Ctrl+Alt+T
```

sudo apt-get update
```

---

### Post by BlueSunshine on 2012-01-14
Hmm... didn't seem to work since it asked for my password. I typed it in and it said "Sorry, try again". I just typed in "terminal" into the Dash Home since my ctrl and alt keys don't work.

---

### Post by bluexrider on 2012-01-14
Try this should work:


sudo apt-get clean

sudo cd /var/lib/apt

cd /var/lib/apt ls

sudo mv lists lists.old

sudo mkdir -p lists/partial

sudo apt-get clean

sudo apt-get update

---

