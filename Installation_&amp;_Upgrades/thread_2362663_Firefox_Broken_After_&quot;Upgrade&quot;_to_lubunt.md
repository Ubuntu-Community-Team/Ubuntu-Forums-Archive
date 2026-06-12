---
title: "Firefox Broken After &quot;Upgrade&quot; to lubuntu 16.04 From 14.04"
date: 2017-05-31
forum: Installation &amp; Upgrades
---

### Post by rebeltaz on 2017-05-31
I'll forgo my usual "upgrade" rant. I had need to "upgrade" my lubuntu 14.04 system to 16.04 last night. Firefox, which had worked up until last night, now crashes with 

```

ExceptionHandler::GenerateDump cloned child 5486
ExceptionHandler::SendContinueSignalToChild sent continue signal to child
ExceptionHandler::WaitForContinueSignal waiting for continue signal...

```

Safe mode does the same thing. I have removed the .mozilla directory. I have purged and re-installed firefox. Nothing works. Any idea?

---

### Post by ian-weisser on 2017-05-31
Firefox works fine on my 16.04 system.
Are there any other possible clues or symptoms?

Thank you for forgoing the rant.

---

### Post by rebeltaz on 2017-05-31
> **ian-weisser said:**
> Firefox works fine on my 16.04 system.
Are there any other possible clues or symptoms?

Not that I can tell. Everything else [seems to] works just fine.

> **ian-weisser said:**
> Thank you for forgoing the rant.
:-\"  :mrgreen:

---

### Post by mc4man on 2017-05-31
Sounds like this bug though it's been fixed..
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1671079](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1671079)

---

### Post by rebeltaz on 2017-05-31
I've done a update/upgrade and it's still crashing. It does sound the same, but apparently, my system hasn't gotten the memo yet :)

The version I'm showing installed is 53.0.3+build1-0ubuntu0.16.04.2.... not sure if that is newer or older. The first set of numbers is higher, but the second set is lower.

---

### Post by vasa1 on 2017-05-31
> **rebeltaz said:**
> ...

The version I'm showing installed is 53.0.3+build1-0ubuntu0.16.04.2.... not sure if that is newer or older. ...
53 is newer.

```
$ apt policy firefox
firefox:
  Installed: (none)
  Candidate: 53.0.3+build1-0ubuntu0.16.04.2
  Version table:
     53.0.3+build1-0ubuntu0.16.04.2 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 Packages
     45.0.2+build1-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
$ 
```

---

