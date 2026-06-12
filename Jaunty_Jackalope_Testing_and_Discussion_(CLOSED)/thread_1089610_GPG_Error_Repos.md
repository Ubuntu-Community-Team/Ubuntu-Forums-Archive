---
title: "GPG Error Repos"
date: 2009-03-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-03-07
Im getting this:

Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

I've gone into sources and removed the auths, set back to restore defaults but no good.

Ideas?

---

### Post by Starks on 2009-03-07
The only alternative is painstakingly registering each GPG key for each offending PPA repo.

---

