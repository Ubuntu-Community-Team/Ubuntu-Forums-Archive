---
title: "Issue with accidentally install 13.10 deps - I Have Made a Huge Mistake"
date: 2013-10-01
forum: Installation &amp; Upgrades
---

### Post by jobmo on 2013-10-01
So, I think the answer is I am SOL and need to re-install Ubuntu. However I was hoping to ask if anyone has any suggestions.

Here is what happened. I was (am still kind of) running Ubuntu 13.04 Raring Ringtail. Everything was running great, I was enjoying life, yay open source! Now I decided I wanted to install the haskell-platform package to do a little functional programming. But bone head me grabbed the deb entry for Saucy instead of Raring, added it really quick to my sources.list and ran a quick: (sudo apt-get update && sudo apt-get install haskell-platform). 

Well chaos insued. Suddenly new saucy packages that are deps of haskell started replacing the 13.04 libraries. All in all the damage wasn't too extensive, honestly the major thing I notice is that my unity bar at the top of the screen has no content (no file menu, no application tray, no clock). 

Does anyone have any suggestions on howto rollback all the changes from the haskell install and its dependancies? Or I am basically stuck with re-installing the OS from scratch?

---

### Post by wojox on 2013-10-01
I would just upgrade to saucy now. :)

---

### Post by oldfred on 2013-10-02
I would make sure you backup what you can if you do not have good backups. I also like to have a dpkg list of installed apps so I can easily reinstall everything.

But you may be able to do a "dirty" install. Or not format partition and install. But any customized config files may still be overwritten.
 Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

---

### Post by Bucky Ball on 2013-10-02
This may be dumb, but couldn't you simply uninstall the deb, if you can get to Software Centre or a terminal to do it, then 'sudo apt-get autoremove' and 'sudo apt-get update/upgrade'?

---

### Post by oldfred on 2013-10-02
You may have to go into /var/log/dpkg and see all the supporting files that were also installed and uninstall each of those. Then refresh system with reinstall of desktop or other files.

---

