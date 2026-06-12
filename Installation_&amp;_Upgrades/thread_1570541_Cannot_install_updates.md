---
title: "Cannot install updates"
date: 2010-09-08
forum: Installation &amp; Upgrades
---

### Post by cwwilson721 on 2010-09-08
Update Manager pops up, saying I have updates to install:

lftp
sudo

OK, cool...I click "Install Updates" (as usual)

It downloads. Then, after a VERY short time, it errors.

"Not all changes and updates completed". I click the Details, and...
```
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 unable to open files list file for package `indicator-application': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover...
```Hmm...So, I switch to cli, and:
```
Need to get 0B/1,676kB of archives.
After this operation, 127kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 unable to open files list file for package `indicator-application': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

```What's going on?

---

### Post by squaregoldfish on 2010-09-08
I/O errors are usually indicative of a corrupt disk. Things to do:

1. Backup your data now! Your disk may be on the way to dying altogether.
2. Run fdisk to check the disk's integrity and find any errors - a Live CD is best for this.

See what fdisk has to say for itself before you decide what to do next.

Steve.

---

### Post by cwwilson721 on 2010-09-08
lol...

While I was waiting on a reply, I did just that, and found 1 bad sector...

Easy fix? I just made a copy of the /var/lib/dpkg/info folder, deletwed the original, renamed the copy, and viola! 
It works

---

