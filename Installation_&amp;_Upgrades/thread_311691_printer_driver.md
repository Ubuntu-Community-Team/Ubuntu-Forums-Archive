---
title: "printer driver"
date: 2006-12-03
forum: Installation &amp; Upgrades
---

### Post by squrl on 2006-12-03
I am trying to use a dell 3110cn network printer. The dell driver disk has a driver for linux but it's for redhat. All I can find out is I should use alien with the dell driver but after a couple days I still can't get alien to work. Is there a place to get a driver already converted for ubunu ? Also is it possible to save the driver after it is converted for future use. 

Thanks

---

### Post by Sef on 2006-12-03
Read [How to Install Anything]("http://monkeyblog.org/ubuntu/installing/") in Ubuntu.

---

### Post by squrl on 2006-12-03
If it was that easy I wouldn't be here. I may hate windows but looks like it's time to consider the new version.

---

### Post by kristopher_d on 2007-07-13
Don't despair.  There's always people trying to help, even if they haven't done exactly what your looking for help on.

I just got my 3110cn today.

Open the RPM in your archive manager and browse down to /./usr/share/cups/model/Dell/ and extract the Dell_3110cn.ppd to a hard disk.  Then from System -> Administration -> printing, open the new printer wizard and when you get the opportunity, install the driver.

---

