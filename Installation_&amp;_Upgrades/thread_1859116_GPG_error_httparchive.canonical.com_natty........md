---
title: "GPG error: http://archive.canonical.com natty......."
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by jameshedwards on 2011-10-13
I am getting the following error when I do a apt-get update:

W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) natty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Doing some searches I found the following solution but it has not fixed the problem:

root@je-thinkpad:~# apt-key adv --recv-key --keyserver keyserver.ubuntu.com 40976EAF437D05B5


This is on Natty 11.04 on a Think Pad.

Thanks,

James

---

### Post by Shazaam on 2011-10-13
I am running lucid at the moment. I get this...
```
W: GPG error: http://archive.canonical.com lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```
There is a LARGE volume (going back to Ubuntu Hoary) of google links about this. I am going to reboot into Natty and see if the same thing occurs.

---

### Post by Shazaam on 2011-10-13
Ok I'm back. Natty update is fine using either apt-get or Synaptic, no errors so far. There was an update for Lucid earlier today for apt that I installed. I don't know if that is causing the problem.
Another possibility is since Oneric is out the servers "may" be getting hammered. I will wait till friday and try a Lucid update again.
Sorry if I haven't helped you in any way but I have tried the workarounds posted here and on Launchpad with no resolution. You are welcome to try them yourself.

---

### Post by jameshedwards on 2011-10-13
Well, now it has stopped giving the error. I'll mark this a fixed.

---

### Post by Shazaam on 2011-10-13
For me the fix was to disable the "Partner" repo's. Good to see you have resolved your problem.

EDIT--- And today I re-enabled the Partner repos and they are working again. :)

---

