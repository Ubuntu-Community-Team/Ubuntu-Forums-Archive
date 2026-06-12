---
title: "Today's update seemed to have problems"
date: 2016-12-15
forum: Installation &amp; Upgrades
---

### Post by Lloydb39 on 2016-12-15
I was watching the details during today's update of 16.04 and it seemed to be having all kinds of difficulties with bad scripts, missing files and failure to open com ports. Everything is working as far as I can tell, but I was just wondering. Doesn't it leave a log file somewhere? I'd like to look at it and see what was going on and whether anything failed to update.

---

### Post by howefield on 2016-12-15
Try browsing these two files..

```
/var/log/apt/history.log
```
```
/var/log/apt/term.log
```

---

### Post by Lloydb39 on 2016-12-15
Thanks. These are the worrisome lines in the term.log. Do I need to worry?
```
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Setting up python3-problem-report (2.20.1-0ubuntu2.4) ...
Setting up python3-apport (2.20.1-0ubuntu2.4) ...
Setting up apport (2.20.1-0ubuntu2.4) ...
initctl: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
insserv: warning: script 'binfmt-support' missing LSB tags and overrides
```

---

### Post by vasa1 on 2016-12-15
> **Lloydb39 said:**
> Thanks. These are the worrisome lines in the term.log. Do I need to worry?
```
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
...
initctl: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
insserv: warning: script 'binfmt-support' missing LSB tags and overrides
```
Have you been seing such entries before, at least in your current term.log file?

You could grep term.log for "unknown media type", for "Unable to connect to Upstart" and for "missing LSB tags and overrides".

I don't have such entries and my current term.log file dates from 2016-12-01.

---

### Post by ajgreeny on 2016-12-15
> initctl: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refusedThat seems a bit strange seering as 16.04 now uses systemd and not upstart, but I am not an sort of expert in either systemd or upstart so that may be a total red-herring.

Have you chosen to replace systemd with upstart in your system for some reason?

---

### Post by howefield on 2016-12-15
> **Lloydb39 said:**
> Thanks. These are the worrisome lines in the term.log. Do I need to worry?

Out of interest is this an upgrade to 16.04 or a fresh install ?

---

### Post by Lloydb39 on 2016-12-15
It was just an automatic update, sitting on my desktop. I clicked it and it installed. I just happened to be watching. I have not deliberately chosen upstart; don't even know what it is. In the 12/9 log there are similar messages, also this: Warning: PreparingStopping snapd.service, but it can still be activated by:  snapd.socket
Not sure what to make of any of this.

---

