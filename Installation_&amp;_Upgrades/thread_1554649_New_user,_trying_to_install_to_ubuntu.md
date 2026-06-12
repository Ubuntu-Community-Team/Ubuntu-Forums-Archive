---
title: "New user, trying to install to ubuntu"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by neilmkearns on 2010-08-17
I downloaded easy-invoice2.0 to be used with my Open Office spreadsheet, and created a launcher to run the "ods" file and I got this-

Details: Failed to execute child process "/home/user/Invoice-Easy2.1-OOo.ods" (Permission denied)

Am I linking to the wrong file?

thanks!

---

### Post by lechien73 on 2010-08-17
No - you're linking to the right file, it's just that it can't be launched directly like that.

If you edit the launcher so that the command is:

```
ooffice -calc /<change path>/Invoice-Easy2.1-OOo.ods
```

Obviously replace <change path> with the path to the spreadsheet. This should then work.

If it does work for you, please use the "Thread Tools" menu at the top to mark the thread [Solved]

Thanks

---

