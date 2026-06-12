---
title: "Dpkg input/output error blocking any package operation."
date: 2015-03-30
forum: Installation &amp; Upgrades
---

### Post by rolandixor on 2015-03-30
I've posted the details here, but as getting answers on Ask Ubuntu can take a bit long (and I'd like to get this answered ASAP), I'm also asking for help here.

[http://askubuntu.com/questions/603295/how-to-fix-this-dpkg-error/603305#603305](http://askubuntu.com/questions/603295/how-to-fix-this-dpkg-error/603305#603305)

I cannot perform any operation: installation, removal or purging. Dpkg returns this error:

```
[INDENT][FONT=arial]dpkg: unrecoverable fatal error, aborting:
reading files list for package 'linux-headers-3.16.0-31': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:[/FONT]
[/INDENT]

```

It isn't, as I thought originally, a bad line in the status file, as removing the entry for linux-headers-3.16.0-31 did not fix the problem. Also clearing the database and cache as suggested did not fix the issue. Now I am getting a slightly different error:

```

[INDENT][FONT=arial]dpkg: unrecoverable fatal error, aborting:
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:[/FONT]
[/INDENT]

```

I have tried whatever solutions I could find, but nothing works so far. I cannot reinstall as I do not have a drive on which to backup my files. I know this can be fixed, so please, if anyone has any idea, point me in the right direction.

---

### Post by bapoumba on 2015-03-31
May be this ?
[http://ubuntuforums.org/showthread.php?t=1232143&p=10010092#post10010092](http://ubuntuforums.org/showthread.php?t=1232143&p=10010092#post10010092)

---

### Post by ian-weisser on 2015-03-31
When dealing with dpkg, don't jack around trying random stuff you find on the internet.
It's usually a waste of time, and sometimes makes fixing harder.

We need more information.

Can we please see more context for your error message? Was this a dpkg command you were running? Or something from apt?
How long have you had this problem?

What command(s) do you run to reliably reproduce this problem?

Do you have ANY other applications that have recently had input/output errors or crashes?

Have you run fsck?

If you run 'sudo apt-get update', does it work successfully?

---

### Post by rolandixor on 2015-03-31
> **ian-weisser said:**
> When dealing with dpkg, don't jack around trying random stuff you find on the internet.
It's usually a waste of time, and sometimes makes fixing harder.

We need more information.

Can we please see more context for your error message? Was this a dpkg command you were running? Or something from apt?
How long have you had this problem?

What command(s) do you run to reliably reproduce this problem?

Do you have ANY other applications that have recently had input/output errors or crashes?

Have you run fsck?

If you run 'sudo apt-get update', does it work successfully?

Thanks for your reply and your concern but I assure I was not "randomly jacking around". I'm not a noob, even if I'm not a dpkg expert.

That said:

[LIST]
[*]The problem started about a day or two ago after regular system updates.
[*]I was using Synaptic when I first encountered the problem, but *any* dpkg related command get this result once you get to installing/removal.
[*]It can be reproduced with apt-get install/remove anything.
[*]I ran fsck about twice - no errors.
[*]sudo apt-get update works fine.
[*]No other application has been giving I/O errors.
[*]SMART data says there are 23 bad sectors (the drive is a bit old, and well used), but no reallocated sectors.
[*]The linux-headers-blablaba (see original post) package seems to be the issue. Running a script to copy and backup apt's config and refresh it (I'll post the link later to the script) ran into an issue with the same package's md5 checksum (forgot where it was located and since the script moved so fast I couldn't copy/paste - so I will have to try that again later).
[*]dpkg --configure -a gives no errors and no result. Same with apt-get install -f.
[*]dpkg -C gives nothing.
[*]Reading the database always stops at 40% with this error.
[*]The usual fix of removing the malformed line from the status file did not work.
[/LIST]

This is all the extra information I could think of.

---

### Post by rolandixor on 2015-03-31
> **bapoumba said:**
> May be this ?
[http://ubuntuforums.org/showthread.php?t=1232143&p=10010092#post10010092](http://ubuntuforums.org/showthread.php?t=1232143&p=10010092#post10010092)

Well, would you believe it? I tried this before (twice!) and it didn't work - but now it did!

Puzzled, but pleased. Thank you!

---

### Post by ian-weisser on 2015-03-31
I'm puzzled too, but happy to see you got it sorted.

---

### Post by bapoumba on 2015-03-31
> **ian-weisser said:**
> When dealing with dpkg, don't jack around trying random stuff you find on the internet.
It's usually a waste of time, and sometimes makes fixing harder.
..
Were you referring to the link I posted ?
It helped me once. I could not find the page I took it from (that was quite some time ago, when I did not take real notes) but it was from a debian tutorial or bug. I remembered the general process and searched the forums here.

Glad to see you got it sorted out rolandixor :)

---

### Post by ian-weisser on 2015-03-31
> **bapoumba said:**
> Were you referring to the link I posted ?

No! Your links, like the rest of your contributions here, have helped many people.

The phrase is intended to disparage the rather poor advice often found without adequate context out in the wild,
NOT to disparage the seekers of advice,
NOT to disparage the kindly and knowledgable advisors.

And I heartily apologize to everyone for a phrase that has distracted from the original puzzling dpkg issue.

---

### Post by bapoumba on 2015-04-01
OK thanks and sorry for asking, I just wanted to understand what you were meaning :)

That said, I agree this error got me searching left and right a while back. Most probably the drive should be monitored. In my case, at the time, the laptop was not dying, It is now barely breathing, dead battery for a long time and recent random shutdowns. At the time, if I recall correctly, I was not running low on space and I had tried to restore the .list file from backup without editing.

@rolandixor : have you had crashes, power interruption or dpkg (or package manager) interruptions before this error appeared ? Or manually removed some files ?

---

