---
title: "Upgrade owner and group problems"
date: 2009-04-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by petersra on 2009-04-20
Did an upgrade from 8.10 to 9.04 (update-manager -d) yesterday.  Everything went as expected until the final step of rebooting.  After the reboot, I was prompted for a un/pw, and then received a blank screen.  Dropped down to text mode and logged in.  The problem was that most of the files in my mounted /home directory had the owner and group set to 1000 not my un.  Could not change them with sudo so was forced to do a clean install.:(

---

