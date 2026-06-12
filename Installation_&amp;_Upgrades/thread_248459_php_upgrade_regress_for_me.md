---
title: "php upgrade regress for me?"
date: 2006-09-01
forum: Installation &amp; Upgrades
---

### Post by alligator424 on 2006-09-01
Hi dear ubuntu users,
i recently let the php upgrade execute, and i see a regression on a query "handled" by phpmyadmin. Say, i was using, not to be due to write a script for that, the output made by phpmyadmin queryng a table as a bookmark for future access on this table with the same query. In other words, I bookmarked a query (copyng the url with all the needed data inside) and used it after, very nic feature.
but with the new upgrade of php, it doesnt work anymore, it says 

import.php: Missing parameter: import_type  (FAQ 2.8)
import.php: Missing parameter: format (FAQ 2.8)

any idea?

---

### Post by alligator424 on 2006-09-01
OK, i found the solution: i used, for my "query bookmark" the read_dump.php function, but i went  back to use the sql.php function, which is not regressing with the last php upgrade. Perhaps i was doing a mistake using a kind of glue in place of the right function...

everything is ok now.

---

### Post by alligator424 on 2006-09-01
NO! too bad! the problem is not solved, i just miss that sqp.php, if no query present , makes a browse by default of the table, which is not what i want ...
problem of handling the import of query output stream with an url/bookmark stil there...

---

