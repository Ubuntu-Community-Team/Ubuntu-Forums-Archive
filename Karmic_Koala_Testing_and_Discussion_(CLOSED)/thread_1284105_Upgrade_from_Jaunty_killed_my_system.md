---
title: "Upgrade from Jaunty killed my system"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dro0g on 2009-10-06
Just wanted to share what I had to do to get things back up and running in case anyone else runs into the same thing.

I ran "update manager -d" and kicked off the upgrade to 9.10. The installation died while updating dbus (the last thing I saw was "The system user `messagebus' already exists" and then a memory leak seemed to take hold and the system eventually hung with the Caps and Scroll lights flashing.

I rebooted and the system hung at boot after displaying "scripts/init-bottom done". Same with booting to single mode.

To fix, I went into grub and changed "ro single" to "rw /bin/bash" That got me to a shell where I could run dpkg --configure -a. The system now boots into X, though it's still pretty wonky and I'm having trouble connecting to the repos to try to get updates.

Hope this helps someone else. This was pretty disappointing vs. the last few releases. I should have known it was an ominous sign when "boot speed" was touted as a feature (why would I need to be rebooting all the time?)

---

### Post by Bucky Ball on 2009-10-06
> Ubuntu Karmic Koala is in development, use only for testing purposes!!!

...

---

