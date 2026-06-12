---
title: "postfix error message"
date: 2017-11-11
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2017-11-11
Upgrading one of my servers I got an error related to postfix init.d script. I removed postfix and reinstalled it and got thse errors

```
Setting up postfix (3.1.0-3ubuntu0.2) ...
insserv: script postfix: service mail-transport-agent already provided!
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package postfix (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The postfix init script looks OK so I'm not sure what the error is telling me.

I do have courier installed but that's never cause any issues before.

---

### Post by SeijiSensei on 2017-11-11
Did you run "sudo apt-get update" before installing?

---

### Post by rsteinmetz70112 on 2017-11-13
> **SeijiSensei said:**
> Did you run "sudo apt-get update" before installing?

I used the software update tool to upgrade all packages. I got the dpkg error during that. From there I removed and reinstalled postfix and this is what I get.

---

