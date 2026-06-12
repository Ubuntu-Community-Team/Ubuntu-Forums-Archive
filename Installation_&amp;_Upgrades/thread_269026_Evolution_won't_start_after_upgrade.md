---
title: "Evolution won't start after upgrade"
date: 2006-10-01
forum: Installation &amp; Upgrades
---

### Post by grayhorse on 2006-10-01
Hi all:

I recently upgraded to Dapper, and now seem to be running into problems. Initially my psc2110 stopped accepting print jobs, although it was still visible, and now Evolution won't start up.

I'm prepared to fiddle with the printer problem, but Evolution had been working, and with no other changes that the regular automatic upgrade, I've now lost it.

Symptoms are: click on Evolution from task bar, get bouncing pointer, wait, bouncing pointer disappears, so does "Evolution Mail - loading application", no program start! ](*,) 

Any ideas on diagnosis?

advthanksance

---

### Post by dcstar on 2006-10-01
> **grayhorse said:**
> Hi all:

I recently upgraded to Dapper, and now seem to be running into problems. Initially my psc2110 stopped accepting print jobs, although it was still visible, and now Evolution won't start up.

I'm prepared to fiddle with the printer problem, but Evolution had been working, and with no other changes that the regular automatic upgrade, I've now lost it.

Symptoms are: click on Evolution from task bar, get bouncing pointer, wait, bouncing pointer disappears, so does "Evolution Mail - loading application", no program start! ](*,) 

Any ideas on diagnosis?

advthanksance

Rename the hidden .evolution directory in your home directory, kill any Evolution processes running, and try and start Evolution again.

If it starts ok, you may have some corruption in your renamed files that caused the problem. If that is the case, you can copy individual files from your renamed directory to the newly created .evolution directory to restore your e-mails.

---

### Post by grayhorse on 2006-10-01
I'm afraid that didn't help. 

I tried re-installing Evolution from Synaptic to set up the various config files again, and that hasn't helped either. 

Could there be some bizarre permissions problem going on?

regards...Ross

---

### Post by grayhorse on 2006-10-01
More info - I tried starting evolution from a terminal and I got a segmentation fault.

What IS going on??

---

### Post by grayhorse on 2006-10-02
Yet more info - I appear to be having a libgcc problem. More & more things are failing (gAIM, aMSN, foomatic-db, adept - the list is growing)

Is there anything I can do to avoid having to re-install?

---

