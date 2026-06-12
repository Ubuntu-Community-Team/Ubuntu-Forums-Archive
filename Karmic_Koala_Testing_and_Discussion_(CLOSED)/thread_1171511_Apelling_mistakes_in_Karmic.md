---
title: "Apelling mistakes in Karmic"
date: 2009-05-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by shankhs on 2009-05-27
I just installed 9.10 alpha1, during the installation I saw one spelling mistake :)

During the setting up of '/' partition there was one field which said "Relatime system" which I think should be "Real time system"

and also after I installed ntfs-config I got an error message which had "caracter" instead of "character".

Correct me if am wrong.
Should I report them as bugs?

I am a first timer testing alpha so don't know much about bugs and their categories in ubuntu.So I thought it would be better to ask here.

NOTE: The thread heading is intended. :)

---

### Post by zekopeko on 2009-05-27
> **shankhs said:**
> I just installed 9.10 alpha1, during the installation I saw one spelling mistake :)

During the setting up of '/' partition there was one field which said "Relatime system" which I think should be "Real time system"

and also after I installed ntfs-config I got an error message which had "caracter" instead of "character".

Correct me if am wrong.
Should I report them as bugs?

I am a first timer testing alpha so don't know much about bugs and their categories in ubuntu.So I thought it would be better to ask here.

NOTE: The thread heading is intended. :)

relatime is probably the flag for the ext3/4 filesystem. it has to do with marking folder/file times of creation/modification of said folder/files IIRC.

---

### Post by shankhs on 2009-05-27
Thanx zekopeko ,
So what about the next one?

---

### Post by davideotape on 2009-05-27
> **shankhs said:**
> Thanx zekopeko ,
So what about the next one?

I'd file a burgreport, with a picture of the mistake as possible.

---

### Post by Kareeser on 2009-05-27
Is relatime really a typo? I've seen it so many times that I figured that was what it really was called...

Oh jeez.

---

### Post by davideotape on 2009-05-27
> **Kareeser said:**
> Is relatime really a typo? I've seen it so many times that I figured that was what it really was called...

Oh jeez.

Sorry if I didn't make myself clear, but I meant just file a report on the second typo. I think we've established that typo no. 1 isn't really a typo.

---

### Post by xat_ on 2009-05-27
relatime is short for relative atime or relative access time.

---

### Post by klein on 2009-05-27
I misread it every time I see it, but it's not a typo.  It stands for RELative Access TIME.  It's a smart way to keep the filesystem from writing a "I read this" time stamp, avoiding a huge boner in the POSIX (?) standard that makes every disk read entail a disk write.

---

### Post by shankhs on 2009-05-27
So I think for the second error I should file a bug report in LP right?(If LP is the right place then where in LP?)
OR should inform the ntfs-config package developer?
OR both?
I dont know guys . Please help.

---

### Post by zekopeko on 2009-05-27
go with launchpad.
was that typo in the ubuntu installer (the one where you partition the disk and select username etc.)? if so report it against the ubiquity package.

---

### Post by shankhs on 2009-05-27
there is also a typo in ntfs3g app..I mentioned in the first post of this thread.
Where should I report that?
As far as relatime is concerned :
[http://kerneltrap.org/node/14148](http://kerneltrap.org/node/14148)
is worth a look.

---

### Post by zekopeko on 2009-05-27
here:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by shankhs on 2009-05-28
thanx zekopeko, but I am still unable to figure out the right place to post the bug in ntfs3g.
LP says that there is no such package.
Done
I was actually searching for ntfs3g which should be ntfs-3g.
Thankyou all guys.

---

### Post by taavikko on 2009-05-28
> **shankhs said:**
> thanx zekopeko, but I am still unable to figure out the right place to post the bug in ntfs3g.
LP says that there is no such package.

[https://edge.launchpad.net/ubuntu/+source/ntfs-3g](https://edge.launchpad.net/ubuntu/+source/ntfs-3g)
when reporting, use "ubuntu-bug ntfs-3g"

If any questions, refer to [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

