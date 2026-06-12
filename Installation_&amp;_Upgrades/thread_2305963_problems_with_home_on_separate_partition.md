---
title: "problems with /home on separate partition"
date: 2015-12-10
forum: Installation &amp; Upgrades
---

### Post by hvdg on 2015-12-10
Hello,

I installed ubuntu 15.10 and set up /home on a separate partition. It works fine, shows up correctly in the directory tree. But when I tried to install new software, it did not created the required directories in my user directory. I had to tell firefox where the home directory was so it would download files into the Download folder, other wise it was dumping the files into /etc. The minecraft install just vanished. There should have been a hidden directory in my folder under home but it was not to be seen. When I tried to run minecraft it was unfindable. Did I miss a setting when I installed?

---

### Post by oldfred on 2015-12-11
I have used the same Firefox profile for about 10 years. So have not done set up for a while. :)

But it normally does ask for a default location where to put downloads, or has a setting for asking each time you download.  From menu icon,  Preferences, general tab.

It should not have been downloading into anything other than somewhere in /home, unless you manually started it from terminal as / which would never, ever be suggested.

---

