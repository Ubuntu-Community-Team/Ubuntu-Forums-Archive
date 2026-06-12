---
title: "Firewire Udev rules in Jaunty?"
date: 2009-02-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Stochastic on 2009-02-27
So I need the audio users to be able to access raw1934, and in previous Ubuntu's I could just change the permission in /etc/udev/rules.d/40-permissions.rules but in Jaunty its gone!  Where did it go?  How do I grant audio access to my firewire soundcard?

---

### Post by taavikko on 2009-02-27
Permissions should be granted dynamically to devices.

```
ls -l /dev/ |grep audio
```
If it doesn't show your 1934 device, search for that devices in /dev/

---

### Post by Stochastic on 2009-02-27
EUREKA!  Solved.

I found that the rules have been moved to /lib/udev/rules.d/ and that the 50-udev-default.rules is lacking in a raw1934 line, so I simply copied mine from Intrepid, and whoila - my soundcard now works.  Off I go to write a bugfix patch.

---

