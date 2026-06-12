---
title: "Evolution Error"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by DWL52 on 2011-05-02
I've upgraded to 11.04 and now Evolution doesn't work right. It shows there are unread messages in my inbox, but when I click on it, it says "Error Generating Message List" at the bottom, with an exclamation mark in a red circle. When I click on that, it says "database disk image is malformed". I've uninstalled and reinstalled Evolution,  but get the same message. Any and all help would be greatly appreciated.

---

### Post by lechien73 on 2011-05-02
It sounds like your mail folders are corrupted. When I had a similar problem, removing the folders.db file solved it, but maybe back it up, just in case ;)

You could remove the file using the following method:

Quit from Evolution, then issue these commands in a terminal window:

```
mv ~/.evolution/mail/local/folders.db ~/folders_1.db
mv ~/.local/share/evolution/mail/local/folders.db ~/folders_2.db
```

Restart Evolution and it should rebuild the database.

If that fails, you can always move the db files back to their previous location from the backups.

---

### Post by DWL52 on 2011-05-02
Worked like a charm. Thanks.

---

### Post by lechien73 on 2011-05-02
Great stuff :) if you wouldn't mind, could you please use the "Thread Tools" menu at the top of the page, and mark this thread as [SOLVED]?

Thanks

---

### Post by Windoze Refugee on 2011-05-05
Genius. Many thanks. WR

---

