---
title: "HAL Problem When Upgrading from Feisty to Gutsy"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by jmg498 on 2007-12-29
I get the infamous failed to initialize HAL problem now that I've upgraded from Feisty to Gutsy.  I've tried just about all of the solutions proposed in the other threads including:

1.) Reverting back to the Feisty HAL version and forcing that version.
2.) Renaming s12hal to s13hal in /etc/rc2.d
3.) Changing CONCURRENCY = shell to CONCURRENCY = none.
4.) Changing CONCURRENCY = none back to CONCURRENCY = shell.

None of these has worked.  Can anyone suggest any other possible fixes (besides downgrading to Feisty)?

Thanks...

---

