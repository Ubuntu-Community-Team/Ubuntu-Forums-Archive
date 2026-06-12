---
title: "OpenOffice 3.2 Mail Merge"
date: 2010-04-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ugm6hr on 2010-04-27
A bug, I believe...  Uncertain whether upstream or Ubuntu specific.  Can anyone reproduce it to confirm?

1. Create database in Base - create at least 1 table (with 2 or 3 fields) and enter at least 1 piece of data.
2. Create text doc in Writer - Edit -> Exchange Database - select your DB and table created above - Insert -> Fields -> Other - select your table fields from above.
3. Print text doc - select Yes to merge form - select correct table (if not already selected) - output as File (either single or multiple).

The resulting odt file will not have merged anything - all the merge fields will be blank.

This worked fine in Ubuntu 9.04 (with OO 3.0) - but not in 3.2 on 10.04.  I tried the Windows version of OO.org briefly at work, and I think it does the same, although I couldn't be certain.

Will report bug if confirmed - if people could check non-Ubuntu OS too - that would help clarify.

---

