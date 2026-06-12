---
title: "Can't install flash for Opera, it works fine with Mozzila."
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by HGodzillov on 2007-08-30
I spent 3 hours trying to find a way to make the flash player work with Opera (I am currently using 9.23), reading ton of guides on the Internet, but without success. I am using Ubuntu 6.06 for 2 days, so if have any suggestions how can I fix it, plaese try to describe them for a newb :). Flash work perfectly with Mozilla, though.

---

### Post by kellemes on 2007-08-30
Did you already see [this link]("https://help.ubuntu.com/community/OperaBrowser")?

---

### Post by HGodzillov on 2007-08-30
Yes, I ve read this article, but it didn't help.

---

### Post by HGodzillov on 2007-08-30
Can anybody help, please?

---

### Post by lefthand on 2007-08-30
Do you have libflashplayer.so? Mine was in /home/XXXX/.mozilla/plugins.

You should just need to copy the file to /usr/lib/opera 

In Opera, if you go to: Tools -> Preferences -> Advanced -> Content -> Plugin Options
Does that list the flash plugin?

---

### Post by HGodzillov on 2007-08-31
Thanx, now it work with both Mozilla and Opera. I'll keep exploring ubuntu :)

---

