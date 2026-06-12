---
title: "Ubuntu 6.10 (Gold) &amp; Ciphire"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by rbalfour on 2006-10-27
Problem:

> When trying to do a new install on Ubuntu 6.10 (rel Oct 26, 2006)
I get the following error

# ./install-ciphire.sh
./files/setupdata/libciphire.sh: 234: Syntax error: "(" unexpected (expecting "}")


Anyone have clues to the issue? Downloaded the archive twice.
I thought maybe my bash was the issue, but other sh installer work.

ANSWER:

> if you look at /bin/sh, that is most likely a symlink to /bin/dash.
so one workaround would be this:
sudo bash
rm /bin/sh
ln -s /bin/bash /bin/sh

you can later undo this change with
sudo bash
rm /bin/sh
ln -s /bin/dash /bin/sh

but we saw also other shell scripts fail on ubuntu edgy, not only our
installer script, so you might want to keep this change as well.

Thanks to tolonuga for the help.

Orig link -> [https://forum.ciphire.com/viewtopic.php?t=838&start=0&postdays=0&postorder=asc&highlight=](https://forum.ciphire.com/viewtopic.php?t=838&start=0&postdays=0&postorder=asc&highlight=)

---

