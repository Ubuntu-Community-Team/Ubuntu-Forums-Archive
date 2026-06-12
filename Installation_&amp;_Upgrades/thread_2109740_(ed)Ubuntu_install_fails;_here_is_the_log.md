---
title: "(ed)Ubuntu install fails; here is the log"
date: 2013-01-28
forum: Installation &amp; Upgrades
---

### Post by Habstinat on 2013-01-28
Trying to install (ed)Ubuntu via Wubi. It downloaded the ISO fine and, after about an hour, failed with a generic error message telling me to check the log, which can be [viewed here]("http://paste.ubuntu.com/1582651/"). I'm logged in as the local administrator on my Windows machine, so I don't see what could be causing this permissions error. What exactly is the error, and what can I do to troubleshoot/fix it?

---

### Post by bcbc on 2013-01-28
It's saying: 
> Error: C:\ubuntu\install\edubuntu-12.10-dvd-amd64.iso: The process cannot access the file because it is being used by another process.

Do you perhaps have an antivirus running that might be probing the file?

You could [file a new bug]("http://bugs.launchpad.net/wubi/+filebug") (if there's nothing you know of that could be accessing the file) and attach your log file to the bug report. You can also download the Edubuntu DVD yourself using bittorrent. First check in the C:\ubuntu\install\ to see if the downloaded one is still there (copy it out if it is).
To install Wubi with the downloaded ISO, just place the two files in the same directory.

---

