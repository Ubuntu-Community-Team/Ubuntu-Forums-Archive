---
title: "80% and stops"
date: 2012-12-26
forum: Installation &amp; Upgrades
---

### Post by lewjayjr on 2012-12-26
Trying to install a couple of programs, etc.  Do the sudo-apt get install "program name"  and it starts running.  Gets to around 84-86% and then it stalls, and comes back with unable to parse error 5.

Not sure what is going on.  I don't think I have a really good install of 10.04 and have tried to update etc and never can get it to install.  Running an older Dell Latitude D610 laptop.  Any suggestions to a neophyte?

---

### Post by Kirk Schnable on 2012-12-26
> **lewjayjr said:**
> Trying to install a couple of programs, etc.  Do the sudo-apt get install "program name"  and it starts running.  Gets to around 84-86% and then it stalls, and comes back with unable to parse error 5.

Not sure what is going on.  I don't think I have a really good install of 10.04 and have tried to update etc and never can get it to install.  Running an older Dell Latitude D610 laptop.  Any suggestions to a neophyte?

Could you copy/paste or screenshot the entire error message for us?  The specific file it can't parse might be useful in troubleshooting.

---

### Post by lewjayjr on 2012-12-28
Ok, error message as follows:  
Read packing list 84%
E: Read error - read(5: input/output error)
E: The packing list or status file could not be parsed or opened.


That's all she wrote.

---

### Post by Kirk Schnable on 2012-12-29
In my experience, input/output errors generally are a sign that the hard drive is having issues / failing. I would advise making sure important data is backed up, and possibly running an fsck. [http://manpages.ubuntu.com/manpages/precise/man8/fsck.8.html](http://manpages.ubuntu.com/manpages/precise/man8/fsck.8.html)

---

### Post by lewjayjr on 2012-12-29
Thanks I'll try that.

---

### Post by ibjsb4 on 2012-12-29
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

And welcome to the forums  :)

---

