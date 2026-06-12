---
title: "Restart Gutsy upgrade after failure?"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by SDraconis on 2007-10-22
Old Gentoo user here trying out Ubuntu for the first time.  Just tried upgrading my testing Ubuntu Server machine from Fiesty to Gutsy, and then had a failure in the middle (the menu asking me what I wanted to do about my existing php.ini wouldn't let me select anything.  Arrow keys instead cycled through previous terminal commands, which appeared in the middle of the screen).  I killed off the upgrade and dpkg processes.  How do I restart the upgrade?

Re-running sudo do-release-upgrade states that there's no upgrade available.  Trying to install the incomplete packages from aptitude fails as well.  Note that the machine is currently in a remote location accessed via SSH, so CD installs/full reinstalls are not an option (though I'd say Ubuntu has a long way to go if there is no way to restart an upgrade without resorting to that).

---

### Post by Sef on 2007-10-22
Have you tried ```
sudo --configure -a
```?

Not sure if it will work, just a thought.

---

### Post by SDraconis on 2007-10-22
Is there supposed to be a command between the "sudo" and the "--configure"?

EDIT: Nevermind, figured out that it was meant to be for dpkg.  Realized that the whiptail process was still running and stopping me from installing anything, so killed that and finished off that part of the install (php).  Dunno if I have a half-upgraded system or not though still...

---

