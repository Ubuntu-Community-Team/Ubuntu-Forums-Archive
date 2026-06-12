---
title: "Calculation error - unknown"
date: 2006-08-09
forum: Installation &amp; Upgrades
---

### Post by timbounceback on 2006-08-09
When I it trys to install, it finishes modifying the software channells and gives me an error about an unknown calculation problem - it also tells me to report it as a bug. Has anyone else had a problem like this?

---

### Post by mlind on 2006-08-09
Could you post the command you invoke and the actual error message ?

---

### Post by timbounceback on 2006-08-10
Now something weirder has happened - I rebooted and tried to get the error message again. Now it gives me an error that says: "Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/sources](http://ca.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/sources) Sub-process gzip returned an error code (1) - this happened when It was somewhere in the "modifying software channels" stage of installation.

---

### Post by mlind on 2006-08-10
> **timbounceback said:**
> Now something weirder has happened - I rebooted and tried to get the error message again. Now it gives me an error that says: "Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/sources](http://ca.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/sources) Sub-process gzip returned an error code (1) - this happened when It was somewhere in the "modifying software channels" stage of installation.

Looks like that url gives 404 response.
Try changing to other mirror, here's some instructions for that if it's not yet familiar for you
[https://help.ubuntu.com/community/Repositories/Ubuntu#edit](https://help.ubuntu.com/community/Repositories/Ubuntu#edit)
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

Here's list of official mirrors [https://wiki.ubuntu.com/Archive](https://wiki.ubuntu.com/Archive)

---

