---
title: "HP7310 Print jobs hang in queue on 9.10"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by BFG on 2009-12-02
HP 7310 multi-function device, connected via USB.
Printing worked fine in 9.04, but hasn't worked in 9.10 fresh install.

The scanner works fine.  Any print sent to the machine just hangs in the queue, and just states "Failed"

I've added HPLIP from the repos, and it connects to the printer just fine.  Nothing in [http://hplipopensource.com/](http://hplipopensource.com/) seems to advise.
I get:


```
$ tail -f /var/log/cups/error_log
D [02/Dec/2009:09:44:27 +0000] [Job 7] prnt/hpijs/services.cpp 386: unable to write to output, fd=1, count=4096: Broken pipe
D [02/Dec/2009:09:44:27 +0000] [Job 7] prnt/hpijs/services.cpp 386: unable to write to output, fd=1, count=4096: Broken pipe
D [02/Dec/2009:09:44:27 +0000] [Job 7] prnt/hpijs/services.cpp 386: unable to write to output, fd=1, count=4096: Broken pipe
D [02/Dec/2009:09:44:27 +0000] [Job 7] prnt/hpijs/services.cpp 386: unable to write to output, fd=1, count=4096: Broken pipe
D [02/Dec/2009:09:44:27 +0000] [Job 7] Backend returned status 22 (unknown)
D [02/Dec/2009:09:44:27 +0000] [Job 7] End of messages
D [02/Dec/2009:09:44:27 +0000] [Job 7] printer-state=3(idle)
D [02/Dec/2009:09:44:27 +0000] [Job 7] printer-state-message="Processing page 1..."
D [02/Dec/2009:09:44:27 +0000] [Job 7] printer-state-reasons=none
E [02/Dec/2009:09:44:32 +0000] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory

```

Printer is sound, I can connect via http and print a test page from the front panel.

Any help appreciated.


**EDIT: ** I was looking for help, but this seems to have solved itself.  In my hplip install, I gave the printer a name different from the default.  That didn;t improve on things and the printer still didn't work.

However, after a reboot, the printer config showed another printer icon.  The system seems to have reinstalled the printer itself, as the extra icon has the default name.  This printer config works.

I confess I don't know why.  Or why it didn't work when I reinstalled myself.  However, I can now print again.

---

