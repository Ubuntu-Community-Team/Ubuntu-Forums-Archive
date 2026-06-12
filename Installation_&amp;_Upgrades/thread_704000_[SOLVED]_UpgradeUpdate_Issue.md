---
title: "[SOLVED] Upgrade/Update Issue"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by Nate9009 on 2008-02-21
Hi everyone!  I'm having a bit of a problem with updating my OS (Running Gutsy currently)

For some reason the update manager is encountering a problem whenever I attempt to upgrade.  Here is the error message I get using the command line.

```


dpkg: syntax error: unknown group `Debian-exim' in statoverride file 
E: Sub-process /usr/bin/dpkg returned an error code (2)


```

So far, I haven't found what the "unknown group" that is causing the problem (I think..,) is.  Does anyone have any ideas of where I should go from here to remedy this problem?  I really appreciate your help! :)

---

### Post by Nate9009 on 2008-02-21
It looks like Bart's scary face scared everyone off... :confused:

---

### Post by Partyboi2 on 2008-02-21
maybe [this]("http://www.thedumbterminal.co.uk/php/knowledgebase/?action=view&id=77") might help, but I have never tried it

---

### Post by Nate9009 on 2008-02-21
Thanks very much for the link!  It's exactly the problem I'm running into.  :)

EDIT : That did the trick.  All that needed to be done was updating the /var/lib/dpkg/statoverride file.  Thanks again!

---

