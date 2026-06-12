---
title: "sbackup on Ubuntu 10.04 beta 1 -- FAIL"
date: 2010-04-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by harmlessdrudge on 2010-04-02
I've used sbackup successfully in the past on previous versions of Ubuntu. I am trying Ubuntu 10.04 beta 1 now. I've installed sbackup using the Synaptic Package manager (its ABOUT icon gives v0.10.4, and **not** v0.10.5 as reported by Synaptic but this is misleading; checking the changelog shows that this needs to be updated). The program dies whenever I attempt to make a backup.

I immediately get a dead process with <defunct> after in it in the process list.

Sometimes the program asks for a password, but not always. It doesn't make any difference. It fails every time.

I'm not able to upload a crash report. First, I got a message 

"The problem cannot be reported:

You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs:

libappindicator0"

Updating the packages resolved this but the program still crashed and I'm not having any luck uploading the crash info to launchpad just now. 

simple-backup-config.py%20crashed%20with%20NoOptionError%20in%20get()

The upload hangs.

Bug #550261: says sbackup not working.

What I didn't know until I read it was

**sudo sbackupd**

works, though I haven't yet done this. (Update: it works!).

The bug appears to be the same as Bug #311429 but those reports are for older versions of Ubuntu and it appears from the discussion as if sbackup is no longer supported. The last release candidate for the supposed replacement, nssbackup, is over a year old. I'm not sure if trying this is advisable.

This is really a pity, sbackup was great when it worked! 

Do I want a "not so simple backup"? (nssbackup). Not *really*.

Update: I've managed to upload a copy of the crash report and I've posted the Traceback here

[https://bugs.launchpad.net/ubuntu/+source/sbackup/+bug/311429](https://bugs.launchpad.net/ubuntu/+source/sbackup/+bug/311429)

---

### Post by Mark Phelps on 2010-04-02
Problems related to the Beta need to be posted to the proper testing forum: Development & Programming, Lucid Lynx Testing.

I will be asking the Mods to move this thread there.  Please look there for any future responses.

---

