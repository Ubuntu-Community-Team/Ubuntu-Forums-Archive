---
title: "What is hal depreciation in karmic?"
date: 2009-09-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ~Las~ on 2009-09-03
In karmic what are the scripts responsible for hibernation?I used to edit /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux to show a confirmation message before hibernating in Jaunty but this trick don't work on  karmic alpha.

---

### Post by keplerspeed on 2009-09-05
The replacement for hal is "DeviceKit-power", "DeviceKit-disks" and "udev". See: [http://www.ubuntu.com/testing/karmic/alpha5#hal%20deprecation](http://www.ubuntu.com/testing/karmic/alpha5#hal%20deprecation)

Not sure where these scripts are kept however.

---

