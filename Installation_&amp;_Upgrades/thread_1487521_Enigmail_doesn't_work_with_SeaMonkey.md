---
title: "Enigmail doesn't work with SeaMonkey"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by scubed on 2010-05-19
I just installed Ubuntu 9.10 amd64 on a laptop for my parents.  They use SeaMonkey with Enigmail for their e-mail.  They complained that they couldn't read their e-mail.

I did apt-get install enigmail.
Here are the versions that are installed:
enigmail 2:0.95.7-1ubuntu2
seamonkey 1.1.17+nobinonly-0ubuntu1

Unfortunately, enigmail didn't show up in SeaMonkey.  I looked at the files it installed. It looks like it only points Thunderbird at enigmail, but not SeaMonkey.

How do I get enigmail to work with SeaMonkey?  Is there another package I can install?  Or do I have to manually move around the files?

---

### Post by scubed on 2010-05-20
It there any more information that I can
provide that would be helpful?

---

### Post by scubed on 2010-05-22
I have upgraded from 09.10 to 10.04,
which included updating SeaMonkey
to version 2.  Then, I was copied the
enigmail symlink from
/usr/lib/thunderbird
into
/usr/lib/seamonkey
and a few other places I saw similar symlinks,
and then SeaMonkey finally had a working
enigmail and was able to send and receive
encrypted e-mail.

---

