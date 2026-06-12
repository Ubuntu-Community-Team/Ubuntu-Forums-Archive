---
title: "Something not loading properly after Ubuntu update"
date: 2011-11-06
forum: Installation &amp; Upgrades
---

### Post by gilbertstuart on 2011-11-06
Hello,

It seems that something is not loading properly in my Ubuntu Machine. I don't know what it is, but I've observed some symptoms.

1. The trash can is not working. If I erase something, the trash doesn't have it. On its icon it says N/A instead of an usual number.

2. The folders auto arrange and resize to the same parameter (organized by last edited folder). After I change the order to alphabetical, close the window and open in again, it auto arranges. It doesn't "remember" my preferences.

3. The Ubuntu Default Calculator application doesn't remember that I left it in Advanced Mode. Every time I restart it, it is displaying the Basic mode. Again, it seems that it doesn't remember my preference like it used to before.

4. Ubuntu is not recognizing other mounted disks, like the separate partition I have for Windows.


Recently I updated Ubuntu with the Update Manager. It was only the regular security updates and recommended updates, not to a newer Ubuntu version. I believe the aforementioned problems appeared after the last update I did.

Running Ubuntu 10.10

---

### Post by bluexrider on 2011-11-06
First thing would be "sudo apt-get update && apt-get dist-upgrade"

then set those things like you want and logout.

Then return to see what has happened.

---

### Post by gilbertstuart on 2011-11-07
Thanks for the quick response. Unfortunately what you recommended didn't do much to solve the problem. I may add to the list of problems:

**5. Not recognizing USB sticks**

I thought it had something to do with Cairo Dock, but after resetting it, still same problems.

Best

Ahmed

---

