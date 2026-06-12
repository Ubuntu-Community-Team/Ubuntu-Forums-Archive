---
title: "Sunbird can't save events / tasks"
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by madmetal on 2009-09-22
I just installed Sunbird 0.9 on Karmic and it seems i can't save any task or event.
Launchpad doesn't track bugs for sunbird so i don't know if its my fault or a bug..
Error console shows..

```

Error: DB error: database table is locked: TEXT
exc: [Exception... "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [mozIStorageStatementWrapper.execute]"  nsresult: "0x80004005 (NS_ERROR_FAILURE)"  location: "JS frame :: file:///usr/lib/sunbird/components/calStorageCalendarModule.js -> file:///usr/lib/sunbird/js/calStorageCalendar.js :: anonymous :: line 2216"  data: no]

Error: exc is not defined
Source File: file:///usr/lib/sunbird/components/calStorageCalendarModule.js -> file:///usr/lib/sunbird/js/calStorageCalendar.js
Line: 2510 
```

---

