---
title: "How to prevent major upgrades"
date: 2024-10-08
forum: Installation &amp; Upgrades
---

### Post by john163 on 2024-10-08
I have a laptop I need to keep on 22.04 for some time.  How can I prevent it from getting upgraded to 24.04?  I'm OK with going to 22.04.6 and getting all updates within 22.04

---

### Post by ian-weisser on 2024-10-08
Your Ubuntu system **won't** upgrade to a new release automatically. A release-upgrade requires a human admin's approval.
It is possible to negligently or accidentally approve, so be careful about that.
ALWAYS double-check why the system is asking you for your password.

You can turn off the reminder that a new version is available:
1. Run the "software-properties-gtk" command (also known as the Software & Updates application).
2. Go to the "Updates" tab
3. Notify me of a new Ubuntu version: Select "Never"

---

