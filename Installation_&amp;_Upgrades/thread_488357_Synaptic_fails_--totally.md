---
title: "Synaptic fails --totally"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by thegitksan on 2007-06-30
Hi all. I tried installing a generic modem driver, for ¨conexant¨, and after it failed to install, I lost my Synaptic Package Manager, totally.

I just tried to remove the package and any other problematic packages (eg spampd) and it tells me even as root I have insufficient privileges to remove it.

What am I missing? Synaptic at this point just tells me I need to re-install conexant, and it cannot find the archive for it.. Also it has issues with reading the cache(1) and to go tell someone about it (report it).

Any ideas?

Russell

error messages below

root@silverbomb:~# dpkg -r pending
dpkg - warning: ignoring request to remove pending which isn't installed.
root@silverbomb:~# dpkg -r --pending
dpkg: error processing conexant (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 145220 files and directories currently installed.)
Removing spampd ...
 * ERROR: Insufficient privileges. Retry as root
invoke-rc.d: initscript spampd, action "stop" failed.
dpkg: error processing spampd (--remove):
 subprocess pre-removal script returned error exit status 4
 * ERROR: Insufficient privileges. Retry as root
invoke-rc.d: initscript spampd, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 4
Errors were encountered while processing:
 conexant
 spampd

---

### Post by thegitksan on 2007-06-30
SUCCESS!

Very late last night I finally figured it out. On my laptop, it was a combination of two problems stemming from the original failed installation.

Firrst off, following advice posted in one of the other Synaptic threads, I went into the folder <something>/apt/ and then deleted any files or folders with the name of the app I tried to install. I had to go in as root, because it would not let me delete them otherwise.

Second, I re-ran the dpkg --remove etc.set of commands, and finally began seeing different error messages this time. dpkg complained that files were missing, first, then I ran it again, and all but one error message disappeared, then I ran it a third time and it announced the package was successfully removed.

After that, Synaptic loaded properly and I was able to reload the database successfully. 

I will post the exact steps in a while.

Russ

---

