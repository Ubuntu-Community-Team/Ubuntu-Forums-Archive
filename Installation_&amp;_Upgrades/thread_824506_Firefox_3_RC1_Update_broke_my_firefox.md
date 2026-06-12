---
title: "Firefox 3 RC1 Update broke my firefox"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by Sh4wn on 2008-06-10
See post below

---

### Post by Sh4wn on 2008-06-10
Little update here. I used the official mozilla launchpad repo:
[https://edge.launchpad.net/~mozillateam/+archive](https://edge.launchpad.net/~mozillateam/+archive)

But now when I try to start Firefox, it gives the message another firefox process is already running, and I should close that process before I can start another.

The problem is, it keeps giving that message, even after a reboot. And I am really sure no firefox process is running.

I get the same error with the official package in the official ubuntu repo.

---

### Post by CA_Warren on 2008-06-10
Couple thoughts:

If Firefox was killed badly at one point its lock file may still be there - delete the files 'lock' and '.parentlock' (you'll need 'view hidden files' on, or to do this in the terminal) in your profile folder (the one under 'Path' in /home/your_user_name/.mozilla/firefox/profiles.ini).

That error message is also the one Firefox gives when it can't find your Firefox profile (friend of mine would get this a lot when he kept his Firefox profile on a separate partition, if the partition wasn't mounted at the time).

I'd suggest taking a look at your /home/your_user_name/.mozilla/firefox/profiles.ini and checking that the Path in there goes to a real profile folder. Alternatively (if you've got your bookmarks, passwords, etc. properly backed up), just delete said profiles.ini file. It should then create a new profile for you when you next start Firefox, letting you in.


Mozilla's [official treatise]("http://kb.mozillazine.org/Profile_in_use") on this issue.

---

### Post by asac on 2008-06-10
if you are sure that ffox isnt running anymore, you can remove the "lock" and "parentlock" files in your $HOME/.mozilla directory.

Remember, to be safe backup your $HOME/.mozilla directory before touching it manually.

---

